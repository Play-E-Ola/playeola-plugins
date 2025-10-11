---
name: implement-analytics
description: Comprehensive analytics implementation workflow - discovers requirements, designs data models, scaffolds dashboard components, and implements complete analytics features
---

Execute a comprehensive analytics implementation workflow that guides from requirements to production-ready analytics features.

## Workflow

### Phase 1: Requirements Discovery

1. **Understand Analytics Needs**
   ```
   Invoke analytics-champion agent to:
   - Identify what metrics need to be tracked
   - Determine the target audience (operators, admins, analysts)
   - Define time ranges and refresh frequencies
   - Understand filtering and segmentation requirements
   - Identify data sources (databases, APIs, events)
   ```

2. **Present Requirements Summary**
   ```
   Show user:
   - Key metrics to track
   - Data sources required
   - Dashboard audience and use cases
   - Performance requirements
   - Refresh frequency
   ```

3. **Get User Approval**
   ```
   Ask user to confirm requirements or adjust
   ```

### Phase 2: Technical Design

1. **Design Data Model**
   ```
   Invoke analytics-champion agent to:
   - Design database schema for analytics data
   - Plan data aggregation strategy
   - Define indexes for performance
   - Consider materialized views for expensive queries
   - Design caching strategy
   ```

2. **Design API Layer**
   ```
   - Define API endpoints or GraphQL queries
   - Specify request/response schemas
   - Plan validation with Zod
   - Design pagination for large datasets
   - Define error handling approach
   ```

3. **Design Frontend Architecture**
   ```
   - Plan component structure
   - Choose visualization library (Recharts recommended)
   - Design data fetching with TanStack Query
   - Plan filtering UI components
   - Design loading and error states
   ```

4. **Present Technical Design**
   ```
   Show user:
   - Database schema
   - API endpoint specifications
   - Component architecture
   - Data flow diagram
   - Performance strategy
   ```

### Phase 3: Implementation

1. **Database Layer**
   ```
   - Create database migrations for analytics tables
   - Add indexes for query optimization
   - Create materialized views if needed
   - Set up aggregation jobs (cron or queue)
   ```

2. **Backend API**
   ```
   - Implement API endpoints (REST or GraphQL)
   - Add Zod schemas for validation
   - Implement query logic with optimization
   - Add caching layer (Redis if available)
   - Implement error handling
   - Add logging for monitoring
   ```

3. **Frontend Components**
   ```
   - Create TanStack Query hooks for data fetching
   - Implement dashboard layout components
   - Create visualization components (charts)
   - Implement filter controls (date range, dropdowns)
   - Add loading and error states
   - Implement export functionality (CSV)
   ```

4. **Testing**
   ```
   - Write unit tests for data transformations
   - Write integration tests for API endpoints
   - Test with realistic data volumes
   - Validate performance targets
   - Test error scenarios
   ```

5. **Documentation**
   ```
   Invoke documentation-orchestrator agent to:
   - Document API endpoints
   - Add usage examples
   - Document dashboard features
   - Update project README if significant
   ```

### Phase 4: Validation & Summary

1. **Performance Validation**
   ```
   - Verify query performance meets targets
   - Check dashboard load times
   - Validate caching effectiveness
   - Monitor memory usage
   ```

2. **Code Review**
   ```
   Optionally invoke code-review-expert agent to:
   - Review code quality
   - Check for performance issues
   - Validate error handling
   - Ensure best practices followed
   ```

3. **Generate Summary Report**
   ```
   Implementation Complete:

   ✅ Database:
   - Created analytics tables
   - Added indexes for optimization
   - Set up aggregation jobs

   ✅ Backend API:
   - Implemented [N] endpoints
   - Added validation schemas
   - Configured caching

   ✅ Frontend:
   - Created dashboard components
   - Implemented visualizations
   - Added filtering controls

   ✅ Testing:
   - [N] unit tests
   - [N] integration tests
   - Performance validated

   ✅ Documentation:
   - API docs updated
   - Usage guide added

   Next Steps:
   1. Test with production data volumes
   2. Deploy to staging
   3. Gather user feedback
   4. Monitor performance metrics
   ```

## Implementation Patterns

### TanStack Query Hook Pattern

