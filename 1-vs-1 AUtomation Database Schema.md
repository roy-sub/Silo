# Database Schema Description: notify_one_vs_one

## Table Overview

| Table Name | Primary Purpose | Key Features |
|------------|----------------|--------------|
| **languages** | Language configuration | Stores supported languages with flags and shortcodes |
| **player_category_map** | Player position mapping | Maps player pairs to categories based on positions |
| **player_comparisons** | Player vs player stats | Stores comparison statistics between two specific players |
| **player_comparisons_fallback** | Default player comparisons | Fallback comparison data when specific player data unavailable |
| **player_pair_categories** | Player pairing types | Defines categories for different player pair combinations |
| **player_positions** | Player position definitions | Master list of player positions with ordering and grouping |
| **player_single** | Individual player stats | Statistics and bullet points for single players |
| **player_single_fallback** | Default player stats | Fallback single player data by position |
| **stat_slip_types** | Statistic categories | Types of statistical information available |
| **subscription** | User preferences | User subscription settings for different notification types |
| **team_comparisons** | Team vs team stats | Comparison statistics between two specific teams |
| **team_comparisons_fallback** | Default team comparisons | Fallback team comparison data |
| **team_single** | Individual team stats | Statistics and bullet points for single teams |
| **team_single_fallback** | Default team stats | Fallback single team data |

## Detailed Table Descriptions

### Core Configuration Tables

| Table | Description | Key Columns |
|-------|-------------|-------------|
| **languages** | Multi-language support configuration | `name`, `shortcode`, `flag` |
| **stat_slip_types** | Statistical category definitions | `name` |
| **player_positions** | Player role/position master data | `name`, `order`, `group` |
| **player_pair_categories** | Pairing classification system | `name` |

### Player Data Tables

| Table | Description | Content Structure |
|-------|-------------|-------------------|
| **player_single** | Specific player statistics | 3 bullet points per player/stat_type/language |
| **player_single_fallback** | Position-based player defaults | 3 bullet points per position/stat_type/language |
| **player_comparisons** | Head-to-head player analysis | 3 bullet points per player pair/stat_type/language |
| **player_comparisons_fallback** | Category-based comparison defaults | 3 bullet points per category/stat_type/language |

### Team Data Tables

| Table | Description | Content Structure |
|-------|-------------|-------------------|
| **team_single** | Specific team statistics | 3 bullet points per team/stat_type/language |
| **team_single_fallback** | General team defaults | 3 bullet points per stat_type/language |
| **team_comparisons** | Head-to-head team analysis | 3 bullet points per team pair/stat_type/language |
| **team_comparisons_fallback** | General comparison defaults | 3 bullet points per stat_type/language |

### System Tables

| Table | Description | Purpose |
|-------|-------------|---------|
| **player_category_map** | Position relationship mapping | Links player positions to pair categories |
| **subscription** | User notification preferences | Controls which stat types users receive |

## Data Hierarchy & Fallback System

The database implements a sophisticated fallback system:

1. **Specific Data** → **Fallback Data**
   - Player-specific stats → Position-based stats
   - Team-specific stats → General team stats
   - Player pair comparisons → Category-based comparisons
   - Team pair comparisons → General comparisons

2. **Multi-language Support**
   - All content tables support multiple languages via `language_id`
   - Each statistical entry has 3 bullet points for comprehensive coverage

3. **Flexible Categorization**
   - Players grouped by positions with ordering and grouping
   - Player pairs categorized for targeted comparisons
   - Multiple stat slip types for different analytical perspectives