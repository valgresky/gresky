[![Deploy to DigitalOcean](https://www.deploytodo.com/do-btn-blue.svg)](https://cloud.digitalocean.com/apps/new?repo=https://github.com/valgresky/gresky/tree/main)

# 🚀 Gresky: Codex Dev Agent Platform (MVP)

A secure, cloud-hosted development environment powered by OpenAI's Codex CLI and a browser-based IDE (code-server).

---

## 🔧 Requirements

- Ubuntu 22.04 (DigitalOcean droplet recommended)
- Docker + Docker Compose
- Domain name pointing to your droplet (for HTTPS)

---

## 📁 File Structure

```
gresky/
├── docker-compose.yml
├── Caddyfile
├── .env.example
└── codex-cli/            # Your cloned Codex CLI repo
```

---

## 📦 Installation Steps

### 1. SSH into your droplet
```bash
ssh root@your-digitalocean-ip
```

### 2. Install Docker
```bash
curl -fsSL https://get.docker.com | sh
```

### 3. Prepare your environment
```bash
git clone https://github.com/openai/codex.git codex-cli
cd gresky
cp .env.example .env
nano .env
```
_Fill in your OpenAI API key and secure password._

### 4. Start the stack
```bash
docker compose up -d
```

---

## 🌐 Access

Visit: `https://your-domain.com`

Login with your `BASIC_AUTH_USER` / `BASIC_AUTH_PASS`

---

## 🧠 Run Codex CLI

From the `code-server` terminal:
```bash
docker exec -it codex-agent codex "refactor this module"
```

---

## 🔐 Notes

- Code-server is password-protected via HTTP Basic Auth.
- HTTPS is provided by Caddy using Let's Encrypt.
- All code and CLI history is saved in the persistent `code-data` volume.

---

## 🧰 Coming Next

- GitHub OAuth login
- Workspace-based container spawning
- API triggerable Codex Agents

---

## 🧩 Credits

Built with ❤️ using:
- [code-server](https://github.com/coder/code-server)
- [OpenAI Codex CLI](https://github.com/openai/codex)
- [Caddy Server](https://caddyserver.com/)
