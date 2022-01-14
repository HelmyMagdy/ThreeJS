# ThreeJS
<!-- My scene -->
	<canvas id="scene"></canvas>
<script src="three.min.js"></script>
<script src="GLTFLoader.js"></script>

<script>

//Get the height and the width of the window
var ww = window.innerWidth,
	wh = window.innerHeight;
speed=5;	
positionn=true;
	moveRight = true;
	rotateOnRed=true;
	counter=0;
	rotateCounts=0;
	numberOfRot = 3;
	angle = Math.PI/30;
	stopAt =((Math.PI/angle) * 2) *numberOfRot;
	console.log("angle:: ",angle);
	console.log("numberOfRot:: ",stopAt);
var scene;
var camera;
var renderer;

function init(){

	/* WEBGL RENDERER */

	//Create the webGl renderer from Three
	renderer = new THREE.WebGLRenderer({canvas : document.getElementById('scene')});
	//Set the background of our scene
	renderer.setClearColor(0x000000);
	//Set the size of my renderer, I want it to be fullscreen
	renderer.setSize(ww,wh);


	/* SCENE */

	//Create my scene
	scene = new THREE.Scene();


	/* CAMERA */

	//Create a new Perspective Camera with four parameters
	
	camera = new THREE.PerspectiveCamera(100, ww/wh, 0.1, 10000 );
	//We set our camera at x:0,y:0 and z:500
	camera.position.set(0, 0, 500);
	//And finally we add our camera in our scene
	scene.add(camera);

 var directionLight = new THREE.DirectionalLight(0xFFFFFF, 0.5);
        directionLight.position.set(0, 10, 0);
        scene.add(directionLight);
		
		 var ambientLight = new THREE.AmbientLight(0xFFFFFF, 15);
        scene.add(ambientLight);


	//Create our spheres
	 manySpheres();
	 createShapes();
	 canon();







};

function manySpheres(){

	spheres = new THREE.Object3D();

	/* The Sphere */
    sphereGeometry = new THREE.SphereGeometry(2, 50, 50);
    sphereMaterial = new THREE.MeshBasicMaterial( {color:0xffffff} );//F8FF12

	//Generate 300 random spheres
	for(var i=0;i<300;i++){
		sphere = new THREE.Mesh( sphereGeometry, sphereMaterial );
		//Set random positions
		sphere.rotation.x = (Math.random()-.5)*Math.PI;
		sphere.rotation.y = (Math.random()-.5)*Math.PI;
		sphere.rotation.z = (Math.random()-.5)*Math.PI;

		sphere.position.x = (Math.random()-.5)*ww;
		sphere.position.y = (Math.random()-.5)*wh;
		sphere.position.z = (Math.random()-.5)*500;

		//Add the new cube in the 3D object
		spheres.add(sphere);
	}
	//spheres.translateY(500);

	//Add my spheres in my scene
	scene.add(spheres);
};

function createShapes(){
 geometry = new THREE.PlaneGeometry( 1000, 1000 );
 material = new THREE.MeshBasicMaterial( {color: 0xffffff, side: THREE.DoubleSide, transparent: true,opacity: 0.2} );
 plane = new THREE.Mesh( geometry, material );
 plane.rotation.x=-Math.PI/4;
scene.add( plane );
};


