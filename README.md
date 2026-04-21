# mini-app 

A minimal Flask web app with automated deployment to [Fly.io](https://fly.io) via GitHub Actions.

Every push to `main` automatically builds and ships the app live — no manual steps.



## Tech Stack

- **Python / Flask** — web framework
- **Gunicorn** — production WSGI server
- **Docker** — containerization
- **GitHub Actions** — CI/CD pipeline
- **Fly.io** — cloud hosting



## Project Structure

mini-app/
├── app.py                        # Flask app
├── requirements.txt              # Python dependencies
├── Dockerfile                    # Container config
├── fly.toml                      # Fly.io config (created after launch)
└── .github/
  └── workflows/
   └── deploy.yml             # CI/CD pipeline



## Run Locally

```bash
docker build -t mini-app .
docker run -p 8080:8080 mini-app
```

Visit `http://localhost:8080`


## Deploy

Deployment is automatic on every push to `main`.
To deploy manually:

```bash
flyctl deploy --remote-only
```

## Setup (one-time)

1. Install [flyctl](https://fly.io/docs/hands-on/install-flyctl/)
2. Run `flyctl auth login`
3. Then `flyctl launch`
4. Add `FLY_API_TOKEN` to GitHub repo secrets
   - Generate the token: `flyctl tokens create deploy`
   - Add to: **Repo → Settings → Secrets → Actions**

## Live URL

``https://your-app-name.fly.dev´´
