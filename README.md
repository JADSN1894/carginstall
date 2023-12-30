# carginstall
Generate artifacts for crates without official releases.

# Usage

```bash
CURRENT_REPO="JADSN1894/carginstall"
CURRENT_VERSION=$(gh --repo $CURRENT_REPO release view --json tagName --jq .tagName)
DOWNLOADED_FILES=$(gh --repo $CURRENT_REPO release view --json assets --jq '.assets[] | select(.name) .name')
for DOWNLOADED_FILE in $DOWNLOADED_FILES; do
    gh --repo $CURRENT_REPO release download $CURRENT_VERSION --pattern "$DOWNLOADED_FILE"
    chmod +x "$DOWNLOADED_FILE"
done
```
