# Open/Closed Principle (OCP)
**Definition:** Subtypes must be substitutable for their base types without altering the correctness of the program.

### Example: Media Player System
**Bad Example:**

```
class MediaPlayer {
  play(audioType: string, fileName: string) {
    if (audioType === 'mp3') {
      console.log(`Playing mp3 file: ${fileName}`);
    } else if (audioType === 'vlc') {
      console.log(`Playing vlc file: ${fileName}`);
    } else if (audioType === 'mp4') {
      console.log(`Playing mp4 file: ${fileName}`);
    } else {
      throw new Error('Invalid media type');
    }
  }
}

```

**Explanation:**

- Subclasses of `MediaPlayer` may not be able to handle all media types, leading to potential errors when substituting the base class.


**Good Example:**

```
interface MediaPlayer {
  play(fileName: string): void;
}

class Mp3Player implements MediaPlayer {
  play(fileName: string): void {
    console.log(`Playing mp3 file: ${fileName}`);
  }
}

class VlcPlayer implements MediaPlayer {
  play(fileName: string): void {
    console.log(`Playing vlc file: ${fileName}`);
  }
}

class Mp4Player implements MediaPlayer {
  play(fileName: string): void {
    console.log(`Playing mp4 file: ${fileName}`);
  }
}

class AudioPlayer {
  constructor(private player: MediaPlayer) {}

  playAudio(fileName: string) {
    this.player.play(fileName);
  }
}

```

**Explanation:**

- `Mp3Player`, `VlcPlayer`, and `Mp4Player` can replace `MediaPlayer` without affecting the correctness of the program.
- **Adherence to LSP:** Each player class can be substituted for the base type without any issues.
