<!DOCTYPE html>
<html lang="en">
<head>
<title>Фигуры Вариант №3 </title>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, user-scalable=no, minimum-scale=1.0, maximum-scale=1.0">
<link type="text/css" rel="stylesheet" href="https://threejs.org/examples/main.css">
</head>
<body>


<script type="module">

import * as THREE from 'https://threejs.org/build/three.module.js';

import { OrbitControls } from 'https://threejs.org/examples/jsm/controls/OrbitControls.js';

var camera, scene, renderer;
var controls;
var ambientLight, light;
init();
animate();

function init() {

var container = document.createElement( 'div' );
document.body.appendChild( container );
// CAMERA
camera = new THREE.PerspectiveCamera( 45, window.innerWidth / window.innerHeight, 1, 8000 );
camera.position.set( 300, 700, 900 );
// LIGHTS
ambientLight = new THREE.AmbientLight( 0x333333 ); // 0.2
light = new THREE.DirectionalLight( 0xFFFFFF, 1.0 );
light.position.set( 1, 1, 1 );
// direction is set in GUI
// RENDERER
renderer = new THREE.WebGLRenderer( { antialias: true } );
renderer.setPixelRatio( window.devicePixelRatio );
renderer.setSize( window.innerWidth, window.innerHeight );
container.appendChild( renderer.domElement );
// EVENTS
window.addEventListener( 'resize', onWindowResize, false );
// CONTROLS
controls = new OrbitControls( camera, renderer.domElement );
controls.addEventListener( 'change', render );
//controls.rotateSpeed = 1;
controls.enableZoom = true;
controls.zoomSpeed = 0.5;
controls.minDistance = 500;
controls.maxDistance = 2500;
controls.enableDamping = true;
// scene itself
scene = new THREE.Scene();
scene.background = new THREE.Color( 0xD3D3D3 );
scene.add( ambientLight );
scene.add( light );
// scene objects

//1КУБОИД
var geometry = new THREE.BoxGeometry( 150, 150, 250 );
var material = new THREE.MeshPhongMaterial( { color: 0xFF0000} );
var Cuboid = new THREE.Mesh( geometry, material );
Cuboid.position.set( 450, 0, 0 );
Cuboid.rotation.z = Math.PI / 2;
Cuboid.rotation.z= Math.PI / 2;
scene.add( Cuboid );


//КОНУС2
var radiusTop = 80; var radiusBottom = 180;
var heigth = 140; var segments = 50;
var geometry = new THREE.ConeGeometry(
radiusTop, radiusBottom, heigth, segments );
var material = new THREE.MeshPhongMaterial( { color: 0x66CDAA} );
var Cone = new THREE.Mesh( geometry, material );
Cone.position.set( 100, 0, 0 );
Cone.rotation.x = Math.PI/2;

//ПРИЗМА3
var radiusTop = 64;
var radiusBottom = 64;
var heigth = 180; var segments = 5;
var geometry = new THREE.CylinderGeometry(
radiusTop, radiusBottom, heigth, segments );
var material = new THREE.MeshPhongMaterial( { color: 0xFFFF00 } );
var prism = new THREE.Mesh( geometry, material );
prism.position.set( -200, 0, 0 );
prism.rotation.x = Math.PI/-2;
scene.add( prism );

//ПИРАМИДА4
var radiusTop = 0;
var radiusBottom = 80;
var heigth = 140; var segments = 3;
scene.add( Cone );
var geometry = new THREE.CylinderGeometry(
radiusTop, radiusBottom, heigth, segments );
var material = new THREE.MeshPhongMaterial( { color: 0xFF69B4} );
var piramida = new THREE.Mesh( geometry, material );
piramida.position.set( -500, 0, 0 );
piramida.rotation.x = Math.PI/2;
scene.add( piramida );

// 5пирамида
var radiusTop = 0;
var radiusBottom = 64;
var heigth = 180; var segments = 4;
var geometry = new THREE.CylinderGeometry(
radiusTop, radiusBottom, heigth, segments );
var material = new THREE.MeshPhongMaterial( { color: 0x00CED1} );
var piramida = new THREE.Mesh( geometry, material );
piramida.position.set( 450, -10, -300 );
piramida.rotation.x = Math.PI/2;
scene.add( piramida );


//6 Цилиндр
var radiusTop = 64; var radiusBottom = 64;
var heigth = 140; var segments = 16;
var geometry = new THREE.CylinderGeometry(
radiusTop, radiusBottom, heigth, segments );
var material = new THREE.MeshPhongMaterial( { color: 0xFF1493 } );
var cylinder = new THREE.Mesh( geometry, material );
cylinder.position.set( 130, 0, -300 );
cylinder.rotation.x = Math.PI/-2;
scene.add( cylinder );

//ПРИЗМА7
var radiusTop = 64;
var radiusBottom = 64;
var heigth = 180; var segments = 3;
var geometry = new THREE.CylinderGeometry(
radiusTop, radiusBottom, heigth, segments );
var material = new THREE.MeshPhongMaterial( { color: 0xFF4500 } );
var prism = new THREE.Mesh( geometry, material );
prism.position.set( -200, 0, -300 );
prism.rotation.x = Math.PI/-2;
scene.add( prism );

// ПЯТИУГОЛЬНАЯ ПИРАМИДА8
var radiusTop = 0;
var radiusBottom = 64;
var heigth = 180; var segments = 5;

var geometry = new THREE.CylinderGeometry(
radiusTop, radiusBottom, heigth, segments );

var material = new THREE.MeshPhongMaterial( { color: 0x008000} );
var piramida = new THREE.Mesh( geometry, material );
piramida.position.set( -500, 0, -300 );
piramida.rotation.x = Math.PI/2;
scene.add( piramida );


//КУБ С ТЕКСТУРОЙ
var textureLoader = new THREE.TextureLoader();
var texture = textureLoader.load( 'лиса.png' );
var material = new THREE.MeshBasicMaterial( { map: texture } );
	
					
var geometry = new THREE.BoxGeometry( 175, 175, 175 );
var Cube1 = new THREE.Mesh( geometry, material );
Cube1.position.set( 0, 0, 300 );
Cube1.rotation.x = Math.PI ;
scene.add( Cube1 );				
					
var texture = textureLoader.load( 'лиса.png' );
texture.wrapS = texture.wrapT = THREE.RepeatWrapping;
texture.repeat.set( 1, 1 );
var material = new THREE.MeshBasicMaterial( { 
map: texture, side: THREE.DoubleSide } );
var geometry = new THREE.PlaneGeometry( 220, 220, 10, 10 );	
var Plane = new THREE.Mesh( geometry, material );
Plane.position.set( 0, 0, 215 );
Plane.rotation.x = Math.PI ;
scene.add( Plane );


}

// EVENT HANDLERS


function onWindowResize() {

camera.aspect = window.innerWidth / window.innerHeight;
camera.updateProjectionMatrix();

renderer.setSize( window.innerWidth, window.innerHeight );

}

//

function animate() {

requestAnimationFrame( animate );
controls.update(); //
render();

}

function render() {

renderer.render( scene, camera );

}


</script>

</body>
</html>
											
											
											
											
