# threejs-raycast-test

Debugging raycasting in THREE.js 2020 vs 2016 versions

- Run `sphere-demo/index2016.html` to see intended behavior, loading the three.js library from 2016.
- Run `sphere-demo/index2020.html` to see the same application running with the 2020 versions of the three.js library and utilities.

The source code of these files is identical other than the libraries loaded in the `<head>`.

The sphere should turn green while you are clicking on it, and red otherwise. It accomplishes this by using the THREE.Raycaster `intersectsObjects` method to determine an intersection between the (x,y) mouse coordinate and any children of the scene.

There appears to be a bug in the 2020 version.

---
*EDIT*: **SOLUTION**: When manually setting the projection matrix, three.js now requires that the projectMatrixInverse also be manually updated. In index2020.html, add the line `camera.projectionMatrixInverse.getInverse(camera.projectionMatrix);` after the line `setMatrixFromArray(camera.projectionMatrix, projectionMatrix);`
