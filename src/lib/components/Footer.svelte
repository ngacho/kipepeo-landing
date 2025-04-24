<script lang="ts">
  import { ChevronsDown } from "lucide-svelte";
  import { Separator } from "$lib/components/ui/separator";
  import { onMount } from 'svelte';
  import { mode } from "mode-watcher";
    let imageSrc = 'kipepeo-logo-light.png';
    
    onMount(() => {
        mode.subscribe(currentMode => {
            imageSrc = currentMode === 'dark' ? 'kipepeo-logo-light.png' : 'kipepeo-logo-dark.png';
        });
    });
</script>

<footer id="footer" class="py-24 pb-16 sm:py-32 sm:pb-24">
  <div class="w-[90%] md:w-[70%] lg:w-[75%] lg:max-w-screen-xl mx-auto p-10 bg-muted/50 dark:bg-card border rounded-2xl">
    <div class="grid grid-cols-2 md:grid-cols-3 xl:grid-cols-4 gap-x-12 gap-y-8">
      <!-- Logo and Description -->
      <div class="col-span-full xl:col-span-2 space-y-4">
        <a href="/" class="flex font-bold items-center">
          <img
            class="w-8 h-8 mr-4 rounded-lg"
            src={imageSrc}
            alt="kipepeo logo"
          />
          <h3 class="text-2xl">Kipepeo Foundation</h3>
        </a>
        <p class="text-sm text-muted-foreground">
          We are a nonprofit fighting poverty, disease, and inequity around the world through education, health, and integrated livelihood programmes.
        </p>
      </div>

      <!-- Contact Information -->
      <div class="flex flex-col gap-2">
        <h3 class="font-bold text-lg">Contact Us</h3>
        <div class="text-sm text-muted-foreground">
          Kipepeo Foundation Headquarters<br />
          <a href="mailto:hello@kipepeo.org" class="opacity-60 hover:opacity-100">hello@kipepeo.org</a><br />
          +254 700 000 000
        </div>
      </div>

      <!-- About Us Links -->
      <div class="flex flex-col gap-2">
        <h3 class="font-bold text-lg">About Us</h3>
        <div><a href="/our-partners" class="opacity-60 hover:opacity-100">Partners</a></div>
        <div><a href="/media" class="opacity-60 hover:opacity-100">Media</a></div>
        <div><a href="/talk-to-us" class="opacity-60 hover:opacity-100">Talk To Us</a></div>
      </div>
    </div>
    
    <Separator class="my-6" />
    
    <section>
      <div class="flex flex-col md:flex-row justify-between items-center gap-4">
        <p>
          &copy; {new Date().getFullYear()} Kipepeo Foundation. All rights reserved.
        </p>
        <ul class="flex gap-4">
          <li><a href="/terms-conditions" class="hover:underline">Terms &amp; Conditions</a></li>
          <li><a href="/privacy-policy" class="hover:underline">Privacy Policy</a></li>
          <li><a href="/talk-to-us" class="hover:underline">Contact Us</a></li>
        </ul>
      </div>
    </section>
  </div>
</footer>