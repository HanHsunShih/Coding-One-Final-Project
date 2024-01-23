# Coding-One-Final-Project
## About My Project
####
I used the THREE.js I learned in Lesson 6 (week7) to make the final project. I added some effects and experimented with the original class assignment.In the original assignment, I just made a simple plane as the floor, and put two rotating cylinders and pasted pictures of jellyfish on them.
####
For this final assignment, I first added the background of the starry sky and made the space on the second side.I really like how jellyfish look in the tank in aquarium, so I made a total of four cylinders and sticked the jellyfish pattern on them. 
<img width="1186" alt="截圖 2022-12-05 11 01 28" src="https://user-images.githubusercontent.com/109679670/205621514-513c74b5-6436-4343-9c59-b276e61b8edc.png">
####
I collected photos of jellyfish in both dark blue and light pink patterns, and when I accidentally overlapped jellyfish cylinders with different pictures posted on them, I found them to have an interesting spiral effect. I changed all four columns into this form.
####
In the middle I put two rotating torus, which are also rotating, and in the very center is a sphere symbolizing the ocean.
####
I was inspired by the Javascript Crash Course 7 and wanted to add some mechanism for interacting with the mouse, and then I decided to use the mouse to change the color of the environment. I wrote the code from line 212 to line 236, hoping that the light of the entire environment will change when the mouse is clicked, symbolizing the various color changes of the ocean seen at different time points, but my code did not work.
```
//set light
    var n = 0;
        const Lightcolor1 = "#FFFFFF";
        const Lightcolor2 = "#960018";
        let Lightcolor = 0;
        let satuation = 1;
       
        //click to change
        function ClickEve() {
            n++;
            console.log(n);
            if (n % 2 != 0) {
            Lightcolor = Lightcolor2;
            }
            else {
                Lightcolor = Lightcolor1;
            }
        }
      canvas.addEventListener("click", ClickEve);
        let light2 = new THREE.DirectionalLight(Lightcolor, satuation);
        light2.position.set(0, 0, 30);
        scene.add(light2);
        renderer.render(scene, camera);
```        
#### 
I'm still trying to figure it out. In addition, I also hope to add and change the picture of the ocean on the middle sphere in the future to echo the ambient light.
####
In addition, when trying to add mouse interaction, the canvas shrinks for some reason, and the background color that should not appear on the top appears. This part also needs to be resolved.


# Mimic Link
https://mimicproject.com/code/50e09956-1661-08f8-16a3-2de76282c42a

# Youtube Link
https://youtu.be/0cT_Oz8a_p0![image](https://user-images.githubusercontent.com/109679670/205622217-aa3ec272-941e-4d81-94d3-426b2ee4aba4.png)



# Code HTML Javascript

