# Global Sales Command Center (Interactive)

A cyberpunk-styled interactive 3D globe dashboard built with Apache ECharts-GL, displaying real-time customer distribution, revenue by country, and order flow visualization with clickable country details.

![globe gif](globe.gif)

## Features

### 3D Globe Visualization
- **Realistic Earth rendering** with atmosphere glow and bloom effects
- **Auto-rotating globe** with mouse-controlled pan and zoom
- **Cyberpunk aesthetic** with neon cyan/gold color scheme on black background

### Data Layers
- **Customer scatter points** - Sized by partner count, colored by revenue intensity
- **3D revenue bars** - Golden bars on top 5 revenue countries
- **Order flow arcs** - Animated lines flowing from customer countries to company HQ

### Interactive Elements
- **Clickable countries** - Click any scatter point or bar to open detail panel
- **Country detail popup** showing:
  - Total customers, orders, and revenue
  - List of up to 10 customers with email/phone
  - Recent orders with amounts and dates
- **Hover tooltips** with quick stats summary
- Auto-rotation pauses when detail panel is open

### Stats Overlay
- **Global stats panel** (top-right) showing:
  - Total countries with customers
  - Total customer count
  - Total orders
  - Total revenue
- **Top markets ranking** - Top 5 countries by revenue
- **HQ indicator** (bottom-left) showing company headquarters location
- Pulsing animation effect on stats panel

### Data Integration
- Pulls real data from `res.partner` (customers by country)
- Aggregates `sale.order` data from the last 365 days
- Groups revenue and order counts by country
- Automatically detects company HQ from `res.company`
- Supports 45+ country coordinate mappings

## Visual Effects

- Realistic globe shading with lighting and shadows
- Atmospheric glow around Earth
- Bloom post-processing for neon glow effect
- Animated trail effects on order flow arcs
- Smooth transitions and fade animations on popups

## Extensions Used

- `echarts-gl` - 3D globe and visualization
- `echarts-wordcloud` - Word cloud support
- `echarts-liquidfill` - Liquid fill charts
- `echarts-stat` - Statistical functions

## Import

1. Download `Global_Sales_Command_Center__Interactive_.csv` from this folder
2. In Odoo, go to **MCP Server > ECharts** list view
3. Click the **gear icon** (Actions) and select **Import records**
4. Upload the `.csv` file and follow the import wizard

## Requirements

- [Odoo MCP Studio](https://apps.odoo.com/apps/modules/19.0/odoo_remote_mcp)
- Sale orders and partner data with country assignments for meaningful visualization
