# Troubleshooting

## Fedora-related issues

### chsh: command not found on Fedora TemplateVM
The package `util-linux-user` wasn't installed by default. To do so:

```
sudo dnf install util-linux-user
```
