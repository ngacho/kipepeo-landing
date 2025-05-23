<script lang="ts">
  import { Button } from "$lib/components/ui/button";
  import { Card, CardHeader, CardContent, CardFooter } from "$lib/components/ui/card";
  import { Label } from "$lib/components/ui/label";
  import { Input } from "$lib/components/ui/input";
  import { Textarea } from "$lib/components/ui/textarea";
  import { Alert, AlertDescription, AlertTitle } from "$lib/components/ui/alert";
  import { AlertCircle, Building2, Phone, Mail, Clock } from "lucide-svelte";
  import * as Select from "$lib/components/ui/select/index.js";

  interface ContactFormProps {
    firstName: string;
    lastName: string;
    email: string;
    subject: string;
    message: string;
  }

  let contactForm: ContactFormProps = {
    firstName: "",
    lastName: "",
    email: "",
    subject: "Web Development",
    message: "",
  };

  let invalidInputForm = false;

  function handleSubmit(event: SubmitEvent) {
    event.preventDefault();
    const { firstName, lastName, email, subject, message } = contactForm;
    console.log(contactForm);

    const mailToLink = `mailto:brandonngacho@gmail.com?subject=${subject}&body=Hello I am ${firstName} ${lastName}, my Email is ${email}. %0D%0A${message}`;
    window.location.href = mailToLink;
  }

  const subjects = [
    { value: "Web Development", label: "Web Development" },
    { value: "Mobile Development", label: "Mobile Development" },
    { value: "Figma Design", label: "Figma Design" },
    { value: "REST API", label: "REST API" },
    { value: "FullStack Project", label: "FullStack Project" }
  ];

  $: triggerContent = subjects.find(s => s.value === contactForm.subject)?.label ?? "Select a subject";
</script>

<section id="contact" class="container py-24 sm:py-32">
  <div class="text-center mb-12">
    <h2 class="text-lg text-primary tracking-wider uppercase">Contact</h2>
    <h2 class="text-3xl md:text-4xl font-bold">Connect With Us</h2>
    <p class="mt-4 text-muted-foreground max-w-xl mx-auto">
      Have a question or want to get involved? Fill out the form below and we’ll get back to you shortly.
    </p>
  </div>

  <div class="max-w-3xl mx-auto">
    <Card class="bg-muted/60 dark:bg-card">
      <CardHeader class="text-primary text-2xl" />
      <CardContent>
        <form on:submit={handleSubmit} class="grid gap-4">
          <div class="flex flex-col md:flex-row gap-8">
            <div class="flex flex-col w-full gap-1.5">
              <Label for="firstName">First Name</Label>
              <Input
                id="firstName"
                type="text"
                placeholder="Jane"
                bind:value={contactForm.firstName}
              />
            </div>

            <div class="flex flex-col w-full gap-1.5">
              <Label for="lastName">Last Name</Label>
              <Input
                id="lastName"
                type="text"
                placeholder="Doe"
                bind:value={contactForm.lastName}
              />
            </div>
          </div>

          <div class="flex flex-col gap-1.5">
            <Label for="contactEmail">Email</Label>
            <Input
              id="contactEmail"
              type="email"
              placeholder="you@example.com"
              bind:value={contactForm.email}
            />
          </div>

          <div class="flex flex-col gap-1.5">
            <Label for="contactSubject">Subject</Label>
            <Select.Root type="single" bind:value={contactForm.subject}>
              <Select.Trigger id="contactSubject" class="w-full">
                {triggerContent}
              </Select.Trigger>
              <Select.Content>
                <Select.Group>
                  {#each subjects as subject}
                    <Select.Item value={subject.value} label={subject.label}>
                      {subject.label}
                    </Select.Item>
                  {/each}
                </Select.Group>
              </Select.Content>
            </Select.Root>
          </div>

          <div class="flex flex-col gap-1.5">
            <Label for="contactMessage">Message</Label>
            <Textarea
              id="contactMessage"
              placeholder="Your message..."
              rows={5}
              bind:value={contactForm.message}
            />
          </div>

          {#if invalidInputForm}
            <Alert variant="destructive">
              <AlertCircle class="w-4 h-4" />
              <AlertTitle>Error</AlertTitle>
              <AlertDescription>
                There is an error in the form. Please check your input.
              </AlertDescription>
            </Alert>
          {/if}

          <Button class="mt-4">Send message</Button>
        </form>
      </CardContent>
    </Card>
  </div>
</section>
