# Portfolio Website

This repository contains the code for my portfolio website. The website is built using Flask, a web framework in Python, and is hosted on PythonAnywhere. The user interface is designed with a custom HTML template and styled using CSS, with JavaScript being used for client-side interactivity.

[View the website here](http://liqianzhang.pythonanywhere.com/index.html)

## Features
**Dynamic Content Rendering**: The website uses Flask's dynamic route handling to render different pages, allowing for an easily scalable website structure.

**Portfolio Showcase**: The site displays a variety of projects, showcasing a wide range of technical skills.

**Contact Form**: The site includes a contact form for visitors to leave messages.

## Contact Form Message Storage

One of the highlights of this website is how it handles form submissions. When a user submits a message through the contact form, the form data is stored in a CSV file. This is achieved using Python's built-in CSV module.

Here's a snippet of the function that writes form data to the CSV:
```
def write_to_csv(data):
    with open('./web_server/database.csv', newline='', mode='a+') as database2:
        name = data['name']
        email = data['email']
        message = data['message']
        csv_writer = csv.writer(database2, delimiter=',', quotechar='"', quoting=csv.QUOTE_MINIMAL)
        csv_writer.writerow([name,email,message])
```

And here's how the form submission is handled: 
```
@app.route('/submit_form', methods=['POST', 'GET'])
def submit_form():
    if request.method == 'POST':
        try:
            data = request.form.to_dict()
            write_to_csv(data)
            return redirect('thankyou.html')
        except:
            return 'Did not save to database'
    else:
        return 'something went wrong, try again'
```

The submit_form function is called when a POST request is made to the /submit_form endpoint, such as when a user submits the contact form. The function retrieves the form data, calls the write_to_csv function to write the form data to a CSV file, and then redirects the user to a "thank you" page.

## Future work
- Apply more features between front end-back end interaction.
- Apply Machine Learning & Deep learning features on the website. 