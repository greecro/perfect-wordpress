# AGENTS.md — perfect-wordpress

Gemeinsame Instruktionsdatei für alle Agenten (Claude, Codex, Gemini); `CLAUDE.md` ist ein
Symlink hierauf. Globale Regeln: `~/Developer/KI/neo.md`.

**Öffentliches Produkt** (MIT, `github.com/greecro/perfect-wordpress`): ein Bash-Installer, der
auf einem *fremden* Ubuntu-24.04- oder Debian-13-Server eine gehärtete WordPress-Site aufsetzt —
Nginx + FastCGI-Cache, PHP-FPM (8.1–8.5 wählbar), MariaDB, Redis, UFW + Fail2ban, optional
Certbot, phpMyAdmin und FileBrowser. Details: [README.md](README.md) (englisch).

## Projektregeln

1. **Öffentliches Repo, fremde Zielgruppe.** Keine IPs, Hostnamen, Domains, Gast-IDs oder
   Lizenzschlüssel aus Danys Umgebung — auch nicht als „Beispiel". Alles Interne gehört nach
   `wp-hosting-scripts` bzw. `homelab-provisioning`.
2. **README und alle Ausgaben bleiben englisch.** Deutsche Strings sind hier ein Bug.
3. **Das ist nicht `wp-hosting-scripts`** und ersetzt es nicht. Hier: **eine** Site pro Server,
   autark mit eigener MariaDB und eigenem TLS. Dort: viele Sites pro VM an einer gemeinsamen
   DB-VM hinter Caddy. Keine Logik zwischen den beiden hin- und herkopieren.
4. **`proxmox-perfect-wordpress` ruft dieses Repo auf.** Wer Optionen, Prompts oder Flags des
   Installers ändert, prüft den Wrapper mit — sonst bricht er stumm.
5. **Der One-line-Installer zieht direkt von GitHub.** Ein Push wirkt sofort bei fremden Nutzern;
   nichts Halbfertiges auf den Standard-Branch.
6. **Idempotenz und Rerun-Sicherheit** sind Produkteigenschaften: `install`, `update` und `reset`
   müssen auf einem bereits eingerichteten Server berechenbar reagieren.
