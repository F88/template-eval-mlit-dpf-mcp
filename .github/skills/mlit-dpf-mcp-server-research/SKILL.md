---
name: mlit-dpf-mcp-server-research
description: Researching data from MLIT Data Platform using mlit-dpf-mcp server tools.
---

# MLIT Data Platform MCP Server Research Skill

## Overview

This skill utilizes the `mlit-dpf-mcp` server tools to search, retrieve, and analyze data from the MLIT Data Platform (国土交通データプラットフォーム). It enables interaction with the platform's API through natural language queries or specific tool calls.

## Tools & Usage

The following tools are available for researching data:

### Search & Discovery

- **`mcp_mlit-dpf-mcp_search`**
  - **Purpose**: Keyword search for datasets.
  - **Usage**: Use `term` for keywords. Supports sorting and pagination.
  - _Example_: "Search for 'bridges' sorted by update date" -> `term="橋梁", sort_attribute_name="DPF:updated_at", sort_order="dsc"`

- **`mcp_mlit-dpf-mcp_search_by_attribute`**
  - **Purpose**: Search using specific attributes like catalog name, dataset name, prefecture, etc.
  - **Usage**: Specify attributes to filter data more precisely.

- **`mcp_mlit-dpf-mcp_get_suggest`**
  - **Purpose**: Get keyword suggestions.
  - **Usage**: Useful when you are unsure of the exact search terms.

### Geospatial Search

- **`mcp_mlit-dpf-mcp_search_by_location_rectangle`**
  - **Purpose**: Search data within a specified rectangular area.
  - **Usage**: Requires top-left and bottom-right latitude/longitude coordinates.

- **`mcp_mlit-dpf-mcp_search_by_location_point_distance`**
  - **Purpose**: Search data within a circle defined by a center point and radius.
  - **Usage**: Requires center latitude, longitude, and radius (in meters).

### Data Retrieval

- **`mcp_mlit-dpf-mcp_get_data`**
  - **Purpose**: Get detailed metadata for a specific data item.
  - **Usage**: Requires `dataset_id` and `data_id` (obtained from search results).

- **`mcp_mlit-dpf-mcp_get_data_summary`**
  - **Purpose**: Get basic information (ID, Title) for a specific data item.
  - **Usage**: Lighter version of `get_data`.

- **`mcp_mlit-dpf-mcp_get_all_data`**
  - **Purpose**: Bulk retrieve large amounts of data matching specified conditions.
  - **Usage**: Use filters such as `term`, attributes, and geographic bounds. Retrieves data in batches.

- **`mcp_mlit-dpf-mcp_get_count_data`**
  - **Purpose**: Get the count of data items matching specified conditions.
  - **Usage**: Useful for estimating data volume before performing a full retrieval with `get_all_data`.

- **`mcp_mlit-dpf-mcp_get_mesh`**
  - **Purpose**: Retrieve data contained within a specified mesh code.
  - **Usage**: Requires a mesh code. Useful for spatial analysis based on standard mesh divisions.

- **`mcp_mlit-dpf-mcp_get_data_catalog`** / **`mcp_mlit-dpf-mcp_get_data_catalog_summary`**
  - **Purpose**: Retrieve info about data catalogs and datasets.

### Utility & Downloads

- **`mcp_mlit-dpf-mcp_get_file_download_urls`**: Get download URLs for dataset files (valid for 60s).
- **`mcp_mlit-dpf-mcp_get_zipfile_download_url`**: Get ZIP download URL for multiple files.
- **`mcp_mlit-dpf-mcp_get_thumbnail_urls`**: Get thumbnail image URLs (valid for 60s).
- **`mcp_mlit-dpf-mcp_normalize_codes`**: Normalize prefecture/municipality names to official codes.
- **`mcp_mlit-dpf-mcp_get_prefecture_data`**: Get a list of all prefectures with their codes and names.
- **`mcp_mlit-dpf-mcp_get_municipality_data`**: Get a list of municipalities, optionally filtered by prefecture or municipality code.

## References

- **Source Code**: [GitHub - MLIT-DATA-PLATFORM/mlit-dpf-mcp](https://github.com/MLIT-DATA-PLATFORM/mlit-dpf-mcp)
- **Usage Guide**: [README](https://raw.githubusercontent.com/MLIT-DATA-PLATFORM/mlit-dpf-mcp/refs/heads/main/README.md)
- **DeepWiki Architecture**: [DeepWiki - System Architecture](https://deepwiki.com/MLIT-DATA-PLATFORM/mlit-dpf-mcp/3-system-architecture)
- **Context7 Page**: [Context7 - MLIT DATA PLATFORM MCP](https://context7.com/mlit-data-platform/mlit-dpf-mcp)
