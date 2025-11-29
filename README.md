1. Difference between res.send() and res.sendFile() and when to use them:
res.send() is used to send a response directly, usually a string, JSON, or HTML code written in the response itself. On the other hand, res.sendFile() is used to send an entire file as the response, such as an HTML file stored on the server. You would use res.send() for small or dynamic content generated on the fly, and res.sendFile() when you have a full static file you want to serve to the user.

2. Why the path module is necessary when serving files:
The path module helps create correct file paths across different operating systems. If you just use a relative path like 'public/index.html', it might work sometimes, but it can break depending on where the server is run or the operating system (Windows vs Mac/Linux). Using path.join(__dirname, 'public', 'index.html') ensures the server always finds the file because it builds an absolute path from the server’s current directory.

3. How to add a third page (e.g., a menu page) to the server:
To add a new page, you would first create a new HTML file in the public folder, for example menu.html. Then, in server.js, you would add a new route for it:

app.get('/menu', (req, res) => {
  res.sendFile(path.join(__dirname, 'public', 'menu.html'));
});


After that, visiting http://localhost:3000/menu would display the new page. Basically, it’s just creating the file and defining a route for it in the server.
