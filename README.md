# Linux Login Sound

A small Bash script that plays a sound when you log in, at whatever volume you want, then puts the volume (and mute state) back where it was. Because why not.

Made for Ubuntu with PipeWire/WirePlumber. Requires `ffplay` and `wpctl`.

## Install

```bash
sudo apt install ffmpeg
mkdir -p ~/.local/bin ~/.config/autostart
cp login-sound.sh ~/.local/bin/
chmod +x ~/.local/bin/login-sound.sh
```

Edit these two lines in `~/.local/bin/login-sound.sh`:

```bash
SOUND="$HOME/Music/startup.mp3"  # MP3, OGG, WAV, etc.
VOLUME=100                    # 0-100%
```

Make it start when you log in:

```bash
cat > ~/.config/autostart/login-sound.desktop <<EOF_DESKTOP
[Desktop Entry]
Type=Application
Name=Login Sound
Exec=$HOME/.local/bin/login-sound.sh
Terminal=false
EOF_DESKTOP
```

Test it with `~/.local/bin/login-sound.sh`.

Each user can have their own sound. Runs **after desktop login**, not at boot. Changing the output volume also affects any other audio playing at the same time.