```javascript
<html>

<head>
 <!-- This is an HTML comment -->
 <!-- Below we are grabbing three.js and some helper stuff for using the camera -->
 <script src = "https://cdnjs.cloudflare.com/ajax/libs/three.js/109/three.min.js"></script>
  <script src = "orbitControls.js"></script>
  
	<meta charset="utf-8">
	<style>
		body {
			margin: 0px; 
			background-color: #ccd5ae;
			overflow: hidden;

         
	</style>
</head>

<body>
    <canvas id = "jellyFish"></canvas>
	<script>
     
      
    const canvas = document.getElementById("jellyFish");
    /*var width = window.innerWidth;
    var height = window.innerHeight;
    canvas.setAttribute("width", width);
    canvas.setAttribute("height", height);*/
    
	var camera = new THREE.PerspectiveCamera(70, window.innerWidth / window.innerHeight, 0.1, 100); 
  
	//add background texture
    var scene = new THREE.Scene();
    var loader = new THREE.TextureLoader();
    var bgTexture = loader.load('BG.jpeg');
    scene.background = bgTexture;
      
      
    var geometry1 = new THREE.PlaneGeometry( 100, 100 );
    var myTextureLoader = new THREE.TextureLoader();
    var myTexture = myTextureLoader.load('jelly fish.jpeg');
    var material1 = new THREE.MeshBasicMaterial({map: myTexture});
    var cube = new THREE.Mesh( geometry1, material1 );
    scene.add( cube );
    cube.position.set(0,50,0)
    
      
    var geometry0 = new THREE.PlaneGeometry( 100, 100 );
    var myTextureLoader0 = new THREE.TextureLoader();
    var myTexture0 = myTextureLoader.load('jelly fish.jpeg');
    var material10 = new THREE.MeshBasicMaterial({map: myTexture0});
    var mesh0 = new THREE.Mesh( geometry0, material );
    scene.add( cube );
    mesh0.position.set(0,50,100)
	
    var geometry = new THREE.CylinderGeometry( 3, 5, 45, 20 );
    var myTextureLoader = new THREE.TextureLoader();
    var myTexture = myTextureLoader.load('jelly fish.jpeg');
    var material = new THREE.MeshPhongMaterial({map: myTexture});
    var mesh = new THREE.Mesh(geometry, material);
    scene.add(mesh);  
    mesh.position.set(30,10,0)
    
    
    var geometry2 = new THREE.CylinderGeometry( 3, 5, 45, 20 );
    var myTextureLoader2 = new THREE.TextureLoader();
    var myTexture2 = myTextureLoader.load('jellyfish2.jpeg'); 
    var material2 = new THREE.MeshPhongMaterial({map: myTexture2});
    var mesh2 = new THREE.Mesh(geometry2, material2);
    scene.add(mesh2);  
    mesh2.position.set(30,10,0)
    
    
     
    var geometry3 = new THREE.PlaneGeometry( 100, 100 );
    var myTextureLoader3 = new THREE.TextureLoader();
    var myTexture3 = myTextureLoader.load('jellyfish2.jpeg'); 
    var material3 = new THREE.MeshPhongMaterial({map: myTexture3});
    var mesh3 = new THREE.Mesh(geometry3, material3);
    scene.add(mesh3);  
    mesh3.position.set(0,0,0)
    mesh3.rotation.x = 5;
      
var geometry4 = new THREE.CylinderGeometry( 3, 5, 45, 20 );
    var myTextureLoader4 = new THREE.TextureLoader();
    var myTexture4 = myTextureLoader.load('jelly fish.jpeg');
    var material4 = new THREE.MeshPhongMaterial({map: myTexture});
    var mesh4 = new THREE.Mesh(geometry4, material4);
    scene.add(mesh4);  
    mesh4.position.set(-30,10,0)
    
    
    var geometry5 = new THREE.CylinderGeometry( 3, 5, 45, 20 );
    var myTextureLoader5 = new THREE.TextureLoader();
    var myTexture5 = myTextureLoader.load('jellyfish2.jpeg'); 
    var material5 = new THREE.MeshPhongMaterial({map: myTexture2});
    var mesh5 = new THREE.Mesh(geometry2, material2);
    scene.add(mesh5);  
    mesh5.position.set(-30,10,0)
    
    
   var geometry6 = new THREE.TorusGeometry( 5, 0, 16, 100 );
   var myTextureLoader6 = new THREE.TextureLoader();
   var myTexture6 = myTextureLoader.load('jellyfish2.jpeg');
   var materia6 = new THREE.MeshBasicMaterial( {map: myTexture6} );
   const mesh6 = new THREE.Mesh( geometry6, material );
scene.add( mesh6 );
      mesh6.position.set(0,13,30)
      
   var geometry7 = new THREE.TorusGeometry( 8, 0, 16, 100 );
   var myTextureLoader7 = new THREE.TextureLoader();
   var myTexture7 = myTextureLoader.load('jellyfish2.jpeg');
   var materia7 = new THREE.MeshBasicMaterial( {map: myTexture7} );
   const mesh7 = new THREE.Mesh( geometry7, material );
scene.add( mesh7 );
      mesh7.position.set(0,13,30)
      
   
    var geometry8 = new THREE.CylinderGeometry( 3, 5, 45, 20 );
    var myTextureLoader8 = new THREE.TextureLoader();
    var myTexture8 = myTextureLoader.load('jelly fish.jpeg');
    var material8 = new THREE.MeshPhongMaterial({map: myTexture});
    var mesh8 = new THREE.Mesh(geometry, material);
    scene.add(mesh8);  
    mesh8.position.set(30,10,30)
    
    
    var geometry9 = new THREE.CylinderGeometry( 3, 5, 45, 20 );
    var myTextureLoader9 = new THREE.TextureLoader();
    var myTexture9 = myTextureLoader.load('jellyfish2.jpeg'); 
    var material9 = new THREE.MeshPhongMaterial({map: myTexture2});
    var mesh9 = new THREE.Mesh(geometry2, material2);
    scene.add(mesh9);  
    mesh9.position.set(30,10,30)

    var geometry10 = new THREE.CylinderGeometry( 3, 5, 45, 20 );
    var myTextureLoader10 = new THREE.TextureLoader();
    var myTexture10 = myTextureLoader.load('jelly fish.jpeg');
    var material10 = new THREE.MeshPhongMaterial({map: myTexture});
    var mesh10 = new THREE.Mesh(geometry, material);
    scene.add(mesh10);  
    mesh10.position.set(-30,10,30)
    
    
    var geometry11 = new THREE.CylinderGeometry( 3, 5, 45, 20 );
    var myTextureLoader11 = new THREE.TextureLoader();
    var myTexture11 = myTextureLoader.load('jellyfish2.jpeg'); 
    var material11 = new THREE.MeshPhongMaterial({map: myTexture2});
    var mesh11 = new THREE.Mesh(geometry2, material2);
    scene.add(mesh11);  
    mesh11.position.set(-30,10,30)
      
    var sphere = new THREE.SphereGeometry( 2, 32, 16 );
    var myTextureLoader12 = new THREE.TextureLoader();
    var myTexture12 = myTextureLoader12.load('ocean.jpeg'); 
    var material12 = new THREE.MeshPhongMaterial({map: myTexture12});
    var mesh12 = new THREE.Mesh(sphere, material12);
    scene.add(mesh12);  
    mesh12.position.set(0,13,30)
      
      
      
     
	var light = new THREE.DirectionalLight("rgb(250,255,255)");

	var renderer = new THREE.WebGLRenderer();


	camera.position.set(0,0,30);

	light.position.set(0,0,30);

	scene.add(mesh);
	scene.add(light);

      renderer.setPixelRatio(window.devicePixelRatio);
	
      renderer.setSize(window.innerWidth, window.innerHeight);

      document.body.appendChild(renderer.domElement);


	window.addEventListener('resize', onWindowResize, false); 
    var controls = new THREE.OrbitControls (camera, renderer.domElement);

   
function draw() {
 	//mesh.rotation.x += 0.005;
  	//mesh.position.x = 0;
	mesh.rotation.y+= 0.01;
    mesh2.rotation.y+= -0.01;
    mesh4.rotation.y+= 0.01;
    mesh5.rotation.y+= -0.01;
    mesh6.rotation.y+= 0.01;
    mesh6.rotation.z+= 0.01;
    mesh7.rotation.y+= -0.02;
    mesh7.rotation.z+= -0.02;
    mesh8.rotation.y+= 0.01;
    mesh9.rotation.y+= -0.01;
    mesh10.rotation.y+= 0.01;
    mesh11.rotation.y+= -0.01;
    mesh12.rotation.y+= -0.008;
    //camera.position.z = 30;
    //camera.position.x += -0.1;
    controls.update();
	renderer.render(scene, camera);
	requestAnimationFrame(draw);
}
      
      //set light
    var n = 0;
        const Lightcolor1 = "#FFFFFF";
        const Lightcolor2 = "#960018";
        let Lightcolor = 0;
        let satuation = 1;
       
        //click to change
        function ClickEve() {
            n++;
            console.log(n);
            if (n % 2 != 0) {
            Lightcolor = Lightcolor2;
            }
            else {
                Lightcolor = Lightcolor1;
            }
        }
      canvas.addEventListener("click", ClickEve);
        let light2 = new THREE.DirectionalLight(Lightcolor, satuation);
        light2.position.set(0, 0, 30);
        scene.add(light2);
        renderer.render(scene, camera);
        

     
function onWindowResize() {
	camera.aspect = window.innerWidth / 		window.innerHeight;
	camera.updateProjectionMatrix();
	renderer.setSize(window.innerWidth, window.innerHeight);
}    
     
requestAnimationFrame(draw());
      
	</script>
</body>


</html>
```
