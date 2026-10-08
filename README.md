# janjuna.cz

Personal website of Jan Jůna, live at [janjuna.cz](https://janjuna.cz/).

It's a single static page (`index.html`) built on [Now UI Kit](https://www.creative-tim.com/product/now-ui-kit) (Bootstrap 4 + jQuery). There's no build step.

## Structure

| Path | Contents |
|---|---|
| `index.html` | The whole page: profile, skills, timeline, contact |
| `css/style.css` | Custom styles on top of Now UI Kit |
| `css/`, `js/`, `fonts/` | Vendor assets (Bootstrap, Now UI Kit, timeline plugin) |
| `img/profile.jpg` | Profile photo (square, shown in a circle) |
| `documents/` | CV in PDF, linked from the page |

## Local development

Serve the folder with any static server:

```sh
python3 -m http.server 8000
# open http://localhost:8000
```

## Deployment

Every push to `master` deploys automatically through GitHub Actions (`.github/workflows/main.yml`). The workflow rsyncs the repo over SSH to the web root on the server. It does not delete files on the server, so a file removed from the repo has to be removed from the server by hand.

The workflow uses these repository secrets:

| Secret | Purpose |
|---|---|
| `HOST` | Server hostname |
| `SSH_PORT` | SSH port (defaults to 22 when empty) |
| `USER` | SSH user |
| `SSH_KEY` | Private SSH key for that user |
| `PATH` | Target directory on the server |

The server's SSH host key is pinned in the workflow. If the server is reinstalled or its host key changes, update the `known_hosts` line in the workflow.
