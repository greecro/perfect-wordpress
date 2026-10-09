# AGENTS.md — perfect-wordpress

Gemeinsame Instruktionsdatei für alle Agenten (Claude, Codex, Gemini); `CLAUDE.md` ist ein
Symlink hierauf.

**Öffentliches Produkt** (MIT, `github.com/greecro/perfect-wordpress`): ein Bash-Installer, der
auf einem *fremden* Ubuntu-24.04- oder Debian-13-Server eine gehärtete WordPress-Site aufsetzt —
Nginx + FastCGI-Cache, PHP-FPM (8.1–8.5 wählbar), MariaDB, Redis, UFW + Fail2ban, optional
Certbot, phpMyAdmin und FileBrowser. Details: [README.md](README.md) (englisch).

## Projektregeln

1. **Öffentliches Repo, fremde Zielgruppe.** Keine IPs, Hostnamen, Domains, Gast-IDs oder
   Lizenzschlüssel aus der Entwicklungsumgebung des Maintainers — auch nicht als „Beispiel". Alles Interne gehört in nicht öffentliche Repos.
2. **README und alle Ausgaben bleiben englisch.** Deutsche Strings sind hier ein Bug.
3. **Das ist ein Ein-Server-Installer:** eine Site pro Server, autark mit eigener MariaDB und
   eigenem TLS. Keine Logik aus Multi-Site- oder Shared-DB-Setups hierher kopieren.
4. **`proxmox-perfect-wordpress` ruft dieses Repo auf.** Wer Optionen, Prompts oder Flags des
   Installers ändert, prüft den Wrapper mit — sonst bricht er stumm.
5. **Der One-line-Installer zieht direkt von GitHub.** Ein Push wirkt sofort bei fremden Nutzern;
   nichts Halbfertiges auf den Standard-Branch.
6. **Idempotenz und Rerun-Sicherheit** sind Produkteigenschaften: `install`, `update` und `reset`
   müssen auf einem bereits eingerichteten Server berechenbar reagieren.
