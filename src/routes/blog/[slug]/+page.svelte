<script>
  // Mock post data (in a real app, load this via SvelteKit's load function)
  const post = {
    title: "My First SvelteKit Blog Post",
    date: "2025-05-24",
    author: {
      name: "Jane Doe",
      avatar: "/path/to/avatar.jpg",
      title: "Full-Stack Developer"
    },
    heroImage: "/favicon.png"
  };
  // Format the date for display (e.g., "May 24, 2025")
  const formattedDate = new Date(post.date).toLocaleDateString(undefined, {
    year: 'numeric', month: 'long', day: 'numeric'
  });
</script>

<article class="max-w-3xl mx-auto px-4 sm:px-6 lg:px-8">
  <!-- Article Header: Title and Byline -->
  <header class="mb-6">
    <h1 class="text-3xl sm:text-4xl font-bold mb-2">{post.title}</h1>
    <p class="text-sm text-gray-600">
      By {post.author.name} <span class="mx-1">·</span> <time>{formattedDate}</time>
    </p>
  </header>

  <!-- Main Content and Author Aside Container -->
  <div class="md:flex md:flex-row-reverse md:items-start gap-8">
    <!-- Author Sidebar (Aside) -->
    <aside class="md:w-1/4 md:flex-shrink-0">
      <div class="flex flex-col items-center md:items-start bg-gray-50 border border-gray-200 p-4 rounded-lg gap-2">
        <img src="{post.author.avatar}" alt="{post.author.name}'s avatar"
             class="w-20 h-20 md:w-24 md:h-24 rounded-full">
        <p class="text-lg font-semibold">{post.author.name}</p>
        <p class="text-sm text-gray-600">{post.author.title}</p>
      </div>
    </aside>

    <!-- Article Content Section -->
    <section class="md:flex-1 text-gray-800 leading-relaxed">
      <!-- Featured Hero Image -->
      <img src="{post.heroImage}" alt="Featured image for the post"
           class="w-full h-auto rounded-lg mb-6" />
      <!-- Example Paragraphs and Rich Text -->
      <p class="mb-4">
        This is the opening paragraph of the blog post content. It introduces the topic and provides some context to engage the reader.
      </p>
      <h2 class="text-2xl font-semibold mb-4">Subheading Example</h2>
      <p class="mb-4">
        Another paragraph follows the subheading, containing some inline <strong>bold text</strong> and even an inline image 
        <img src="/path/to/inline-image.jpg" alt="Inline demo" 
             class="w-32 h-auto inline-block rounded mx-2" /> 
        to illustrate how images can appear within text.
      </p>
      <blockquote class="border-l-4 border-gray-300 pl-4 italic text-gray-700 mb-4">
        “This is a blockquote example, used to highlight an important excerpt or quote from the article.”
      </blockquote>
      <ul class="list-disc pl-5 mb-4">
        <li>First list item to illustrate a bullet list in the post.</li>
        <li>Second list item with additional details for readers.</li>
        <li>Third list item as part of the example list.</li>
      </ul>
      <p class="mb-4">
        You can also include links in your content, for example a 
        <a href="#" class="text-blue-600 underline hover:text-blue-800">relevant resource link</a> 
        to supplement the article.
      </p>
      <p class="mb-4">
        Finally, this is a concluding paragraph to wrap up the post. It summarizes the key points and might invite the reader to comment or share.
      </p>
    </section>
  </div>
</article>
