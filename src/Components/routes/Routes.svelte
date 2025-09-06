<script>
    import Router from "svelte-spa-router";
    import User from "../User.svelte";
    import About from "../About.svelte";
    import Files from "../Files.svelte";
    import Cards from "../Cards.svelte";
    import Testimonials from "../Testimonials.svelte";

    const routes = {
    '/about': About,
    '/user': User,
    '/files': Files,
    '/cards': Cards,
    '/testimonials': Testimonials,
  };

</script>

<Router {routes} />