# Odoo MCP Studio - Demo App Library

A collection of ready-to-import demo applications and EChart dashboards for the
[Odoo MCP Studio - AI App & EChart Builder](https://apps.odoo.com/apps/modules/19.0/odoo_remote_mcp) module.

## About

This repository provides pre-built templates that you can import directly into your Odoo instance.
Each demo app serves as a working example you can use as-is or as a starting point for your own projects.

## What's Included

### Web Applications

Each app lives in its own folder and contains:

- `README.md` - Description, screenshots, and usage instructions for the app
- `.xlsx` - Export file ready to import into Odoo

### EChart Dashboards

Pre-built dashboard examples demonstrating various Apache ECharts visualization types, including charts,
3D visualizations, globe maps, wordclouds, and more.

## How to Import

1. Install [Odoo MCP Studio](https://apps.odoo.com/apps/modules/19.0/odoo_remote_mcp) on your Odoo 19 instance
2. Download the `.xlsx` file from the demo app you want to import
3. In Odoo, navigate to **MCP Server > Web Apps** (or **ECharts** for dashboards) to open the list view
4. Click the **gear icon** (Actions) and select **Import records**
5. Upload the downloaded `.xlsx` file and follow the import wizard
6. The app or dashboard will be created and ready to use

## Repository Structure

```
odoo_mcp_app_library/
  app-name/
    README.md
    app-name.xlsx
  another-app/
    README.md
    another-app.xlsx
  ...
```

## Requirements

- Odoo 16+
- [Odoo MCP Studio - AI App & EChart Builder](https://apps.odoo.com/apps/modules/19.0/odoo_remote_mcp) v3.0+

## License

See [LICENSE](LICENSE) for details.
