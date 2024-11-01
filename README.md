// Initialize an array to store chatbots
let chatbots = [];

// Function to create a new chatbot
export function createChatbot(name, gender, responses) {
    const chatbot = {
        name: name,
        gender: gender,
        responses: responses
    };
    chatbots.push(chatbot);
    return chatbot;
}

// Function to publish chatbots
export function publishChatbot(chatbot) {
    // Here you can implement logic to save chatbots to a database
    console.log("Chatbot published:", chatbot);
}

// UI Functions
$w.onReady(function () {
    $w("#createButton").onClick(() => {
        const name = $w("#nameInput").value;
        const gender = $w("#genderDropdown").value;
        const responses = $w("#responsesInput").value.split(",");

        const newChatbot = createChatbot(name, gender, responses);
        publishChatbot(newChatbot);
        
        // Clear inputs after creation
        $w("#nameInput").value = "";
        $w("#responsesInput").value = "";
        
        // Update the chatbot list display
        $w("#chatbotList").text += `Chatbot: ${newChatbot.name}, Gender: ${newChatbot.gender}\n`;
    });
});
