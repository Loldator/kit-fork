<script>
	import { beforeNavigate } from '$app/navigation';

	let times_triggered = 0;
	let unload = false;
	let navigation_type;
	beforeNavigate(({ cancel, type, willUnload, to }) => {
		times_triggered++;
		unload = willUnload;
		navigation_type = type;
		if (!to?.route.id?.includes('redirect')) {
			cancel();
		}
	});
</script>

<h1>prevent navigation</h1>
<a href="/before-navigate/a">a</a>
<a href="/before-navigate/redirect">redirect</a>
<a href="https://google.de">external</a>
<pre>{times_triggered} {unload} {navigation_type}</pre>
