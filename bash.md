# bash: Bourne Again SHell

## Resources

- [awesome-shell](https://github.com/alebcay/awesome-shell)
- [bash-guide](https://github.com/Idnan/bash-guide)
- [Bash reference manual](https://www.gnu.org/savannah-checkouts/gnu/bash/manual/bash.html#Introduction)
- [Learn Enough Command Line to Be Dangerous](https://www.learnenough.com/command-line-tutorial/basics)
- [Learn Shell](https://www.learnshell.org/)
- [Learn X in Y minutes](https://learnxinyminutes.com/docs/bash/)
- [the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line)

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
