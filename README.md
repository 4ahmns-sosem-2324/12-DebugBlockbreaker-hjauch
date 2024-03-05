# 12-DebugBlockbreaker-hjauch

```mermaid
classDiagram
    MonoBehaviour <|-- Ball
    MonoBehaviour <|-- Block
    MonoBehaviour <|-- GameSession
    MonoBehaviour <|-- Level
    MonoBehaviour <|-- LoseCollider
    MonoBehaviour <|-- Paddle
    MonoBehaviour <|-- SceneLoader
 
    class Ball {
        + paddle1: Paddle
        + xPush: float
        + yPush: float
        + ballSounds: AudioSource
        + randomFactor: float
        - hasStarted: bool
        - paddleToBallVector: Vector2;
        - myAudioSource: AudioSource
        - myRigidBody: Rigidbody2D
        - Start() void
        - Update() void
        - LaunchOnMouseClick() void
        - LockBallToPaddle() void
        - OnCollisionEnter2D() void
    }
    class Block {
        - BREAKABLE: const string
        - UNBREAKABLE: const string
        - level: Level
        - gameStatus: GameSession
        + breakSound: AudioSource
        + blockSparklesVFX: GameObject
        - [SerializeField] timesHit: int
        - Start() void
        - CountBreakableBlocks() void
        - OnCollisionEnter2D() void
        - HandleHit() void
        - ShowNextHitSprite() void
        - DestroyBlock() void
        - PlayBlockDestroySFX() void
        - TriggerSparkleVFX() void

    }
 
    class GameSession {
        + gameSpeed: float
        + pointsPerBlockDestroyed: int
        + scoreText: TextMeshProUGUI
        + isAutoPlayEnabled: bool
        + currentScore: int
        - Awake() void
        - Start() void
        - Update() void
        - AddToScore() void
        - ResetGame() void
        - isAutoPlayEnabled() bool
    }

     class Level {
        - [SerializeField] breakableBlocks: int
        - sceneLoader: SceneLoader
        - target: Transform
        - Start() void
        - CountBlocks() void
        - BlockDestroyed() void
        - LoadEndScreen() void
    }

     class LoseCollider {
        + loader: GameObject
        + sceneLoader: sceneLoader
        - Update() void
        - OnTriggerEnter2D() void
    }

     class Paddle {
        + minX: float
        + maxX: float
        + screenWidthInUnits: float
        - theGameSession: GameSession
        - theBall: Ball
        - Update() void
        - Start() void
        - GetXPosition() float

    }

     class SceneLoader {
        - GAMEOVERSCREEN: const string
        - CONGRATSSCREEN: const string
        - LEVEL5: const string
        - LoadNextScene() void
        - LoadWelcome() void
        - LoadGameOver() void
        - LoadCongrats() void
        - IsLastPlayScene() bool
    }
  ```
