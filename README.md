

* Copy from Three.js examples Ejemplos_basicos_three/Array_boxes/

* Extract from Skybox project (Ejemplos_basicos_three/Skybox/) and add:

  * Copy the pngs files (textures)
  * Add the cube load of skybox and add it to scene

  ```
  var urls = ["nievepx.jpg", "nievenx.jpg", "nievepy.jpg", "nieveny.jpg", "nievepz.jpg", "nievenz.jpg"];
  var textureCube = THREE.ImageUtils.loadTextureCube( urls );
  var shader = THREE.ShaderLib[ "cube" ];
  shader.uniforms[ "tCube" ].value = textureCube;

  var material = new THREE.ShaderMaterial( {
    fragmentShader: shader.fragmentShader,
    vertexShader: shader.vertexShader,
    uniforms: shader.uniforms,
    depthWrite: false,
    side: THREE.BackSide
  });

   skycube = new THREE.Mesh( new THREE.BoxGeometry( 1500, 1500, 1500 ), material );
   scene.add( skycube );
```

  * Choose texture from Humus page: http://www.humus.name/index.php?page=Textures, download the images and use them into the project.

  * Modify the creation of boxes to different sizes using randomise:

  ```
  // rand min-max
  var rand = (min.max) => Math.floor(Math.random() * (max - min + 1)) + min

  function createBuildings(height){
      var geometry = new THREE.BoxGeometry( 40, height, 40 );
      var material = new THREE.MeshLambertMaterial( {color: controls.colormesh} );
	  var mesh = new THREE.Mesh(geometry, material);
      mesh.position.y = height / 2; // Adjust to coordinates system
      return mesh;
  }

  var buildings = [createBuilding(40),createBuilding(80),createBuilding(140)];

  for (var i = -4; i < 5; i++){
    for (var j = -4; j < 5; j++) {
        var mesh = buildings(rand(0,buildings.length)        
        mesh.position.set(j*80, mesh.position.y, i*80);
        scene.add(mesh);
    }
  }
  ```




# vcity
Procedural city #three.js #3d 
