# Stack Keeper

A web application for managing speaking turns in student council meetings. Stack Keeper helps facilitate orderly discussions by tracking who has spoken, managing the speaking queue, and enforcing time limits.

## Features

- **Member Roster**: Display all council members with their speak counts
- **Stack Management**: Automatically orders speakers by speak count (lower counts first)
- **Response Queue**: Separate queue for responses that occur within the current speaker's time
- **3-Minute Timer**: Automatic countdown timer with visual warnings
- **Data Persistence**: Automatically saves state to browser localStorage

## How to Use

### Getting Started

1. Open `index.html` or visit [https://snigdhapodugu.github.io/8csc-stack/](https://snigdhapodugu.github.io/8csc-stack/) in any modern web browser
2. The application will automatically load any saved state from previous sessions
3. All council members are displayed in the left sidebar

### Adding Members to the Stack

**Regular Stack:**
- Click the **"Add"** button next to any member's name
- Members are automatically ordered by speak count:
  - Lower speak counts appear first
  - Members with the same count are ordered by when they were added

**Response Queue:**
- Click the **"Response"** button next to a member's name
- Responses are handled within the current speaker's 3-minute time slot
- The timer does NOT reset when a response is given
- After all responses are complete, the system returns to the original speaker if time remains

### Managing the Speaking Queue

**Next Speaker:**
- Click **"Next Speaker →"** to move to the next person in the regular speaking stack
- This action will:
  - Remove the current speaker from the stack
  - Increment their speak count by 1
  - Move to the next person in the queue
  - Automatically reset and start the 3-minute timer
  - Clear any saved "original speaker" (used for responses)

**Next Response:**
- Click **"Next Response →"** to move to the next person in the response queue
- If the response queue is empty, it automatically falls back to the regular stack
- This action will:
  - Remove the current responder from the response queue
  - Increment their speak count by 1
  - Continue the timer without resetting

**Remove from Stack:**
- Click the **"Remove"** button next to any person in the stack list
- This removes them from the queue WITHOUT incrementing their speak count
- Useful for removing someone who no longer wants to speak

**Remove from Response Queue:**
- Click the **"Remove"** button next to any person in the response queue
- This removes them from the response queue WITHOUT incrementing their speak count

### Timer Controls

The timer is displayed at the top of the page and automatically runs when you click "Next Speaker".

- **Start**: Manually start the 3-minute countdown
- **Pause**: Pause the timer (useful for breaks or interruptions)
- **Reset**: Reset the timer back to 3:00

**Timer Features:**
- Automatically starts at 3:00 when "Next Speaker" is clicked
- Shows a visual warning when 30 seconds remain (changes to amber/orange)
- Shows a visual alert when time expires (changes to red)
- Displays an on-screen notification when the 3 minutes are up
- Timer continues running during responses (does not reset)

### Stack Management

**Clear Stack:**
- Click **"Clear Stack"** to empty both the regular stack and response queue
- This removes everyone from the queue
- Speak counts are preserved (not reset)
- Useful for clearing the queue when changing topics

**Reset All Counts:**
- Click **"Reset All Counts"** to set all members' speak counts to 0
- This should be used when moving to a new topic or discussion
- The stack and queues are preserved (not cleared)

### Understanding Speak Counts

- Each member has a **speak count** that tracks how many times they've spoken
- Speak counts are displayed as a badge next to each member's name
- When a member speaks (via "Next Speaker" or "Next Response"), their count increases by 1
- The queue automatically orders members by speak count to ensure everyone gets a fair chance
- Members with speak counts of 2 or more are placed at the bottom of their count group

### Visual Indicators

- **Purple**: Default color scheme for the application
- **Orange/Amber**: Used for response queue and timer warnings
- **Red**: Used for high speak counts (2+) and timer expiration
- **Current Speaker**: Highlighted with a distinct card showing their name and speak count

## Technical Details

### Technology

- **Single HTML File**: All code is contained in one file for easy deployment
- **Vanilla JavaScript**: No external dependencies required
- **localStorage**: Automatically saves state to browser storage

### Data Persistence

The application automatically saves:
- Member speak counts
- Current stack order
- Response queue
- Current speaker
- Timer state is NOT saved (resets on page reload)

Data is saved to browser localStorage and persists across browser sessions.

### Customization

**Adding/Removing Members:**
Edit the `members` array in the JavaScript section of `index.html`:

```javascript
let members = [
    { name: "Member Name", speakCount: 0 },
    // Add more members here
];
```

The application will:
- Use the code-defined member list as the base
- Preserve speak counts from previous sessions for existing members
- Ignore old members that are no longer in the list

## Contact

For bugs, feature requests, or update ideas, contact Snigdha.


