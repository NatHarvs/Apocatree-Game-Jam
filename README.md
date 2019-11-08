# Apocatree-Game-Jam
Ukie Game Jam 2019


Changes scene from Menu to Game after Start button clicked:
```
public class StartGame : MonoBehaviour
{
    public void PlayGame()
    {
        //Scene changes from Menu to Game.
        SceneManager.LoadScene(SceneManager.GetActiveScene().buildIndex + 1);
    }
}
```

Button makes audio when clicked:
```
public class ButtonSound : MonoBehaviour
{
    public AudioSource mySound;
    public AudioClip clickButton;

    public void ClickSound()
    {
        //If audio is not playing when clicked, play audio.
        if (mySound != null)
        {
            mySound.PlayOneShot(clickButton);
        }
    }
    
}
```

Button slider in option menu adjusts music:
```
public class SetVolume : MonoBehaviour
{
    public AudioMixer mixer;
    
    public void SetLevel (float sliderValue)
    {
        //Logarithmic math. Indice value multiply 20.
        mixer.SetFloat("MusicVol", Mathf.Log10(sliderValue) * 20);
    }
}
```

Return to menu:
```
public class ReturnToMenu : MonoBehaviour
{
    void Update()
    {
        if (Input.GetKeyDown(KeyCode.E))
        {
            //When E Key pressed, Game scene goes to Menu scene.
            SceneManager.LoadScene(SceneManager.GetActiveScene().buildIndex - 1);
        }
    }
}
```

Pause Game:
```
public class PauseGame : MonoBehaviour
{
    public static bool isPaused = false;
    public GameObject pauseMenuGUI;

    void Update()
    {
        if (Input.GetKeyDown(KeyCode.Space))
        {
            if (isPaused)
            {
                Resume();
            }
            else
            {
                Pause();
            }
        }
        
    }

    void Resume()
    {
        //Pause menu removed, time continues.
        pauseMenuGUI.SetActive(false);
        Time.timeScale = 1f;
        isPaused = false;
    }

    void Pause()
    {
        //Pause menu appears, time stops.
        pauseMenuGUI.SetActive(true);
        Time.timeScale = 0f;
        isPaused = true;
    }
}
```

Close down the application:
```
public class ExitMenu : MonoBehaviour {

    public void Exit()
    {
        //Game closes when exit button is clicked.
        Application.Quit();
    }
}
```