var mainSphere;
function canon(){

	cylinders = new THREE.Object3D();



 geometry3 = new THREE.BoxGeometry( 300, 40, 40 );
 material3 = new THREE.MeshBasicMaterial( {color: 0x00ff00} );
 cube = new THREE.Mesh( geometry3, material3 );
cube.position.y=-400;
cylinders.add( cube );

 geometry4 = new THREE.BoxGeometry( 50, 10, 10 );
 material4 = new THREE.MeshBasicMaterial( {color: 0x0000ff} );
 cube1 = new THREE.Mesh( geometry4, material4 );
cube1.position.y=-360;
cylinders.add( cube1 );

	sphereGeometry1 = new THREE.SphereGeometry(20,150,150);
	sphereMaterial1 = new THREE.MeshBasicMaterial({color:0xffffff});
	mainSphere = new THREE.Mesh(sphereGeometry1,sphereMaterial1);
    mainSphere.position.y=-370;
	
	cylinders.add(mainSphere);
	
	//Add my spheres in my scene
	scene.add(cylinders);
};

   var corona1;
   var corona2;
   var loader = new THREE.GLTFLoader();
        loader.load("models/corona.glb", function (model) {
		corona5=model.scene;
            corona5.scale.set(50, 50, 10);
            corona5.position.set(80, 400, -300);
            //added the model to the scene after it's loaded
            scene.add(corona5);
			});
			var loader = new THREE.GLTFLoader();
        loader.load("models/corona.glb", function (model) {
            model.scene.scale.set(50, 50, 10);
            model.scene.position.set(-350, 400, -300);
            //added the model to the scene after it's loaded
            scene.add(model.scene);
        });
					var loader = new THREE.GLTFLoader();
        loader.load("models/corona.glb", function (model) {
            model.scene.scale.set(50, 50, 10);
            model.scene.position.set(-150, 400, -300);
            //added the model to the scene after it's loaded
            scene.add(model.scene);
        });
							var loader = new THREE.GLTFLoader();
        loader.load("models/corona.glb", function (model) {
            model.scene.scale.set(50, 50, 10);
            model.scene.position.set(300, 400, -300);
            //added the model to the scene after it's loaded
            scene.add(model.scene);
        });
		 loader.load("models/corona.glb", function (model) {
		 corona4=model.scene;
            corona4.scale.set(50, 50, 10);
            corona4.position.set(80, 210, -100);
            //added the model to the scene after it's loaded
            scene.add(corona4);
        });
		 loader.load("models/corona.glb", function (model) {
            model.scene.scale.set(50, 50, 10);
            model.scene.position.set(-350, 210, -100);
            //added the model to the scene after it's loaded
            scene.add(model.scene);
        });
		 loader.load("models/corona.glb", function (model) {
            model.scene.scale.set(50, 50, 10);
            model.scene.position.set(-150, 210, -100);
            //added the model to the scene after it's loaded
            scene.add(model.scene);
        });
		 loader.load("models/corona.glb", function (model) {
            model.scene.scale.set(50, 50, 10);
            model.scene.position.set(300, 210, -100);
            //added the model to the scene after it's loaded
            scene.add(model.scene);
        });
		 loader.load("models/corona.glb", function (model) {
           corona1=model.scene;
		   corona1.scale.set(50, 50, 10);
            corona1.position.set(80, 75, 1);
            //added the model to the scene after it's loaded
            scene.add(corona1);
        });
		 loader.load("models/corona.glb", function (model) {
            corona2=model.scene;
            corona2.scale.set(50, 50, 10);
            corona2.position.set(-350, 75, 1);
            //added the model to the scene after it's loaded
            scene.add(corona2);
		});
		 loader.load("models/corona.glb", function (model) {
		 corona3 = model.scene;
            corona3.scale.set(50, 50, 10);
            corona3.position.set(-150, 75, 1);
            //added the model to the scene after it's loaded
            scene.add(corona3);
		});
		 loader.load("models/corona.glb", function (model) {
            model.scene.scale.set(50, 50, 10);
            model.scene.position.set(300, 75, 1);
            //added the model to the scene after it's loaded
            scene.add(model.scene);
		});
		
		

		
		
		
		
		function touching(a, d) {
  let b1 = a.position.y - a.geometry.parameters.height / 2;
  let t1 = a.position.y + a.geometry.parameters.height / 2;
  let r1 = a.position.x + a.geometry.parameters.width / 2;
  let l1 = a.position.x - a.geometry.parameters.width / 2;
  let f1 = a.position.z - a.geometry.parameters.depth / 2;
  let B1 = a.position.z + a.geometry.parameters.depth / 2;
  let b2 = d.position.y - d.geometry.parameters.height / 2;
  let t2 = d.position.y + d.geometry.parameters.height / 2;
  let r2 = d.position.x + d.geometry.parameters.width / 2;
  let l2 = d.position.x - d.geometry.parameters.width / 2;
  let f2 = d.position.z - d.geometry.parameters.depth / 2;
  let B2 = d.position.z + d.geometry.parameters.depth / 2;
  if (t1 < b2 || r1 < l2 || b1 > t2 || l1 > r2 || f1 > B2 || B1 < f2) {
    return false;
  }
  return true;
}
		
		
		
		
		
	/*function removecorona(){

	if(Math.abs(mainSphere.position.x - model.position.x)<45 && Math.abs(mainsphere.position.z - model.position.z)<45){

		scene.remove(model);
	}
	
};*/





var bulletMoving=false;
var bulletsCount=0;
function hitCorona(){
   mainSphere.position.y+=4;
if(mainSphere.position.y.toFixed(1)>35){
if(bulletsCount==0){
scene.remove(corona1);
}
if(bulletsCount==1){
scene.remove(corona2);
}
if(bulletsCount==2){
scene.remove(corona3);
}
if(bulletsCount==3){
scene.remove(corona4);
}
if(bulletsCount==4){
scene.remove(corona5);
}
bulletsCount++;
mainSphere.position.y=-370;
bulletMoving=false;
}
}





//create the key board input on the sphere using arrows of key board
document.onkeydown = function (e) {
            if (e.keyCode == '38')//Up
             {  console.log("up");
 bulletMoving=true;
                
	   } 

            else if (e.keyCode == '37')//Right
              { console.log("right");
			  cylinders.position.x -= speed*2;}
            else if (e.keyCode == '39')//Left
              {  cylinders.position.x += speed*2;}
         
                
        };

	

		
	

		
//Init our scene
init();

    function animate() {

          
            requestAnimationFrame(animate);
		renderer.render(scene,camera);
          if(bulletMoving){

         hitCorona();

        }
}



        animate();

        
</script>
