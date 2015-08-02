# Unity3D Tutorial - BlockBuster

Script for camera controlss

```csharp
using UnityEngine;
using System.Collections;

public class CameraMovement : MonoBehaviour {
	public float speed = 1;

	// Update is called once per frame
	void Update () {
		// read key and move according to direction given in the movement vector
		if (Input.GetKey (KeyCode.UpArrow)) {
			transform.Translate(new Vector3(0f, Time.deltaTime * speed, 0f));
		} else if (Input.GetKey (KeyCode.DownArrow)) {
			// don't let camera move under ground
			if (transform.position.y > 0.5) {
				transform.Translate(new Vector3(0f, -Time.deltaTime * speed, 0f));
			}
		} else if (Input.GetKey (KeyCode.LeftArrow)) {
			transform.Translate(new Vector3(-Time.deltaTime * speed, 0f, 0f));
		} else if (Input.GetKey (KeyCode.RightArrow)) {
			transform.Translate(new Vector3(Time.deltaTime * speed, 0f, 0f));
		}
	}
}
```

Script for the bullet:

```csharp
using UnityEngine;
using System.Collections;

public class ShootBullet : MonoBehaviour {

	public float speed = 30;
	public Rigidbody projectile;

	void Update() {
		if (Input.GetButtonDown("Fire1")) {
			Rigidbody clone;
			clone = Instantiate(projectile, transform.position, transform.rotation) as Rigidbody;
			clone.velocity = transform.TransformDirection(Vector3.forward * speed);
		}
	}
}	
```

