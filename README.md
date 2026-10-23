# XKNX-Editor for Unraid

An Unraid Docker template for [XKNX-Editor](https://github.com/XKNX/xknx-editor), a web-based editor for creating and managing KNX smart home projects.

The template makes it easy to run XKNX-Editor on Unraid with persistent storage for application data and KNX projects.

## Features

- Easy installation through an Unraid Docker template
- Web-based user interface
- Persistent storage for application data and settings
- Separate storage for KNX projects
- Configurable web interface port
- Password protection through an environment variable
- Based on the official XKNX-Editor container image

## Docker Image

The template uses the official container image:

[`ghcr.io/xknx/xknx-editor-web:latest`](https://github.com/orgs/XKNX/packages)

## Installation

### Unraid Community Applications

Once this template has been accepted into Unraid Community Applications:

1. Open **Apps** in the Unraid web interface.
2. Search for **XKNX-Editor**.
3. Select the application and click **Install**.
4. Configure the storage paths, web interface port, and password.
5. Apply the configuration and start the container.

### Manual Installation

You can also install the template manually:

1. Open the Unraid web interface.
2. Navigate to **Docker**.
3. Select **Add Container** and switch to template or XML-based installation, depending on your Unraid version.
4. Use the template XML from this repository:

   `templates/xknx-editor.xml`

5. Review the configuration and start the container.

## Configuration

| Setting | Default | Description |
|---|---|---|
| Web UI Port | `8080` | Host port used to access the web interface |
| Application Data | `/mnt/user/appdata/xknx-editor/data` | Persistent application data and settings |
| KNX Projects | `/mnt/user/appdata/xknx-editor/projects` | Persistent storage for KNX projects |
| Web Password | User-defined | Password passed to the container through `XKNX_WEB_PASSWORD` |

The container paths `/data` and `/projects` are mapped to the corresponding host directories.

Choose a strong password during installation and do not expose the web interface directly to the public internet without appropriate security measures.

## Accessing the Web Interface

After the container has started, open the following URL in your browser:

`http://YOUR-UNRAID-IP:8080/`

Replace `YOUR-UNRAID-IP` with the IP address of your Unraid server. If you configured a different host port, use that port instead.

## Data Persistence

The template uses two persistent directories:

- `appdata/xknx-editor/data` for application data and settings
- `appdata/xknx-editor/projects` for KNX projects

Back up these directories regularly to protect your configuration and project files.

## Troubleshooting

- **The web interface is unavailable:** Check whether the container is running and whether the configured host port is available.
- **Projects are not retained:** Verify the host path mapping for `/projects` and ensure the directory is writable by the container.
- **Authentication does not work:** Verify that `XKNX_WEB_PASSWORD` is configured correctly and consult the upstream project's documentation.
- **Container startup fails:** Check the container logs in the Unraid Docker interface.

## Upstream Project

XKNX-Editor is maintained by the XKNX project.

- **Source code:** https://github.com/XKNX/xknx-editor
- **Issues and support:** https://github.com/XKNX/xknx-editor/issues
- **Container image:** https://github.com/orgs/XKNX/packages

Please report application-specific bugs to the upstream project. Issues related to this Unraid template can be reported in this repository.

## Disclaimer

This repository provides an Unraid template for the XKNX-Editor container. It is not an official XKNX project and is maintained independently.

XKNX-Editor and its container image remain the property of their respective authors. Please refer to the upstream repository for licensing information.

## License

The licensing terms for this Unraid template should be specified separately from the upstream XKNX-Editor project. See the `LICENSE` file in this repository for details.
