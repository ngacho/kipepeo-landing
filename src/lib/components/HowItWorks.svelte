<script lang="ts">
  import { Card, CardContent, CardHeader, CardTitle } from "$lib/components/ui/card";
  import { Badge } from "$lib/components/ui/badge";

  interface HowItWorksProps {
    badgeTitle: string;
    title: string;
    description: string;
    image: string;
  }

  const HowItWorksList: HowItWorksProps[] = [
  {
    badgeTitle: "Contribute",
    title: "Fund Futures Through Education",
    description:
      "Your support helps us cover tuition, living expenses, and school supplies for vulnerable children—especially girls—so they can stay in school and thrive.",
    image: "roboto.png",
  },
  {
    badgeTitle: "Discover",
    title: "See the Impact in Real Lives",
    description:
      "Follow the stories of women and children whose lives have been transformed through access to healthcare, education, and sustainable livelihoods.",
    image: "runner.png",
  },
  {
    badgeTitle: "Innovate",
    title: "Support Women-Led Solutions",
    description:
      "We invest in innovative, community-led projects—especially those led by women—that create lasting economic opportunities and dignity.",
    image: "pacheco.png",
  },
  {
    badgeTitle: "Collaborate",
    title: "Empower Communities Together",
    description:
      "Join hands with us, local leaders, and global supporters to create inclusive programs that break cycles of poverty and unlock potential.",
    image: "gamestation.png",
  },
];

</script>

<section id="process" class="container py-24 sm:py-32">
  <div class="text-center mb-8">
    <h2 class="text-lg text-primary text-center mb-2 tracking-wider">
      How It Works
    </h2>

    <h2 class="text-3xl md:text-4xl text-center font-bold">
      Step-by-Step Process
    </h2>
  </div>

  <div class="w-[90%] md:w-[70%] lg:w-[75%] lg:max-w-screen-xl top-5 mx-auto relative">
    {#each HowItWorksList as { badgeTitle, title, description, image }, index}
      <div class="flex mb-8 items-center" class:flex-row-reverse={index % 2 !== 0}>
        <Card class="h-full bg-transparent border-0 shadow-none">
          <CardHeader>
            <div class="pb-4">
              <Badge>{badgeTitle}</Badge>
            </div>

            <CardTitle>
              {title}
            </CardTitle>
          </CardHeader>

          <CardContent class="text-muted-foreground w-[80%]">
            {description}
          </CardContent>
        </Card>

        <img
          src={image}
          alt="Image describing {title}"
          class="w-[150px] md:w-[250px] lg:w-[300px] mx-auto -scale-x-100"
        />
        
        <div
          class="-z-10 absolute right-0 w-44 h-72 lg:w-64 lg:h-80 rounded-full bg-primary/15 dark:bg-primary/10 blur-3xl"
          class:left-0={index % 2 !== 0}
        ></div>
      </div>
    {/each}
  </div>
</section>
