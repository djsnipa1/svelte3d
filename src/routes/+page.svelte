<script>
	import * as Threlte from '@threlte/core';
	import * as Three from 'three';
	import * as MathUtils from 'three/src/math/MathUtils';
</script>

<Threlte.Canvas>
	<Threlte.PerspectiveCamera position={{ x: 20, y: 20, z: 20 }} fov={50}>
		<Threlte.OrbitControls autoRotate />
	</Threlte.PerspectiveCamera>

	<Threlte.AmbientLight color="white" intensity={0.2} />

	<Threlte.DirectionalLight color="0xffffff" intensity={2} position={{ x: 10, y: 20 }} />

	<Threlte.Mesh
		geometry={new Three.SphereGeometry(4, 64, 64)}
		material={new Three.MeshStandardMaterial({ color: '#fff' })}
	/>

	<Threlte.Mesh
		geometry={new Three.PlaneGeometry(20, 20)}
		material={new Three.MeshStandardMaterial({ color: '0xff00ff' })}
	/>
</Threlte.Canvas>
