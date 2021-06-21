<p>please help me</p>

<script>
import { onMount } from 'svelte'
import { dev } from '$app/env'

let url = dev ? 'http://localhost:3000' : 'https://pleasehelpme.games'

onMount(() => {
  window.addEventListener("message", (event) => {
    // Do we trust the sender of this message?
    if (event.origin !== url)
      return;

    console.log({ event })

    // Assuming you've verified the origin of the received message (which
    // you must do in any case), a convenient idiom for replying to a
    // message is to call postMessage on event.source and provide
    // event.origin as the targetOrigin.
    event.source.postMessage('neato',
                             event.origin);
  }, false);
})
</script>
