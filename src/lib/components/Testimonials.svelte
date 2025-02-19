<script lang="ts">
  import { Avatar, AvatarFallback, AvatarImage } from "$lib/components/ui/avatar";
  import {
    Card,
    CardContent,
    CardDescription,
    CardHeader,
    CardTitle,
  } from "$lib/components/ui/card";
  import * as Carousel from "$lib/components/ui/carousel";
  import { Star } from "lucide-svelte";
  import type { CarouselAPI } from "$lib/components/ui/carousel/context";
  import Autoplay from "embla-carousel-autoplay";

  interface ReviewProps {
    image: string;
    name: string;
    userName: string;
    comment: string;
    rating: number;
  }

  const reviewList: ReviewProps[] = [
    {
    image: "https://github.com/shadcn.png",
    name: "John Doe",
    userName: "Product Manager",
    comment:
      "Wow Vue + Shadcn-Vue is awesome!. This template lets me change colors, fonts and images to match my brand identity. ",
    rating: 5.0,
  },
  {
    image: "https://github.com/shadcn.png",
    name: "Sophia Collins",
    userName: "Cybersecurity Analyst",
    comment:
      "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna. ",
    rating: 4.8,
  },

  {
    image: "https://github.com/shadcn.png",
    name: "Adam Johnson",
    userName: "Chief Technology Officer",
    comment:
      "Lorem ipsum dolor sit amet,exercitation. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.",
    rating: 4.9,
  },
  {
    image: "https://github.com/shadcn.png",
    name: "Ethan Parker",
    userName: "Data Scientist",
    comment:
      "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod labore et dolore magna aliqua. Ut enim ad minim veniam.",
    rating: 5.0,
  },
  {
    image: "https://github.com/shadcn.png",
    name: "Ava Mitchell",
    userName: "IT Project Manager",
    comment:
      "Lorem ipsum dolor sit amet, tempor incididunt  aliqua. Ut enim ad minim veniam, quis nostrud incididunt consectetur adipiscing elit.",
    rating: 5.0,
  },
  {
    image: "https://github.com/shadcn.png",
    name: "Isabella Reed",
    userName: "DevOps Engineer",
    comment:
      "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
    rating: 4.9,
  },
  ];

  let api = $state<CarouselAPI>();
  const plugin = Autoplay({ delay: 4000, stopOnInteraction: true });
</script>

<section id="testimonials" class="container py-24 sm:py-32">
  <div class="text-center mb-8">
    <h2 class="text-lg text-primary text-center mb-2 tracking-wider">
      Testimonials
    </h2>

    <h2 class="text-3xl md:text-4xl text-center font-bold mb-4">
      Hear What Our 1000+ Clients Say
    </h2>
  </div>

  <Carousel.Root
    opts={{
      align: "start",
      loop: true,
    }}
    plugins={[plugin]}
    class="relative w-[80%] sm:w-[90%] lg:max-w-screen-xl mx-auto"
    setApi={(emblaApi) => (api = emblaApi)}
    onmouseenter={plugin.stop}
    onmouseleave={plugin.reset}
  >
    <Carousel.Content class="-ml-4">
      {#each reviewList as review (review.name)}
        <Carousel.Item class="pl-4 md:basis-1/2 lg:basis-1/3">
          <Card class="bg-muted/50 dark:bg-card h-full">
            <CardContent class="p-6 h-full flex flex-col">
              <div class="flex-1">
                <div class="flex gap-1 mb-6">
                  {#each Array(5) as _}
                    <Star class="size-4 fill-primary text-primary" />
                  {/each}
                </div>

                <p class="mb-6">"{review.comment}"</p>
              </div>

              <div class="flex items-center gap-4 pt-6 border-t">
                <Avatar>
                  <AvatarImage
                    src={review.image}
                    alt={`Avatar of ${review.name}`}
                  />
                  <AvatarFallback>
                    {review.name.split(' ').map(n => n[0]).join('')}
                  </AvatarFallback>
                </Avatar>

                <div class="flex flex-col">
                  <CardTitle class="text-lg">{review.name}</CardTitle>
                  <CardDescription>{review.userName}</CardDescription>
                </div>
              </div>
            </CardContent>
          </Card>
        </Carousel.Item>
      {/each}
    </Carousel.Content>
    <Carousel.Previous />
    <Carousel.Next />
  </Carousel.Root>
</section>
