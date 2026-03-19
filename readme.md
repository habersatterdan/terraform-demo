# Terraform GitHub Repository Manager

Dieses Projekt erstellt und verwaltet GitHub Repositories automatisiert mit **Terraform** und dem offiziellen GitHub Provider.

---

## Voraussetzungen

- [Terraform](https://developer.hashicorp.com/terraform/downloads) >= 1.0
- GitHub Account
- GitHub Fine-Grained Personal Access Token mit folgenden Berechtigungen:
  - `Administration: Read and Write`
  - `Contents: Read and Write`
  - `Metadata: Read`

---

## Projektstruktur

```
terraform-project/
├── main.tf            # Ressourcen (Repository, Dateien)
├── providers.tf       # GitHub Provider Konfiguration
├── variables.tf       # Variablen-Definitionen
├── terraform.tfvars   # Variablen-Werte (nicht in Git!)
├── outputs.tf         # Outputs (z. B. Repository URL)
└── README.md          # Diese Datei
```

---

## Konfiguration

`terraform.tfvars` lokal anlegen (wird nicht gepusht):

```hcl
github_token = "github_pat_..."
github_owner = "dein-username"
repo_name    = "terraform-demo"
```

---

## Verwendung

```bash
# Provider initialisieren
terraform init

# Änderungen prüfen
terraform plan

# Infrastruktur anwenden
terraform apply

# Infrastruktur wieder entfernen
terraform destroy
```

---

## Erstellt

| Ressource | Beschreibung |
|---|---|
| `github_repository` | Neues öffentliches GitHub Repository |
| `github_repository_file` | README.md wird automatisch ins Repository hochgeladen |

---

## Sicherheit

Die Datei `terraform.tfvars` enthält sensible Zugangsdaten und ist in `.gitignore` eingetragen. Sie wird **niemals** in das Repository gepusht.

```
# .gitignore
.terraform/
*.tfstate
*.tfstate.backup
terraform.tfvars
```

---

## Autor

Erstellt im Rahmen eines DevOps Lab Projekts – Infrastructure as Code mit Terraform.