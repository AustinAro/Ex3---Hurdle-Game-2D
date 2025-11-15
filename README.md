# Ex3 Hurdle Game 2D
## AIM:
To develop a 2D game using C# program in unity .

## ALGORITHM:
### STEP 1:
Create a 2D project in unity.
### STEP 2:
Add player,hurdles,coins,track in the frame and add the valid collider2D component.
### STEP 3:
Click Assets->Create-># Script.
### STEP 4:
create player.cs and coinmanger script and add c# code.
### STEP 5:
Click canvas->Gamemanager->add Score and value.
### STEP 6:
Drag the script to player and coin.
### STEP 7:
Run the scene and display the output.

## PROGRAM:
```
Developed by: Austin Aro A
Register no: 212224040038
```
### player.cs :
```
using System;
using UnityEngine;
public class Player : MonoBehaviour
{
    public float speed, jumpForce;
    private Rigidbody2D rb;
    public Score cc;
    void Start()
    {
        rb=GetComponent<Rigidbody2D>();
        
    }
    void Update()
    {
        float moveinp = Input.GetAxisRaw("Horizontal");
        transform.position += new Vector3(moveinp, 0, 0) * Time.deltaTime * speed;
        if (Input.GetKeyDown(KeyCode.Space) && Mathf.Abs(rb.linearVelocity.y) < 0.001f)
        {
            rb.AddForce(new Vector2(0, jumpForce), ForceMode2D.Impulse);
        }
    }
    private void OnTriggerEnter2D(Collider2D other)
    {
        if (other.CompareTag("Destroy"))
        {
            cc.coincount++;
            Destroy(other.gameObject);
        }
    }
}
```
### Score.cs :
```
using UnityEngine;
using UnityEngine.UI;

public class Score : MonoBehaviour
{
    public int coincount;
    public Text Value;
    // Start is called once before the first execution of Update after the MonoBehaviour is created
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        Value.text = coincount.ToString();
    }
}
```

## OUTPUT:
<img width="1919" height="1136" alt="Screenshot 2025-11-15 224717" src="https://github.com/user-attachments/assets/1d1fade3-fd00-4ede-9c50-3efccd9f9e65" />
<img width="1918" height="1137" alt="Screenshot 2025-11-15 224649" src="https://github.com/user-attachments/assets/23915d15-79d4-41b7-adb3-dc57c6f19d55" />

## RESULT:
Thus a 2D game using C# program in unity is developed successfully.
