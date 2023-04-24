import * as THREE from '../three/three.module.js';

// Our Javascript will go here.

const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 0.1, 1000 );

const renderer = new THREE.WebGLRenderer();
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild( renderer.domElement );

var loader = new THREE.TextureLoader();
 const boxgeometry = new THREE.BoxGeometry(1, 1, 1 );
const boxmaterials = [
 new THREE.MeshBasicMaterial ( { map: loader.load('cube1.png') } ),
 new THREE.MeshBasicMaterial ( { map: loader.load('cube2.png') } ),
 new THREE.MeshBasicMaterial ( { map: loader.load('cube3.png') } ),
 new THREE.MeshBasicMaterial ( { map: loader.load('cube4.png') } ),
 new THREE.MeshBasicMaterial ( { map: loader.load('cube5.png') } ),
 new THREE.MeshBasicMaterial ( { map: loader.load('cube6.png') } ),
 
];

const cube = new THREE.Mesh( boxgeometry, boxmaterials );
scene.add( cube );

 const cylgeometry = new THREE.CylinderGeometry(5, 5, 20, 32 );
const cylmaterial = new THREE.MeshLambertMaterial ( { color: 0xffff00 } );
const cylinder = new THREE.Mesh( cylgeometry, cylmaterial );
scene.add( cylinder );
cylinder.position.z=-25;
cylinder.position.x=5;


var lightOne= new THREE.AmbientLight(0xffffff, 0.5);
scene.add (lightOne);

var lightTwo= new THREE.PointLight(0xffffff, 0.5);
scene.add (lightTwo);

lightTwo.position.set(25, 0, -25)

//напівсферичне освітлення
var lightThree = new THREE.HemisphereLight(0xfffff, 0x080820, 1);
scene.add(lightThree);

camera.position.z= 7;
camera.position.x= 2;

renderer.setClearColor (0x555555);
renderer.clear( );

let angle = 0, radius = 47;
function animate () {
requestAnimationFrame ( animate );
renderer.render( scene, camera );
lightTwo.position.x = radiys * Math.cos(angle) +5;
lightTwo.position.y = radiys * Math.cos(angle);
cube.rotation.x +=0.01;
cube.rotation.y +=0.01;


angle += Math.PI/180;
animate( );