# scorpio
### Purpose: Transcribe Phone Calls To Store Conversations and Set Reminders

1. Twilio transactions save audio recordings of phone conversations
2. Use speech to text analyzer api (Google or Siri or popup archive)
3. wit.ai or indico parses those audio files to highlight the following:
    1. Numbers mentioned 
    2. Locations mentioned
    3. Dates mentioned
    4. Summary of intent and content
    5. Possibly people mentioned but it's less important
4. Organizes data into a helpful format
5. Adds trigger commands that user customizes
    1. if the trigger words are detected, those commands get added directly to calendar/external location or the words surrounding those trigger words get shown

### Routes and Models
#### Models:
User:
    contacts:
        conversations
            audio data/file
            text data
            locations, people, etc.
            words surrounding triggers
            time of conversation
    triggers
    
#### Routes:
1. get/register - registers a user to the app
2. post/register
3. get/login - logs in and renders the home page that has a list of your stored contacts
4. post/login
5. post/call - makes a request to twilio, twilio handles the call and records an audio file. We then make a request to an audio to text api. Then run that text through a text analyzer. Add results to the data model.
    - give the user a new twilio number
    - set the bin number (within TWiML code) to the person they are calling (the contact's number)
    - add a recording command within the TWiML code
    - or just send a transcription command directly with twilio, and bypass the speech-to-text analyzer
6. get/convo - grabs the conversation text sorted by date.
7. post/trigger - adding new trigger words or phrases to the data model.
