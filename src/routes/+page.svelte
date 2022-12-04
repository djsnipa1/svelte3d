<script>
	import { browser } from '$app/environment';
	import { Pane } from 'tweakpane';

	import * as Threlte from '@threlte/core';
	import * as Three from 'three';
	import * as Utils from 'three/src/math/MathUtils';
	import { object_without_properties } from 'svelte/internal';

	const gridHelper = new Three.GridHelper(20, 20);
	const axesHelper = new Three.AxesHelper(10);

	const sphere = {
		position: { x: 0, y: 4, z: 0 }
	};

	if (browser) {
		const pane = new Pane({ title: 'Scene' });

		const sphereControls = pane.addFolder({ title: 'sphere' });
		sphereControls.addInput(sphere, 'position');
		sphereControls.on('change', ({ value }) => {
			// @ts-ignore
			sphere.position = value;
		});
	}
</script>

<Threlte.Canvas>
	<Threlte.Object3DInstance object={gridHelper} />
	<Threlte.Object3DInstance object={axesHelper} />

	<Threlte.PerspectiveCamera position={{ x: 20, y: 20, z: 20 }} fov={50}>
		<Threlte.OrbitControls autoRotate />
	</Threlte.PerspectiveCamera>

	<Threlte.AmbientLight color="white" intensity={0.2} />

	<Threlte.DirectionalLight
		color="0xffffff"
		intensity={2}
		position={{ x: 10, y: 20 }}
		shadow={{
			camera: { top: 8 }
		}}
	/>

	<Threlte.Mesh
		geometry={new Three.SphereGeometry(4, 64, 64)}
		material={new Three.MeshStandardMaterial({ color: '#fff' })}
		position={sphere.position}
		receiveShadow
		castShadow
	/>

	<Threlte.Mesh
		geometry={new Three.PlaneGeometry(20, 20)}
		material={new Three.MeshStandardMaterial({
			color: '0xffffff',
			side: Three.DoubleSide
		})}
		rotation={{ x: Utils.DEG2RAD * 90 }}
		receiveShadow
	/>
</Threlte.Canvas>
