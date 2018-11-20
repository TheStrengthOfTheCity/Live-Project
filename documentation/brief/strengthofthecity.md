# The Strength of the City

**Challenge Rating: 3/5**

MMU regularly collaborates on events, where we can enjoy a day or so with our local community, learn a thing or two and hopefully make people enthusiastic about the work we do.

Manchester Science Festival is one those events. We are slowly putting together a fun installation we can take to it.

Here's what we're doing. 

We go to MSF with an enclosure in which members of the public will participate in individal exercises in a competition to find 'The Strength of Manchester'. During the event, participant demographic and performance data will be taken, and added to a searchable database. The data will be made available to researchers.

## The Strength of Manchester Data Acquisition System

The following schematic illustrates the flow of participants through the event. The schematic shows just 2 Observers. There may be many more. [![schematic](./schematic.jpg)](https://github.com/CMDT/DigitalLabsOperations/blob/master/Business%20Development/Prospective/MSF2017/docs/estimate/schematic.jpg)

### Registration

On entering the event, participants will be given a visit token by a concierge. The token will uniquely identify them for the event.

###Entry

On entry to the enclosure, the concierge will ask each participant to complete an entry survey.
The survey will ask them questions about their attitude and experience prior to the event.
The survey will be run on a tablet app, and will associate their answers with their event token.
The concierge will handle entry of the participants answers.

### Performance Capture

Each participant will visit several stations within the enclosure.
Each station is dedicated to a single exercise. There may be more than one station servicing each exercise, in order to process participants as quickly as possible.

Each station is run by an observer who will be responsible for ensuring participants perform the exercises consistently. The measurement will be recorded on a tablet, which will send it to a central facility. The app will be very responsive. The time to record the measurement will be minimal.

Each observer will:

- operate an instrument which will be reset for each participant.
- record the participant's visit token before they begin the exercise.
- record the one-time measurement, representing the participant's performance.

### Exit

On exit from the enclosure, the concierge will ask each participant to complete an exit survey. The survey will ask them questions about their attitude and experience post the event. The survey will be run on a tablet app, and will associate their answers with their event token. The concierge will handle entry of the participants answers.

### Event Display

During the event, a large display screen will show a leader-board of the top-scoring participants.

## System

The primary development is to be able to accumulate population performance data at a single event.

This will be done by the use of specially prepared apps, designed around a flow of participants, with the following priority:

1. performance data
2. survey data

It may not be possible to survey all participants at the event, due to the length of time a survey will take to complete. However, the system is designed that many concierges, registrars and observers can be supported: on encountering a particpant, the app user enters the shortcode identifier of the participant, then their data, and then uploads it in the shortest possible time.

Following, is a list of the apps needed, and their function, the website needed to display results, and the data facility needed to store them.

### Administration App

This is used prior to the event, and sets up the activities and surveys to be expected at the event and how the activites will be scored. Once this is done, all other apps can see the event data, and can be set-up easily.

#### Function: Set up an Event

Create (Read, Update, Delete) an Event. Add event name, description, location, start and end date

#### Function: Set up Performance Attributes

Create (Read, Update, Delete) a performance attribute: Add attribute name, description, units Add attribute scoring ranges (score value and threshold) - for evaluation purposes.

#### Function: Build the Event

Add and remove performance attributes to and from an event. Add and remove surveys to an from an event.

### Registration App

This is used by the Registras, and will provide a shortcode identifier for a participant, to be used around the event enclosure.

#### Function: Register a Participant

Create (Read, Update, Delete) a participant. Add participant nickname.

#### Function: create a Participant Code

Obtain a short-form (5 digit) participant code, unique within the event. (The short form code can be combined with the event id to get the full participant Id)

### Concierge App (Entry)

This presents a survey to be answered by a participant, on entry to the Event

#### Function: Setup

*Used before the event*
List and select from the available events, the event being held List and select from the available surveys, the survey to be used at the event

#### Function: Survey a Participant

*Used during the event* Enter the shortform code of the participant Present a survey to be answered. Upload the survey results.

### Concierge App (Exit)

This presents a survey to be answered by a participan on exit from the Event

#### Function: Setup

*Used before the event* List and select from the available events, the event being held List and select from the available surveys, the survey to be used at the event

#### Function: Survey a Participant

*Used during the event* Enter the shortform code of the participant Present the survey to be answered. Upload the survey results.

### Observation App

This allows the speedy evaluation of a single action performed by a partipant. Data is entered by the Observer.

#### Setup

*Used before the event* List and select from the available events, the event being held. List and select from the available attributes the attribute to be observed during the event.

#### Per observation

*Used during the event*
Enter the shortform code of the participant Enter the value of the attribute observed Upload the value.

### Leader board Web Site

This is a web-based UI which will connect to the data facility. It can be used in display mode (i.e. full-screen monitor) or as a website.

#### Front Page

List and select from the available events

#### Running

Show a list of all event participants (paged per 100) and their scores.

#### Search

Select from an list of events, and search for your nickname or participant to get individual performance readings.

### Data Facility

The data facility holds the definition of all data, and provides an easilly-searchable schema for the accumulated observation data.

The Data facility will be split into separate parts:

- Survey definitions and anonymous answer data
- Attribute definitions and anonymous performance data
- Event definitions and shortform identifier lookups and nicknames

Survey definition and answer data will be freely searchable, by clients having an access code. All data is linked to a unique participant identifier. Security is minimal. The definitions and performance data will be freely searchable, by clients having an access code. All performance data is linked to a unique participant identifier. Security is minimal. The event definitions data provides a lookup from participant identifiers, to shortcode data used at each event. It has minimal security.

## How far have we got?

Last year's Live Project (Thanks [RatchetC](https://github.com/RatchetC/)!) gave us:

* Administration App
* Registration App
* Observation App
* Data Facility

-----------------

# Your Project

This year, we want to get to a functional system, by adding a leader-board, which is actually a searchable website of results. It can be used equally well on a giant display screen at the event, or a by someone who wants to see how they did when they get home.

Here are some examples to give you an idea of what we mean:

First, searching for a leader-board, for the current event:

![results_1](results_visualiser_page_1_3.png)

Next, look for the nickname of a person, so you can see their results: 



![results_2](./results_visualiser_context.png)



Now, click on the entry, to get the full breakdown of their event performance:

![individual](results_visualiser_subject_display.png)

## Development

You will certainly need to use RatchetC's source code to create and deploy the apps, so you can populate the Data Facility.

You will need to look at the data which you have and how it is created and stored together.

You will need to create a NodeJS server, to create the leaderboard data, and wrap it in a REST API.

You will need to create a single page web app, using AngularJS, to display it.

# Experience Areas
**This project will allow members to gain and exercise knowledge and experience in the following areas:**
- Project Management
- Javascript, AngularJS, Node.js
- RESTful web services
- Platforms-as-a-service: Restlet, Heroku

# Possible costs
n/a

# Equipment or Accounts needed
- developer accounts to Heroku service, Restlet Cloud


