# bash: Bourne Again SHell

## cURL(client URL)

### Format JSON response from curl
[Pretty Print JSON responses from curl](https://til.hashrocket.com/posts/pgyjvtuwba-pretty-print-json-responses-from-curl)
- When you use `curl` to manually make API calls, sometimes the response is not formatted
- You can pipe `json_pp` at the end so you have a prettier json response
```bash
$ curl 'https://til.hashrocket.com/api/developer_posts.json?username=gabrielreis' | json_pp

{
   "data" : {
      "posts" : [
         {
            "slug" : "mmzlajavna",
            "title" : "Display line break content in React with just CSS"
         },
         {
            "title" : "Mutations with the graphql-client Ruby gem",
            "slug" : "xej7xtsnit"
         },
         {
            "title" : "The rest of keyword arguments 🍕",
            "slug" : "o2wiclcyjf"
         }
      ]
   }
}
```
