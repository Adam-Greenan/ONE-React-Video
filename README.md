## Project overview
- React + TypeScript video listing built for the ONE React video display code test
- Uses the YouTube Data API to fetch and display videos
- Focused on clean structure, performance, and a simple UX

## Tech stack
- React (functional components)
- TypeScript
- Vite
- CSS Modules
- YouTube Data API v3
- Fuse.js for client-side filtering
- react-virtuoso for list virtualisation

## Structure
- `api/` – YouTube API calls only
- `data/` – Shapes API responses into app-friendly data
- `contexts/` – Global state via `useContext` + `useReducer`
- `helpers/` – Small utilities for search, filtering, pagination
- `components/` – Reusable UI components
- `screens/` – Page-level composition

## State management
- Global state handled with `useReducer` and `useContext`
- Reducers kept pure and synchronous
- Async logic handled outside reducers
- State includes:
  - search query
  - video results
  - loading / error state
  - pagination token
  - filter query
  - infinite scroll enablement

## Data fetching
- Uses the YouTube `search.list` endpoint
- Fetches results in pages of 9
- Cursor-based pagination via `nextPageToken`
- Results cached in session memory to avoid refetching on refresh

## Filtering
- Client-side filtering using Fuse.js
- Filters against already-fetched results
- While filtering:
  - pagination is disabled
  - infinite scroll is paused
- Filtered results are derived without mutating the original data

## Pagination & performance
- Manual “Next page” button to fetch more results
- Infinite scroll enabled only after user interaction
- Additional results loaded as the user scrolls
- Virtualisation keeps performance consistent with large result sets

## What I’d do with more time
- Add unit tests for reducers and data-mapping helpers
- Add basic component tests around search, filtering, and pagination
- Improve loading states with skeleton placeholders
- Add additional sort and filter options (date, relevance)
- Persist cached results with expiry rather than session-only storage
- Fetch and display richer video metadata (duration, view count)
- Further accessibility improvements (keyboard flow, focus management)