```typescript
// hooks/useGameAnalytics.ts
import { useQuery } from '@tanstack/react-query';
import { z } from 'zod';

const GameAnalyticsSchema = z.object({
  gameId: z.string(),
  totalSpins: z.number().int().nonnegative(),
  totalRevenue: z.number().nonnegative(),
  rtp: z.number().min(0).max(100),
  playerCount: z.number().int().nonnegative(),
});

type GameAnalytics = z.infer<typeof GameAnalyticsSchema>;

export const useGameAnalytics = (
  gameId: string,
  dateRange: { start: string; end: string }
) => {
  return useQuery({
    queryKey: ['game-analytics', gameId, dateRange],
    queryFn: async () => {
      const response = await fetch(
        `/api/analytics/games/${gameId}?start=${dateRange.start}&end=${dateRange.end}`
      );
      const data = await response.json();
      return GameAnalyticsSchema.parse(data);
    },
    staleTime: 5 * 60 * 1000, // 5 minutes
    cacheTime: 30 * 60 * 1000, // 30 minutes
  });
};
```

### API Endpoint Pattern

```typescript
// api/analytics/games/[gameId]/route.ts
import { z } from 'zod';
import { db } from '@/lib/db';

const QuerySchema = z.object({
  start: z.string().datetime(),
  end: z.string().datetime(),
});

export async function GET(
  request: Request,
  { params }: { params: { gameId: string } }
) {
  try {
    const { searchParams } = new URL(request.url);
    const query = QuerySchema.parse({
      start: searchParams.get('start'),
      end: searchParams.get('end'),
    });

    const analytics = await db.gameAnalytics.findFirst({
      where: {
        gameId: params.gameId,
        date: {
          gte: new Date(query.start),
          lte: new Date(query.end),
        },
      },
      select: {
        totalSpins: true,
        totalRevenue: true,
        rtp: true,
        playerCount: true,
      },
    });

    return Response.json(analytics);
  } catch (error) {
    if (error instanceof z.ZodError) {
      return Response.json({ error: 'Invalid query parameters' }, { status: 400 });
    }
    return Response.json({ error: 'Internal server error' }, { status: 500 });
  }
}
```

### Dashboard Component Pattern

```typescript
// components/GameAnalyticsDashboard.tsx
import { useGameAnalytics } from '@/hooks/useGameAnalytics';
import { LineChart, Line, XAxis, YAxis, Tooltip, ResponsiveContainer } from 'recharts';

export function GameAnalyticsDashboard({ gameId }: { gameId: string }) {
  const [dateRange, setDateRange] = useState({
    start: '2024-01-01',
    end: '2024-01-31',
  });

  const { data, isLoading, error } = useGameAnalytics(gameId, dateRange);

  if (isLoading) return <div>Loading analytics...</div>;
  if (error) return <div>Error loading analytics: {error.message}</div>;
  if (!data) return <div>No data available</div>;

  return (
    <div className="analytics-dashboard">
      <DateRangePicker value={dateRange} onChange={setDateRange} />

      <div className="metrics-grid">
        <MetricCard label="Total Spins" value={data.totalSpins} />
        <MetricCard label="Revenue" value={`$${data.totalRevenue}`} />
        <MetricCard label="RTP" value={`${data.rtp}%`} />
        <MetricCard label="Players" value={data.playerCount} />
      </div>

      <ResponsiveContainer width="100%" height={300}>
        <LineChart data={data.timeline}>
          <XAxis dataKey="date" />
          <YAxis />
          <Tooltip />
          <Line type="monotone" dataKey="revenue" stroke="#8884d8" />
        </LineChart>
      </ResponsiveContainer>
    </div>
  );
}
```

## Special Considerations

### Performance Optimization

**For Large Datasets:**
- Use materialized views for expensive aggregations
- Implement pagination or cursor-based loading
- Add database indexes on common query fields
- Use Redis caching for frequently accessed data
- Consider data archival for old records

**Frontend Performance:**
- Use React.memo for expensive components
- Implement virtualization for long lists
- Debounce filter inputs
- Lazy load chart libraries
- Optimize bundle size

### Real-Time Analytics

