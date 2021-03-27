## Setting up GitHub Native Dependabot

```yml
version: 2
updates:
  - package-ecosystem: "npm"
    # Look for `package.json` and `lock` files
    directory: "/frontend"
    # Check the npm registry for updates every day (weekdays)
    schedule:
      interval: "daily"

  # Enable version updates for Maven
  - package-ecosystem: "maven"
    directory: "/backend"
    schedule:
      interval: "weekly"
  
  # Docs: https://dependabot.com/docs/config-file/
```
