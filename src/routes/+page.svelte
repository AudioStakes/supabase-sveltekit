<script>
  import { user } from '../../lib/sessionStore'
  import { supabase } from '../../lib/supabaseClient'
  import Auth from '../../lib/Auth.svelte'
  import Profile from '../../lib/Profile.svelte'

  user.set(supabase.auth.user())

  supabase.auth.onAuthStateChange((_, session) => {
    user.set(session.user)
  })
</script>

<div class="container pt-[50px] pb-[100px]">
  {#if $user}
  <Profile />
  {:else}
  <Auth />
  {/if}
</div>
