<script lang="ts">
  import {
    Card,
    CardContent,
    CardHeader,
    CardTitle,
    CardFooter,
  } from "$lib/components/ui/card";

  import LinkedInIcon from "$lib/icons/LinkedInIcon.svelte";
  import GithubIcon from "$lib/icons/GithubIcon.svelte";
  import XIcon from "$lib/icons/XIcon.svelte";

  interface TeamProps {
    imageUrl: string;
    firstName: string;
    lastName: string;
    positions: string[];
    socialNetworks: SocialNetworkProps[];
  }

  interface SocialNetworkProps {
    name: 'LinkedIn' | 'Github' | 'X';
    url: string;
  }

  const teamList: TeamProps[] = [
    {
    imageUrl: "https://i.pravatar.cc/250?img=58",
    firstName: "Sallyann",
    lastName: "Pendo",
    positions: ["Executive Trustee"],
    socialNetworks: [
      {
        name: "LinkedIn",
        url: "https://www.linkedin.com/in/leopoldo-miranda/",
      },
      {
        name: "Github",
        url: "https://github.com/leoMirandaa",
      },
      {
        name: "X",
        url: "https://x.com/leo_mirand4",
      },
    ],
  },
  {
    imageUrl:
      "https://images.unsplash.com/photo-1534528741775-53994a69daeb?q=80&w=1528&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
    firstName: "Esther",
    lastName: "Loice",
    positions: ["Executive Trustee"],
    socialNetworks: [
      {
        name: "LinkedIn",
        url: "https://www.linkedin.com/in/leopoldo-miranda/",
      },
      {
        name: "X",
        url: "https://x.com/leo_mirand4",
      },
    ],
  },
  {
    imageUrl:
      "https://images.unsplash.com/photo-1527980965255-d3b416303d12?q=80&w=1760&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
    firstName: "Brandon",
    lastName: "Ngacho",
    positions: ["Executive Trustee"],
    socialNetworks: [
      {
        name: "LinkedIn",
        url: "https://www.linkedin.com/in/leopoldo-miranda/",
      },
      {
        name: "Github",
        url: "https://github.com/leoMirandaa",
      },
    ],
  }
  ];

  const socialIconMap = {
    LinkedIn: LinkedInIcon,
    Github: GithubIcon,
    X: XIcon,
  };
</script>

<section id="team" class="container max-w-7xl mx-auto px-4 py-16 sm:py-24 lg:py-32">
  <div class="text-center mb-12">
    <h2 class="text-lg text-primary text-center mb-3 tracking-wider">Team</h2>

    <h2 class="text-3xl md:text-4xl text-center font-bold">
      Governance
    </h2>
  </div>

  <div class="w-[90%] md:w-[70%] lg:w-[75%] lg:max-w-screen-xl top-5 mx-auto grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-6 md:gap-8 justify-center items-start">

    {#each teamList as { imageUrl, firstName, lastName, positions, socialNetworks }}
      <Card class="bg-muted/60 dark:bg-card flex flex-col h-full overflow-hidden group/hoverimg">
        <CardHeader class="p-0 gap-0">
          <div class="h-full overflow-hidden">
            <img
              src={imageUrl}
              alt={`${firstName} ${lastName}`}
              class="w-full aspect-square object-cover saturate-0 transition-all duration-300 ease-in-out group-hover/hoverimg:saturate-100 group-hover/hoverimg:scale-105"
            />
          </div>
          <CardTitle class="p-4 sm:p-6">
            {firstName}
            <span class="text-primary">{lastName}</span>
          </CardTitle>
        </CardHeader>

        <div class="px-4 sm:px-6 flex-grow">
          {#each positions as position, index}
            <CardContent class="p-0 pb-2 text-muted-foreground">
              {position}{#if index < positions.length - 1},{/if}
            </CardContent>
          {/each}
        </div>

        <CardFooter class="space-x-4 px-4 sm:px-6 py-4">
          {#each socialNetworks as { name, url }}
            <a
              href={url}
              target="_blank"
              class="hover:opacity-80 transition-opacity"
              aria-label="Visit our {name} page"
            >
              <svelte:component this={socialIconMap[name]} />
            </a>
          {/each}
        </CardFooter>
      </Card>
    {/each}
  </div>
</section>
