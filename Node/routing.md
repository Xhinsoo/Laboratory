
1: Routing refers to taking incoming request and a path that is requested and matching that to a code in some response. Path could be /dog, /help anything.

2: Get request: use them to retrieve info. Websites can only send get requests

When client submit get request if we have data that is being sent alongside(it is included in the query string). This allows us to see data in url, with query string. There is a word limit in url. We cannot use body to send data with get request.
We are only sending data like query search term, filters, sort by and so on. But we are not creating stuff, we are not sending data that is being used to edit/update or create stuff.

Post request: Used to post data to the server, client important data as part of the request body and it wont be included in the query string. Instead it is sent in the request body. This means we can send more data as we are not limited by url length, and we can send data as any type including json, html. This data is not added to the query string, this data is payload of the request. In query string, everything is treated as text.

TLDR: Get req page, viewing things, no creating, updating or editing. No side effects to the backend.  
Post req is to create things, where you can send bunch of data like signing up, registering account, adding comment to your blog, posting new blog and adding photo and so. Post req allows us to submit data as part of request body, get request does not. As a result, we have more flexibility in what we send and how much we send.

Note: incoming request have query string and request body.

3: Express function have methods such as: .get, .send and .render methods.

sendFile() function in Express. js is mainly used to send the file at the given path whereas the 
render() function is used to render a view and send the HTML string to the client as a response. By default, res.render looks in views folder.

app.use: is a middleware that gets used on every single request

syntax to parse incoming request body with urlencoded/json payloads:

app.use(express.urlencoded({ extended:true})) i.e please parse data from req body as json

app.use(express.json()) . i.e please use middle ware to parse data from json

---

View engine allow us to render web pages using template files. These templates are filled with actual data and served to the client.
--
app.set('view engine', 'ejs') //this syntax sets the view engine to ejs

app.set("views", path.join(__dirname, "views")); i.e take absolute path and add views in that folder, so can execute files from dir above

---


4: REST stands for representational state transfer. It is set up guide line, idea, principles on how client and server should communicate with each other when architecting web applications.  - Architectural style for distributed hypermedia systems.

CRUD: create, read, update and delete.
resource is an entity that we provide access to via http.

http is stateless protocol, every request is on its own in vacuum, it does not have access to request before. 
Every restful system have restful interface, which mostly contains consistent url patterns matches with different http verbs. 
So we can combine base url with diff http methods to expose full CRUD operations over HTTP. We are going to create API, applications i.e. todo someone can create new comment, view it, edit it or delete it using restful guideline.
----
github has api that expose CRUD functionality for gist
get/gists/{gist_id}: gives me info /serve a form with .render

post/gists/{gist_id}: post req to same endpoint gists is how we make new gist. (gists is a resource in rest context)

-- need to npm i methodOverride and require it
patch/gists/{gist_id}: updating something on same endpoint. /also has payload like post request

put: replacing whole  object.

delete/gists/{gist_id}: delete something 



I have crud capability via http.

BASIC CRUD FUNC blueprint
 GET /comments - list all comments
 POST /comments - Create a new comment
 GET /comments/:id - Get one comment (using ID)
 PATCH /comments/:id - Update one comment 
 DELETE  /comments/:id - Destroy one comment
---

 We can listen for .get , .post etc request inside our express ap

 HTML forms can only send get and post req. Cannot send put/patch and so on