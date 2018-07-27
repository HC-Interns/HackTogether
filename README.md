# HackTogether
> Real Time Editor on HC

**NOTE: This is a proposed implementation of the Real-Time Editor in HC. No code is written yet.**


## Conventional way:

### Overview:
> We all know how to do this. !!! Right!!!

### Issues:
- Real-Time problems.
- Rewire code for OT(Operational transformation) that is used for real time editing.

## Non-Conventional way:

### Overview : 

- Agent1 Creates a new Notepad and Shares the screen to Agent2 and Agent3 using the Together for editing
- Now their is a system that people can edit together.
- To add some Holochain magic, the data is only submited and stored in the DHT if validation is passed by all 3 of the users. 
    - So for this we will send it to Agent2 and Agent3 so that they agree by comparing with the copy they can see. 
    - This shows that even with the server that TogetherJS is using, no changes can be made in the  DHT by all of the agents agreeing

### Detail Working:

- Agent1(A1) Creates a notepad.
- A1 Can now hack on that notepad.
- A1 Decides to hack with others
    - A1 Creates a link using TogetherJS. 
    - This link is linked to the notepad_entry (So that the other users know were the entry is stored in the DHT. And they can acces it if needed).
    - A1 shares this to A2.
    - A2 adds this link to this App and gets a UI of the notpad that A1 is editing.
    - Now A2 can hack with A1.
    - Keep in mid nothing is submited in the DHT yet.
    - So when the A1 submits it in the DHT, A2 needs to validate this entry(Specificaly).
    - Once validated it is submited and can be updated in the next update with the same process.

- Now if A1 stops sharing the session for that link is closed.
- But A2 has access to the entry. So he can continew editing. And can create a session to work with others


### Issues:

- The TogetherJS is using a server to pass around the updates. (They have provided the server code. But do we trust them.)
- No record of all the small changes made by everyone(Do we need it. I can see the use but can we live without it?) 
- if the agent that started the session leaves the session is closed. causing an interuption for all the other agents. 

### Conclusion:
- This is good because it deals with the issues that HC is having with real-time soluitons.
- Also we can mess with the TogetherJS code to remove the unnecessary modules that we dont want link the chat etc.
- TogetherJS is created by **Morzilla**