If real-time updates are required:
```typescript
// WebSocket pattern for live updates
const useRealtimeAnalytics = (gameId: string) => {
  const [data, setData] = useState(null);

  useEffect(() => {
    const ws = new WebSocket(`wss://api.playeola.com/analytics/${gameId}`);

    ws.onmessage = (event) => {
      const update = JSON.parse(event.data);
      setData(update);
    };

    return () => ws.close();
  }, [gameId]);

  return data;
};
```

### Aggregation Jobs

For historical analytics, set up cron jobs:
```typescript
// cron/daily-analytics-aggregation.ts
async function aggregateDailyAnalytics() {
  const yesterday = new Date();
  yesterday.setDate(yesterday.getDate() - 1);

  // Aggregate from raw events table to daily analytics table
  await db.$executeRaw`
    INSERT INTO daily_game_analytics (game_id, date, total_spins, total_revenue, player_count)
    SELECT
      game_id,
      DATE(created_at) as date,
      COUNT(*) as total_spins,
      SUM(bet) as total_revenue,
      COUNT(DISTINCT player_id) as player_count
    FROM game_rounds
    WHERE DATE(created_at) = ${yesterday}
    GROUP BY game_id, DATE(created_at)
  `;
}
```

## Integration with Other Commands

- **Works with `/smart-commit`**: Commit analytics implementation with quality checks
- **Works with `analytics-champion` agent**: Uses for design and implementation guidance
- **Works with `code-review-expert`**: Optional code review before completion
- **Works with `documentation-orchestrator`**: Keeps docs updated

## Example Usage

### Scenario 1: Game Performance Dashboard

```
User: /implement-analytics

Claude:
I'll help implement an analytics feature. First, let me understand your requirements.

Invoking analytics-champion agent for requirements discovery...

### Requirements Discovery
What analytics feature would you like to implement?

User: Game performance dashboard for operators

Claude:
Great! Let me gather more details:

1. Which metrics should be displayed?
   - Total spins
   - Revenue
   - RTP
   - Active players
   - Win rate

2. What time ranges? (Today, 7 days, 30 days, custom)
3. Any filtering needs? (By game, game type, provider)
4. Refresh frequency? (Real-time, every 5 min, hourly)

[User provides answers]

Claude:
### Requirements Summary
✅ Metrics: Spins, revenue, RTP, players, win rate
✅ Time ranges: Today, 7d, 30d, custom
✅ Filters: Game, game type
✅ Refresh: Every 5 minutes
✅ Audience: Operators

Proceeding to technical design...

### Technical Design
**Database:**
- Table: daily_game_analytics
- Indexes: game_id, date
- Materialized view for real-time (last 24h)

**API:**
- GET /api/analytics/games/performance
- Query params: gameId, start, end, groupBy
- Validation: Zod schemas
- Cache: 5 minutes

**Frontend:**
- TanStack Query for data fetching
- Recharts for visualization
- Date range picker
- Game filter dropdown

Implementing now...

[Creates database migration]
[Implements API endpoint]
[Creates React components]
[Adds tests]
[Updates documentation]

✅ Implementation Complete!

Database migrations created
API endpoint implemented and tested
Dashboard components created
Documentation updated

Next steps:
1. Run migrations: npm run migrate
2. Test dashboard at /dashboard/game-analytics
3. Deploy to staging for operator feedback
```

### Scenario 2: Player Engagement Analytics

```
User: /implement-analytics for player engagement tracking

Claude:
I'll help implement player engagement analytics.

Invoking analytics-champion agent...

### Requirements
Tracking: Session duration, games played, return frequency
Audience: Marketing team
Time range: Last 90 days
Visualization: Cohort analysis, retention curves

### Technical Design
**Database:**
- player_engagement_metrics table
- Daily aggregation from sessions
- Cohort analysis stored procedure

**API:**
- GraphQL for flexible queries
- Cohort query resolver
- Retention query resolver

**Frontend:**
- Custom cohort visualization
- Retention curve chart
- Export to CSV

Implementing...

[Creates schema]
[Implements GraphQL resolvers]
[Creates cohort visualization]
[Adds export functionality]

✅ Complete! Marketing dashboard ready with cohort analysis.
```

## Best Practices

1. **Start with requirements** - Don't jump to implementation
2. **Design for performance** - Consider data volumes early
3. **Validate inputs** - Always use Zod for API validation
4. **Cache aggressively** - But with appropriate invalidation
5. **Handle errors gracefully** - Show meaningful error messages
6. **Test with real data** - Use production-like datasets for testing
7. **Document APIs** - Make it easy for other developers
8. **Monitor performance** - Add logging and metrics

## Troubleshooting

### Slow Query Performance
- Check if indexes exist on query fields
- Review query execution plan
- Consider materialized views for complex aggregations
- Add Redis caching for frequently accessed data

### High Memory Usage
- Implement pagination or cursor-based loading
- Use streaming for large exports
- Optimize component re-renders
- Check for memory leaks in React

### Inaccurate Data
- Validate data transformation logic
- Check timezone handling
- Verify aggregation query correctness
- Add data integrity tests

---

**Goal**: Make analytics implementation systematic, performant, and production-ready. From requirements to deployment, guide every step of the process.
