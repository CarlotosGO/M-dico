# Medical Assistant Chatbot
> An Artificially Intelligent Medical Assistant Chat Bot created in 2021 as a project for my introductory course to artificial intelligence in the British University in Dubai.

> Python and deep learning algorithoms were used for the creation of realistic-sounding conversations.

> Concepts from natural language processing, deep learning, and neural networks were used in this project.

> A GUI is used to display the input and the output of the program.

> The GUI is designed to look like a typical messaging app using in social media.


## Design Process and Methods

> The chatbot is divided into five python files. Each python file performs a task that is essential for the bot to work. In this report, the five python files are going to be categorized and explained in their respective category. The categories are as follows: training, processing, and graphic user interface. The python files that handle the training of the dataset are nnModel.py, stem.py, and training.py. The python file that handles the processing of data is predict.py and the python file that handles the graphical user interface is gui.py. All of these files will be explored in more details throughout the report. For our dataset, we chose to create our own data and it was saved in intents.json.

## Training

>The main function of the python files that fall under this category is to load the data, process it, and train the bot using it. There are many processes that the data goes through but the main ones are looping through different linear function layers of a neural network and stemming. Stemming is the process of simplifying a word to its root form which helps the program to recognize patterns more efficiently. After the data goes through stemming, the program then sends it to the neural network layers that house a linear function that is used in recognizing patterns. After that, the process is repeated a couple of times and the trained data is then stored in a file called data.pth. 

>The stem.py file handles the stemming. The function tokenizeWords() creates an array that isolates each word and saves them. This array can be used later in the stemWords() function. In the stemWords() function, the process of stemming is used and the root of a word is returned. 

>The nnModel.py file houses the neural network that processes the data. The layers are defined in the __init__ function which is the standard function that handles the initialization of the attributes of an object. In this function, the three linear function layers are initialized with the addition of another linear function that focuses on the elements of a sentence instead of the sentence as a whole. The other function in this class is the forward() function which is the function that processes the data. In this function, the data is passed through each of the three linear function layers and ultimately ends up in the last element-specific linear function layer. 

>The last python file of the training process of the program is training.py. This file handles the actual process of extracting the data, processing it, and using it to train the program with the help of the aforementioned python files. The program first starts with tokenizing each word using the tokenizeWords() function mentioned in the stem.py file. Then, it creates the training data and passes them through the neural network we created in the nnModel.py file by apprehending the data from the intents.json file. 

>After the parameters of the training data are defined and the training data ready, the program proceeds to the training process. Using the functions from the nnModel.py file, the data from the training set is sent through each of the files and repeats until it reaches the desired number of epochs. At the very end, the data is saved in a variable and that variable is exported to data.pth.

## Processing

> The file that handles the retrieval of information from the data.pth is the predict.py python file. This file loads the information from the data.pth and uses it in functions that return the bot’s response depending on the user’s input. First, we save the values from the data.pth in usable variables and create a new object from the neural network class created in the nnModel.py file. Then, these variables and neural network object are going to be used in both the getBotInput() and getTag() functions. The getBotInput() function predicts the response of the chatbot depending on the user’s input and returns that response. The getTag() function is used to retrieve the tag of the predicted response and returns the phrase “online” or “offline”. Both of these functions go through the same first process but then retrieve and return different information. The first process both functions go through is sending the user’s input to the neural network and predicting which tag it falls under. This is the process where softmax is used. Softmax is a function that applies probability to processed data and returns the percentage of how likely the response matches the user’s input.

>After getting the prediction of the tag, the getBotInput() uses an if statement that states that if the probability of the prediction being the right match is over 75% then it returns one of the responses from the corresponding tag at random. If the probability of the prediction isn’t 75% then it returns a message asking the user to ask something else.

>In the getTag() function, the predicted tag is compared to the “goodbye” tag and if it satisfies the if statement then it returns the word “offline” otherwise it returns “online”. The first part of the function is the same as the previous function but the only difference is the information that the function returns. 

## Graphic User Interface

>For the graphical interface, we use the Tkinter python library to place widgets on the screen that can be interacted with by the user or that can be changed depending on the event. First, we create a class the houses all the functions needed to display the user interface. These functions call upon each other to display different windows. The application consists of two windows which are the waiting room and the doctor’s office. The waiting room is the first window presented to the user and its only function is to display a form that the user is then forced to fill out to proceed. The doctor’s office is the window that houses the chatbox and it is the one the user can input their message into to get a response. The application first starts by creating a new object of the class and executing the run() function. When it starts, it will initialize the variable root as a Tkinter object and it will call upon the login() function. The login() function houses the first page the user sees which is the waiting room. In the login() function, the title, the dimensions, and the properties of the window are set. Afterwards, labels are used to create the welcome message. Using Tkinter, the text and the properties of it are customized to fit the window and the aesthetic of the application. The next element of the page is the error message which is an empty label at first until the user tries to proceed without entering the required information. After that, four labels are created to display the names of the criteria needed to be filled out by the user and, to accompany these labels, four textboxes were added so that the user can type and so that the information can be retrieved by the program. 

>A button is then created so that the user can interact with it. The button calls upon the loginForm() function once it is pressed. The loginForm() function saves the data from the textboxes that the user filled out and determines whether to proceed to the next window or display an error message. Using an if statement, the program would determine whether to send the user to the other window or not. The program gets the information out of the textboxes using the Tkinter get() function and if it returns an empty space in any of the four textboxes then an error message will appear in the error label. If all the textboxes were filled then the function will destroy all the elements in the window, so it does not overlap the elements in the next window, and calls upon the mainWindowSetUp() function.

>In the mainWindowSetUp() function, the chat room is created. The chat room consists of the chat bot’s name with its status, a profile picture for the bot, a chat box with a scroll bar, a message box with a button, and a label with the information filled out by the user in the previous screen. The function starts by redefining the name, dimensions, and properties of the window. Then, a text box is used to, as a label, to present the name of the bot with its status. The name of the bot is displayed as “Assistant” with a number following it. The random function is used to get a random number so that the bot has a unique number every time the application is run. The status is also set to “Offline” until the user interacts with the bot. After that, the profile picture is created using a Tkinter canvas which is used to display basic shapes. A circle and a Japanese symbol were used to create the profile picture. Afterwards, a text box was used to create the chat window. Tags were used to differentiate between the user’s input and the bot’s response. The chat window cannot be written on but can be navigated using a scroll bar. Next, an entry box was created so that the user can type their message onto it. If the enter key was pressed, then it will execute the userTyping() function. A button is also created that executes the same function when it is pressed. Lastly, a text box was created to house the user’s information that they entered at the beginning of running the application.

>The userTyping() function only has one job which is to save the user’s input and send it to the addUserAndBotInputs() function. The addUserAndBotInputs() function displays the user’s input on the chat window, gets the bot’s response, and displays it. The chat window is automatically scrolled to the last message using Tkinter’s see() function. The user’s input is sent to predict.py file’s getBotInput() function which returns the bot’s response and displays it on the chat window. The last function of the addUserAndBotInputs() function is updating the status label that sits under the assistant label. By using the getTag() function from chat.py, a string would return “Offline” or “Online” depending on whether the user’s input tag matches the “goodbye” tag. That means when the user says goodbye to the chatbot the status changes to “Offline” and only turns back to “Online” when the user interacts with the chatbot again.

## Example
>![d](https://user-images.githubusercontent.com/92636212/186777655-60c18eb3-c0ed-45d5-971a-69752d877f78.png)