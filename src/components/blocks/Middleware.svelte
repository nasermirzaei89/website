<script>
  import CodeBlock from '../CodeBlock.svelte';

  const exampleCode = `package main

import (
  "github.com/gofiber/fiber"
  "github.com/gofiber/cors"
)

func main() {
  app := fiber.New()

  app.Use(cors.New())
  app.Use(func (c *fiber.Ctx) {
    if !c.Is("json") {
      c.Send("Sorry, only JSON requests are allowed!")
      return
    }

    c.Next()
  })

  app.Get("/", func(c *fiber.Ctx) {
    c.JSON(&fiber.Map{
      "message": "Hello World",
    })
  })

  app.Listen(3000)
}`;
</script>

<section class="generic-block reverse">
  <div class="mid">
    <div class="right">
      <h3>Flexible Middleware Support</h3>
      <p>
        Choose from <a href="https://docs.gofiber.io/middleware" target="_blank">a
        number of already existing middleware</a> or create your own! Use them
        to verify and manipulate certain requests in your app before they reach
        your controller.
      </p>
    </div>
    <div class="left">
      <CodeBlock>
        {exampleCode}
      </CodeBlock>
    </div>
  </div>
</section>
