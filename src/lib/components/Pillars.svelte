<script lang="ts">
  import { Card, CardContent, CardHeader, CardTitle } from "$lib/components/ui/card";
  import {
    Sparkle,
    Tag,
    Paintbrush,
    Blocks,
    LineChart,
    Wallet,
    HeartPulse,
    Microscope,
  } from "lucide-svelte";

  interface BenefitsProps {
    icon: 'heart-pulse' | 'education' | 'paintbrush' | 'blocks' | 'lineChart' | 'wallet';
    title: string;
    description: string;
  }

  const benefitList: BenefitsProps[] = [
    {
      icon: "heart-pulse",
      title: "Health",
      description:
        "We believe that healthy individuals form the backbone of thriving communities. Our health initiatives focus on providing access to essential medical services and health education, especially for women and children in underserved areas. By prioritizing maternal and child health, mental wellness, and preventative care, we aim to create resilient families and break the cycle of generational poverty.",
    },
    {
      icon: "education",
      title: "Education",
      description:
        "Education is at the heart of what we do. We are committed to ensuring that vulnerable children, have the opportunity to reach their academic potential. Kipepeo Foundation covers both tuition and living expenses, removing financial barriers that often prevent promising students from continuing their studies. Our support goes beyond the classroom—we provide mentorship, school supplies, and a nurturing environment that fosters both academic and personal growth.",
    },
    {
      icon: "wallet",
      title: "Integrated Livelihoods",
      description:
        "Economic independence is a powerful tool for transformation. We work closely with women in marginalized communities to build sustainable income-generating skills and connect them to opportunities. Through vocational training, financial literacy programs, and support for small-scale businesses, we help women gain control over their economic futures.",
    }
  ];

  const iconMap = {
    "heart-pulse": HeartPulse,
    "education" : Microscope,
    tag: Tag,
    paintbrush: Paintbrush,
    blocks: Blocks,
    lineChart: LineChart,
    wallet: Wallet,
  };
</script>

<section id="pillars" class="container py-24 sm:py-32 text-center">
  <div class="w-[90%] md:w-[70%] lg:w-[75%] lg:max-w-screen-xl top-5 mx-auto">
    <div class="max-w-3xl mx-auto mb-16">
      <h2 class="text-3xl md:text-4xl font-bold mb-4">
        Our Pillars
      </h2>
    </div>
  
    <!-- Horizontal Grid for Cards -->
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
      {#each benefitList as { icon, title, description }, index}
        <Card class="bg-muted/50 dark:bg-card hover:bg-background dark:hover:bg-background transition-all delay-75 group/number">
          <CardHeader>
            <div class="flex justify-between">
              <svelte:component 
                this={iconMap[icon]} 
                class="size-8 mb-6 text-primary"
              />
              <span class="text-5xl text-muted-foreground/15 font-medium transition-all delay-75 group-hover/number:text-muted-foreground/30">
                0{index + 1}
              </span>
            </div>
            <CardTitle>{title}</CardTitle>
          </CardHeader>
  
          <CardContent class="text-muted-foreground">
            {description}
          </CardContent>
        </Card>
      {/each}
    </div>

  </div>
  
  
</section>
