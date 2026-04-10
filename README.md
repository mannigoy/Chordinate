# IT317-G

## AGILE PLANNING

## Proponents:

## Pielago, Emman Roy D.

## Date: April 4, 2026


## EPIC 1: Onboarding

Enable new users to discover, understand, and navigate into the CHORDINATE app through a smooth
introduction experience.

### FEATURE: App Introduction & Navigation

### User Story: Navigate to Login/Register (ONB-002)

As a new user, I want to navigate from the intro screen to the Login or Register page so that I can access the
app.

```
MoSCoW Story Pts Business Value Priority MVP Status
MUST 3 9 High YES - MVP
```
#### Acceptance Criteria (User Story Level)

#### Given the app intro screen is displayed

#### When the user taps Login or Register

**Then** they are navigated to the correct authentication screen

#### Given the user is already logged in

#### When the app launches

**Then** they are redirected directly to the home screen

#### Given navigation is triggered

#### When the transition occurs

**Then** the screen change is smooth with no errors or blank states

### Subtask: Intro Screen Navigation UI

#### Subtask Acceptance Criteria

#### Given the app launches for the first time

#### When the intro screen renders

```
Then Login and Register buttons are clearly visible and tappable
```
#### Given Login button is tapped

#### When navigation is triggered

**Then** the Login screen loads within 1 second


### Subtask: Route Guard / Redirect Logic

#### Subtask Acceptance Criteria

#### Given a logged-in user opens the app

#### When the app checks auth state

**Then** they are redirected to the dashboard, bypassing the intro screen

### User Story: App Introduction Screen (ONB-001)

As a new user, I want to see an introduction screen when I first open the app so that I understand what
CHORDINATE is about.

```
MoSCoW Story Pts Business Value Priority MVP Status
MUST 2 7 High YES - MVP
```
#### Acceptance Criteria (User Story Level)

#### Given the app is opened for the first time

#### When the intro screen loads

**Then** the app name, logo, and a brief description are displayed

#### Given the intro screen is active

#### When the user does nothing

#### Then the screen remains static and does not auto-navigate without input

#### Given the intro screen is rendered

#### When on any device size

#### Then the layout is responsive and visually consistent

### Subtask: Intro Screen UI Design

#### Subtask Acceptance Criteria

#### Given the intro screen is rendered

#### When the page loads

#### Then logo, app name, tagline, and CTA buttons are all visible

#### Given the screen is displayed on a small device

#### When the layout is checked


#### Then no elements are cut off or overlapping

### User Story: Feature Highlights Carousel (ONB-003)

As a new user, I want to swipe through feature highlights so that I know what CHORDINATE can do before I
register.

```
MoSCoW Story Pts Business Value Priority MVP Status
COULD 3 5 Low Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** the carousel is displayed
**When** the user swipes left or right
**Then** the next or previous feature slide is shown

**Given** all slides have been viewed
**When** the user taps Get Started
**Then** they are navigated to the Register screen

**Given** a slide is active
**When** the carousel renders
**Then** a page indicator shows the current position

### Subtask: Carousel Component

#### Subtask Acceptance Criteria

**Given** the carousel mounts
**When** it renders
**Then** all feature slides load with icons and descriptions

**Given** the user swipes
**When** the gesture is detected
**Then** the slide transitions smoothly with animation

### User Story: App Tutorial / Onboarding (ONB-004)

As a new user, I want an interactive tutorial so that I can learn how to use the app's key features.

```
MoSCoW Story Pts Business Value Priority MVP Status
COULD 5 5 Low Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** a user logs in for the first time
**When** the tutorial is triggered


**Then** a guided walkthrough of the main features begins

**Given** the tutorial is active
**When** the user taps Skip
**Then** the tutorial is dismissed and the home screen is shown

**Given** the tutorial completes
**When** the final step is acknowledged
**Then** the app marks the tutorial as done and does not show it again

### Subtask: Tutorial Overlay / Tooltip System

#### Subtask Acceptance Criteria

**Given** the tutorial starts
**When** each step renders
**Then** a tooltip highlights the relevant UI element

**Given** the tutorial is completed
**When** state is saved
**Then** the tutorial flag is stored locally so it does not repeat


## EPIC 2: Authentication

Provide secure user registration, login, logout, and account recovery to protect user data and control
platform access.

### FEATURE: User Login & Session Management

### User Story: User Login (AUTH-001)

As a registered user, I want to log in with my credentials so that I can access my CHORDINATE account.

```
MoSCoW Story Pts Business Value Priority MVP Status
MUST 5 10 High YES - MVP
```
#### Acceptance Criteria (User Story Level)

**Given** valid email and password are entered
**When** the user taps Login
**Then** they are authenticated and redirected to the home dashboard

**Given** invalid credentials are entered
**When** the user taps Login
**Then** an error message Invalid email or password is displayed

**Given** the login form is submitted
**When** fields are empty
**Then** validation errors highlight the empty fields

### Subtask: Login UI Form

#### Subtask Acceptance Criteria

```
Given the login screen renders
When it loads
Then email and password fields plus a Login button are visible
```
```
Given invalid input is entered
When the user submits
Then inline validation messages appear below the relevant fields
```

### Subtask: Backend Authentication API

#### Subtask Acceptance Criteria

```
Given a POST /auth/login is received with valid credentials
When it is processed
Then the API returns 200 OK with a JWT token
```
**Given** invalid credentials are sent
**When** processed
**Then** the API returns 401 Unauthorized

### Subtask: Password Hashing / Security (AUTH-003)

#### Subtask Acceptance Criteria

**Given** a user registers
**When** their password is stored
**Then** it is hashed using bcrypt before saving to the database

**Given** a login attempt is made
**When** the password is verified
**Then** the system compares the hash and denies access if it does not match

### User Story: Logout (AUTH-002)

As a logged-in user, I want to log out so that my account is secure when I am not using the app.

```
MoSCoW Story Pts Business Value Priority MVP Status
MUST 2 8 Medium YES - MVP
```
#### Acceptance Criteria (User Story Level)

**Given** the user taps the Logout button
**When** the action is confirmed
**Then** the session is invalidated and the user is returned to the intro screen

**Given** logout succeeds
**When** the session ends
**Then** all locally cached auth tokens are cleared


### Subtask: Logout UI & Session Clearing

#### Subtask Acceptance Criteria

**Given** the logout button is tapped
**When** confirmation is given
**Then** the JWT token is removed from local storage

**Given** the user is logged out
**When** they try to access a protected route
**Then** they are redirected to the Login screen

### FEATURE: Account Security & Recovery

### User Story: Backend Permission Validation (AUTH-007)

As a system, I want all API requests to validate permissions so that unauthorized users cannot access
protected resources.

```
MoSCoW Story Pts Business Value Priority MVP Status
MUST 5 9 Medium Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** a request is made to a protected endpoint without a token
**When** it is processed
**Then** the API returns 401 Unauthorized

**Given** a valid token is attached to a request
**When** it is processed
**Then** access is granted to the appropriate resource

**Given** a token has expired
**When** a request is made
**Then** the API returns 401 and prompts re-authentication

### Subtask: JWT Middleware

#### Subtask Acceptance Criteria

**Given** a request arrives with a Bearer token
**When** middleware runs
**Then** the token is decoded and the user identity is attached to the request

```
Given the token is invalid or tampered
```

**When** middleware validates it
**Then** the request is rejected with 401

### User Story: Email Validation (AUTH-004)

As a new user, I want my email to be validated during registration so that only valid accounts are created.

```
MoSCoW Story Pts Business Value Priority MVP Status
SHOULD 2 6 Low YES - MVP
```
#### Acceptance Criteria (User Story Level)

**Given** an invalid email format is entered
**When** the user submits the form
**Then** a validation error Enter a valid email is shown

**Given** a valid email is entered
**When** the user submits
**Then** registration proceeds without email-related errors

### Subtask: Email Format Validator

#### Subtask Acceptance Criteria

**Given** the user types in the email field
**When** they leave the field
**Then** the format is checked and an error shown if invalid

### User Story: Password Reset (AUTH-005)

As a user who forgot their password, I want to reset it via email so that I can regain access to my account.

```
MoSCoW Story Pts Business Value Priority MVP Status
SHOULD 5 7 Low Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** the user taps Forgot Password and enters a valid email
**When** submitted
**Then** a password reset link is sent to that email

**Given** the reset link is clicked within the valid window
**When** it is opened


**Then** the user is taken to a form to set a new password
**Given** the reset link has expired
**When** the user clicks it
**Then** they see an Expired link message and are prompted to request a new one

### Subtask: Reset Email Flow

#### Subtask Acceptance Criteria

**Given** a reset is requested and the email is valid
**When** processed
**Then** a tokenized reset link is generated and emailed within 30 seconds

### User Story: Social Login (AUTH-006)

As a user, I want to log in using Google or Facebook so that I can sign in without creating a separate
password.

```
MoSCoW Story Pts Business Value Priority MVP Status
WON'T 8 4 Low Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** the user taps Login with Google and approves OAuth consent
**When** authenticated
**Then** they are redirected to the home screen

**Given** the user cancels OAuth consent
**When** the flow is dismissed
**Then** they are returned to the login screen with no error


## EPIC 3: Profile

Allow users to view and manage their personal profiles, including their band memberships and profile photo.

### FEATURE: Profile Management

### User Story: View Profile (PROF-001)

As a user, I want to view my profile so that I can see my personal information and band memberships.

```
MoSCoW Story Pts Business Value Priority MVP Status
MUST 3 8 High YES - MVP
```
#### Acceptance Criteria (User Story Level)

**Given** the user navigates to their profile
**When** the screen loads
**Then** their name, photo, role, and joined bands are displayed

**Given** the profile data is loading
**When** a network call is in progress
**Then** a loading indicator is shown

**Given** no profile data is found
**When** the screen loads
**Then** a prompt to complete the profile is shown

### Subtask: Profile Screen UI

#### Subtask Acceptance Criteria

**Given** the profile screen renders
**When** data is available
**Then** name, avatar, and band list are all visible

### Subtask: Profile Data Fetch API

#### Subtask Acceptance Criteria

**Given** GET /users/:id is called
**When** the user exists
**Then** the API returns profile data with 200 OK


### User Story: Edit Profile (PROF-002)

As a user, I want to edit my profile details so that my information stays current.

```
MoSCoW Story Pts Business Value Priority MVP Status
MUST 3 7 Medium YES - MVP
```
#### Acceptance Criteria (User Story Level)

**Given** the user taps Edit Profile
**When** the edit form opens
**Then** current profile values are pre-filled in the fields

**Given** valid changes are saved
**When** the user submits
**Then** the profile is updated and a success message is displayed

**Given** required fields are cleared
**When** the user submits
**Then** validation errors are shown and the form is not submitted

### Subtask: Edit Profile Form UI

#### Subtask Acceptance Criteria

**Given** the edit form loads
**When** it renders
**Then** all editable fields show current values

### Subtask: Update Profile API

#### Subtask Acceptance Criteria

**Given** a PATCH /users/:id request is made with valid data
**When** processed
**Then** the API returns 200 with updated profile


### User Story: View Joined Bands (PROF-003)

As a user, I want to view all bands I have joined so that I can manage my band memberships.

```
MoSCoW Story Pts Business Value Priority MVP Status
MUST 2 7 High YES - MVP
```
#### Acceptance Criteria (User Story Level)

**Given** the user opens their profile
**When** band data is fetched
**Then** all joined bands are listed with name and role

**Given** the user has not joined any band
**When** the section loads
**Then** an empty state with Join or create a band prompt is shown

### Subtask: Joined Bands List Component

#### Subtask Acceptance Criteria

**Given** the bands section renders
**When** the user has bands
**Then** each band card shows the band name and the user's role

### User Story: Upload Profile Picture (PROF-004)

As a user, I want to upload a profile picture so that my bandmates can recognize me.

```
MoSCoW Story Pts Business Value Priority MVP Status
COULD 3 5 Low Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** the user taps the avatar
**When** the image picker opens
**Then** they can select a photo from their gallery

**Given** a valid image is selected
**When** it is uploaded
**Then** the new avatar is displayed on the profile immediately

**Given** an unsupported file type is selected


**When** upload is attempted
**Then** an error Only JPG/PNG allowed is shown

### Subtask: Image Upload Component

#### Subtask Acceptance Criteria

**Given** an image is picked
**When** upload is triggered
**Then** a progress indicator is shown and the image uploads to cloud storage


## EPIC 4: Access Control

Enforce role-based permissions and screen-level access restrictions to ensure users only access features
appropriate to their role.

### FEATURE: Role-Based Access & Screen Guards

### User Story: Mobile Screen Access Control (ACC-001)

As a system, I want to restrict access to certain screens based on authentication state so that
unauthenticated users cannot view protected pages.

```
MoSCoW Story Pts Business Value Priority MVP Status
MUST 5 8 Medium Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** an unauthenticated user tries to access a protected screen
**When** navigation is attempted
**Then** they are redirected to the Login screen

**Given** an authenticated user navigates to a protected screen
**When** the guard checks the token
**Then** they are granted access

### Subtask: Route Guard Implementation

#### Subtask Acceptance Criteria

**Given** the app initializes
**When** it checks auth state
**Then** protected routes are locked for unauthenticated sessions

### User Story: Role-Based Access Control (ACC-002)

As a band leader, I want certain actions to be restricted by role so that only authorized members can
perform administrative tasks.

```
MoSCoW Story Pts Business Value Priority MVP Status
SHOULD 5 8 Medium Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** a regular member tries to delete the band
**When** the action is attempted
**Then** they are denied with a Permission denied message

**Given** a band leader accesses admin features
**When** they are validated
**Then** they can manage members, roles, and band settings


**Given** a role is updated for a member
**When** the change is saved
**Then** their permissions are updated immediately

### Subtask: Role Permission Matrix

#### Subtask Acceptance Criteria

**Given** a user action is triggered
**When** the backend validates their role
**Then** only permitted actions are executed; others return 403 Forbidden


## EPIC 5: Band Management

Enable users to create and manage bands, invite members, assign musical roles, and maintain band
information.

### FEATURE: Band Creation & Membership

### User Story: Create Band (BAND-001)

As a musician, I want to create a band so that I can organize my group and start collaborating.

```
MoSCoW Story Pts Business Value Priority MVP Status
MUST 5 10 High YES - MVP
```
#### Acceptance Criteria (User Story Level)

**Given** the user fills in the band name and genre
**When** they submit
**Then** a new band is created and they are set as band leader
**Given** required fields are empty
**When** the form is submitted
**Then** validation errors prevent submission
**Given** a band is created
**When** the data is saved
**Then** the band appears in the user's profile under My Bands

**Subtask: Create Band UI Form**

#### Subtask Acceptance Criteria

**Given** the create band screen renders
**When** it loads
**Then** name, genre, and description fields are visible

**Subtask: Create Band API**

#### Subtask Acceptance Criteria

**Given** a POST /bands request is made with valid data
**When** processed
**Then** the API creates the band and returns 201 Created

### User Story: Invite Band Members (BAND-002)

As a band leader, I want to invite musicians to my band so that we can collaborate together.

```
MoSCoW Story Pts Business Value Priority MVP Status
SHOULD 3 8 Medium YES - MVP
```
#### Acceptance Criteria (User Story Level)


**Given** the band leader enters a username or email
**When** they send an invite
**Then** the invitation is delivered to the target user

**Given** a non-existent user is entered
**When** the invite is sent
**Then** an error User not found is displayed

### Subtask: Invite UI & Search

#### Subtask Acceptance Criteria

**Given** the invite screen opens
**When** the leader types a name
**Then** matching users are suggested in a dropdown

### Subtask: Invitation Backend

#### Subtask Acceptance Criteria

**Given** POST /bands/:id/invite is made and target user exists
**When** processed
**Then** an invitation record is created and a notification is sent

### User Story: Accept/Reject Band Invitation (BAND-003)

As a user, I want to accept or reject band invitations so that I can control which bands I join.

```
MoSCoW Story Pts Business Value Priority MVP Status
SHOULD 3 8 Medium YES - MVP
```
#### Acceptance Criteria (User Story Level)

**Given** an invitation is received
**When** the user taps Accept
**Then** they are added to the band and the invitation is marked accepted

**Given** an invitation is received
**When** the user taps Reject
**Then** the invitation is dismissed and the band is not joined

### Subtask: Invitation Response UI

#### Subtask Acceptance Criteria

**Given** the notifications screen loads and invitations exist
**When** it renders
**Then** each invite shows band name, inviter, and Accept/Reject buttons


### User Story: Assign Musical Roles (BAND-004)

As a band leader, I want to assign musical roles to members so that everyone knows their position in the
band.

```
MoSCoW Story Pts Business Value Priority MVP Status
MUST 3 7 Medium YES - MVP
```
#### Acceptance Criteria (User Story Level)

**Given** the band leader selects a member and assigns a role
**When** the role is saved
**Then** the member's role is updated and visible to all band members

**Given** a role is already assigned
**When** the leader changes it
**Then** the new role replaces the old one

### Subtask: Role Assignment UI

#### Subtask Acceptance Criteria

**Given** the member list is open and a role picker is shown
**When** it renders
**Then** available roles (Vocalist, Guitarist, Bassist, Drummer, etc.) are listed

### User Story: View Band Members (BAND-005)

As a band member, I want to view all members in my band so that I know who is part of the group.

```
MoSCoW Story Pts Business Value Priority MVP Status
MUST 2 7 High YES - MVP
```
#### Acceptance Criteria (User Story Level)

**Given** the user opens a band and accesses the members tab
**When** it loads
**Then** all current members are listed with their name, avatar, and role

**Given** a member has no role assigned
**When** the list renders
**Then** their role is shown as Unassigned

### Subtask: Members List UI

#### Subtask Acceptance Criteria

**Given** the band members screen loads
**When** data is fetched
**Then** a card for each member shows name, photo, and musical role


### User Story: Edit Band Information (BAND-006)

As a band leader, I want to edit band information so that the band profile stays accurate.

```
MoSCoW Story Pts Business Value Priority MVP Status
COULD 2 5 Low Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** the leader taps Edit Band
**When** the edit form opens
**Then** all current band details are pre-filled

**Given** valid changes are saved
**When** the form is submitted
**Then** band info is updated and a success toast is shown

### Subtask: Edit Band Form

#### Subtask Acceptance Criteria

**Given** the form renders
**When** current values load
**Then** name, genre, and description fields are editable

### User Story: Remove Band Member (BAND-007)

As a band leader, I want to remove a member from the band so that inactive members can be managed.

```
MoSCoW Story Pts Business Value Priority MVP Status
COULD 2 5 Low Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** the leader selects Remove Member
**When** a confirmation dialog appears
**Then** the member is removed from the band upon confirmation

**Given** a member is removed
**When** the action completes
**Then** they no longer appear in the band's member list

### User Story: Delete Band (BAND-008)

As a band leader, I want to delete a band so that disbanded groups can be removed from the platform.

```
MoSCoW Story Pts Business Value Priority MVP Status
WON'T 3 3 Low Not MVP
```

#### Acceptance Criteria (User Story Level)

**Given** the leader taps Delete Band
**When** a confirmation prompt is shown
**Then** the band is permanently deleted upon confirmation

**Given** a band is deleted
**When** the action completes
**Then** all associated songs and rehearsals are also removed


## EPIC 6: Song Management

Allow bands to add, organize, search, edit, and delete songs within their band's song library.

### FEATURE: Song Library

### User Story: Add Song (SONG-001)

As a band member, I want to add a song to our library so that the band can rehearse and manage it.

```
MoSCoW Story Pts Business Value Priority MVP Status
MUST 3 9 High YES - MVP
```
#### Acceptance Criteria (User Story Level)

**Given** valid song details are entered
**When** the user submits
**Then** the song is added to the band's library and appears in the list

**Given** required fields are empty
**When** the form is submitted
**Then** validation errors are shown

**Given** a song is added
**When** it is saved
**Then** the title, artist, and key are stored correctly

### Subtask: Add Song Form UI

#### Subtask Acceptance Criteria

**Given** the add song screen renders
**When** it loads
**Then** title, artist, key, and notes fields are displayed

### Subtask: Store Song Metadata (SONG-003)

#### Subtask Acceptance Criteria

**Given** a song is submitted
**When** POST /songs is called
**Then** the API stores the metadata and returns 201 Created

### User Story: Upload Audio File (SONG-002)

As a band member, I want to upload an audio file for a song so that members can listen to the reference track.

```
MoSCoW Story Pts Business Value Priority MVP Status
```

```
COULD 5 6 Low Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** a valid audio file is selected
**When** upload begins
**Then** a progress bar is shown and the file is uploaded

**Given** an unsupported file type is chosen
**When** upload is attempted
**Then** an error Unsupported format is displayed

### Subtask: Audio Upload Component

#### Subtask Acceptance Criteria

**Given** a file is selected
**When** the upload starts
**Then** the UI shows upload progress and a success state on completion

🧾 **User Story: Edit Song (SONG-004)**

As a band member, I want to edit song details so that I can correct or update information.

```
MoSCoW Story Pts Business Value Priority MVP Status
SHOULD 2 6 Medium Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** the user opens a song and taps Edit
**When** the form opens
**Then** existing song data is pre-filled

**Given** changes are saved
**When** the form is submitted
**Then** the song is updated and a success message is shown

### Subtask: Edit Song Form

#### Subtask Acceptance Criteria

**Given** the edit form loads
**When** current values are shown
**Then** all fields are editable and changes persist on save

### User Story: Search Songs (SONG-005)

As a band member, I want to search for songs in our library so that I can quickly find what I need.

```
MoSCoW Story Pts Business Value Priority MVP Status
```

```
SHOULD 2 7 Medium Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** the user types in the search bar
**When** results are filtered
**Then** only songs matching the query are displayed

**Given** no songs match the query
**When** search completes
**Then** an empty state No songs found is shown

### Subtask: Search Bar & Filter Logic

#### Subtask Acceptance Criteria

**Given** a search query is entered
**When** the filter runs
**Then** the list updates in real-time as the user types

### User Story: Delete Song (SONG-006)

As a band member, I want to delete a song from the library so that outdated songs can be removed.

```
MoSCoW Story Pts Business Value Priority MVP Status
COULD 1 4 Low Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** the user taps Delete on a song
**When** a confirmation dialog appears
**Then** the song is permanently removed upon confirmation

**Given** deletion succeeds
**When** the list refreshes
**Then** the deleted song no longer appears in the library

### User Story: Filter by Key (SONG-007)

As a band member, I want to filter songs by musical key so that I can find songs in a specific key quickly.

```
MoSCoW Story Pts Business Value Priority MVP Status
COULD 2 5 Low Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** the user selects a key filter
**When** the filter is applied
**Then** only songs in that key are shown
**Given** no songs match the selected key


**When** filter is applied
**Then** an empty state message is shown

### User Story: Pagination (SONG-008)

As a user, I want the song list to paginate so that the app remains performant with a large library.

```
MoSCoW Story Pts Business Value Priority MVP Status
COULD 2 4 Low Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** the song list loads and there are more than 20 songs
**When** the page renders
**Then** only the first page of results is shown
**Given** the user scrolls to the bottom
**When** the next page is triggered
**Then** additional songs are loaded and appended to the list


## EPIC 7: Chord Transposition

Provide musicians with tools to transpose chords, select keys, and manage preferred key settings for songs.

### FEATURE: Chord Transposition Tools

### User Story: Chord Transposition Algorithm (CHRD-001)

As a developer, I want a chord transposition algorithm so that chords can be accurately converted
between musical keys.

```
MoSCoW Story Pts Business Value Priority MVP Status
MUST 8 8 Medium Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** a chord and target key are provided
**When** the algorithm runs
**Then** the correct transposed chord is returned

**Given** a sharp/flat edge case is provided e.g. B# or Cb
**When** the algorithm runs
**Then** the enharmonic equivalent is returned correctly

**Given** an invalid chord is given
**When** the algorithm runs
**Then** an error is returned rather than a wrong result

### Subtask: Core Transposition Logic

#### Subtask Acceptance Criteria

**Given** a set of chords and a semitone shift are passed
**When** the function runs
**Then** each chord is transposed by the correct number of semitones

### User Story: Key Selection UI (CHRD-002)

As a user, I want to select a target musical key so that I can transpose chords to the key I need.

```
MoSCoW Story Pts Business Value Priority MVP Status
SHOULD 3 7 Medium Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** the chord screen opens
**When** it renders
**Then** a key selector showing all 12 keys C through B is visible


**Given** the user selects a key
**When** the selection is confirmed
**Then** the chord display updates to the new key

### Subtask: Key Selector Component

#### Subtask Acceptance Criteria

**Given** the key selector renders
**When** it loads
**Then** all 12 chromatic keys are displayed as selectable options

### User Story: Display Transposed Chords (CHRD-003)

As a musician, I want to see chords displayed in my selected key so that I can play the song without
manual calculation.

```
MoSCoW Story Pts Business Value Priority MVP Status
MUST 3 8 Medium YES - MVP
```
#### Acceptance Criteria (User Story Level)

**Given** a key is selected
**When** transposition runs
**Then** all chords in the song are updated to reflect the new key

**Given** the display updates
**When** it renders
**Then** chord names are clear, readable, and correctly formatted

### Subtask: Chord Display Component

#### Subtask Acceptance Criteria

**Given** transposed chords are available
**When** the component renders
**Then** each chord is displayed with the correct name and formatting

### User Story: Handle Sharp/Flat Edge Cases (CHRD-004)

As a system, I want the transposition engine to handle enharmonic equivalents so that chords are always
musically accurate.

```
MoSCoW Story Pts Business Value Priority MVP Status
SHOULD 3 6 Low Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** a chord like E# is transposed
**When** the algorithm runs


**Then** it is correctly displayed as F

**Given** a chord like Cb is transposed
**When** the algorithm runs
**Then** it is correctly displayed as B

### Subtask: Enharmonic Normalization

#### Subtask Acceptance Criteria

**Given** a transposed chord contains a double sharp or flat
**When** normalization runs
**Then** it is converted to the standard equivalent

### User Story: Save Preferred Key (CHRD-005)

As a user, I want to save my preferred key for a song so that I do not need to re-select it every time.

```
MoSCoW Story Pts Business Value Priority MVP Status
COULD 2 5 Low Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** the user selects a key and taps Save as preferred
**When** the action completes
**Then** the key is stored and auto-selected next time the song opens
**Given** the song is opened again
**When** the preferred key is loaded
**Then** the correct key is pre-selected automatically


## EPIC 8: AI Key Detection

Use AI (Librosa integration) to detect the musical key of a recorded or uploaded audio clip, helping
musicians identify the correct key for their songs.

### FEATURE: AI-Powered Audio Key Detection

### User Story: Librosa AI Integration (AI-001)

As a developer, I want to integrate Librosa so that the app can analyze audio and detect musical keys.

```
MoSCoW Story Pts Business Value Priority MVP Status
SHOULD 13 8 Low Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** an audio file is passed to the Librosa pipeline
**When** analysis runs
**Then** a musical key is returned as output

**Given** the audio is corrupted or unreadable
**When** analysis is attempted
**Then** a descriptive error is returned instead of crashing

### Subtask: Librosa Backend Service

#### Subtask Acceptance Criteria

**Given** audio data is received by the backend
**When** Librosa processes it
**Then** the detected key and confidence score are returned

### User Story: Record Audio via Mobile Mic (AI-002)

As a user, I want to record audio using my phone's microphone so that I can detect the key of a live
instrument.

```
MoSCoW Story Pts Business Value Priority MVP Status
SHOULD 5 7 Low Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** the user taps Record and microphone permission is granted
**When** recording begins
**Then** a timer is shown and audio is captured

**Given** the user taps Stop
**When** recording ends
**Then** the audio is saved and ready for analysis


**Given** microphone permission is denied
**When** recording is attempted
**Then** a prompt to enable permissions in settings is shown

### Subtask: Microphone Recording Component

#### Subtask Acceptance Criteria

**Given** record button is tapped and mic is active
**When** the component renders
**Then** a waveform or recording indicator is displayed

### User Story: Upload Audio for AI (AI-003)

As a user, I want to upload an audio file for AI analysis so that I can detect the key of a pre-recorded track.

```
MoSCoW Story Pts Business Value Priority MVP Status
COULD 3 6 Low Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** the user selects an audio file
**When** upload begins
**Then** the file is sent to the AI analysis endpoint
**Given** an unsupported format is uploaded
**When** the upload is validated
**Then** an error Supported formats: MP3, WAV, AAC is shown

### User Story: Detect Musical Key (AI-004)

As a user, I want the app to detect the musical key from my audio so that I can tune my chord
transpositions.

```
MoSCoW Story Pts Business Value Priority MVP Status
SHOULD 8 8 Low Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** audio is submitted for analysis
**When** Librosa processes it
**Then** the detected key e.g. C Major or A Minor is returned
**Given** detection is complete
**When** results are available
**Then** the key is displayed clearly on screen


### Subtask: Key Detection Flow

#### Subtask Acceptance Criteria

**Given** audio analysis completes
**When** the result is returned
**Then** the detected key is passed to the display and storage layers

### User Story: Store Detected Key (AI-005)

As a system, I want to store the AI-detected key so that users can reference the result later without re-
analyzing.

```
MoSCoW Story Pts Business Value Priority MVP Status
SHOULD 2 6 Medium Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** a key is detected and the result is available
**When** saved
**Then** it is written to the song record in the database

**Given** a key is already stored
**When** a new detection is run
**Then** the stored key is updated with the latest result

### Subtask: Detected Key Storage

#### Subtask Acceptance Criteria

**Given** POST /ai/detect returns a key
**When** the result is valid
**Then** it is saved to the songs table under the detected_key field

### User Story: Display Key Result (AI-006)

As a user, I want to see the detected key displayed on screen so that I can use it for chord transposition.

```
MoSCoW Story Pts Business Value Priority MVP Status
SHOULD 2 7 Medium Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** key detection succeeds
**When** the result screen loads
**Then** the detected key is shown in large, readable text


**Given** no key could be detected
**When** the result loads
**Then** a message Could not detect key - try a clearer recording is shown

### User Story: AI Error Handling (AI-007)

As a user, I want to receive clear error messages when AI detection fails so that I know what went wrong.

```
MoSCoW Story Pts Business Value Priority MVP Status
SHOULD 2 7 Medium Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** audio analysis fails
**When** an error occurs
**Then** a user-friendly error message is shown instead of a crash

**Given** the backend returns an error code
**When** the UI receives it
**Then** the correct message is mapped and displayed to the user

### User Story: AI Performance Optimization (AI-008)

As a system, I want AI analysis to complete within acceptable time limits so that users are not left waiting.

```
MoSCoW Story Pts Business Value Priority MVP Status
COULD 5 5 Low Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** a standard audio clip under 30 seconds is submitted
**When** analysis runs
**Then** the result is returned within 5 seconds

**Given** analysis takes longer than expected
**When** a timeout occurs
**Then** the user is notified and offered a retry option


## EPIC 9: Rehearsal Management

Allow bands to create, schedule, manage, and track rehearsal events, including member RSVP and
calendar views.

### FEATURE: Rehearsal Scheduling

### User Story: Create Rehearsal Event (REHE-001)

As a band leader, I want to create a rehearsal event so that the band knows when and where to practice.

```
MoSCoW Story Pts Business Value Priority MVP Status
MUST 3 9 Medium YES - MVP
```
#### Acceptance Criteria (User Story Level)

**Given** the leader fills in date, time, and location
**When** the form is submitted
**Then** a rehearsal event is created and the band is notified

**Given** required fields are empty
**When** the form is submitted
**Then** validation errors are displayed

**Given** a rehearsal is created
**When** it is saved
**Then** it appears on the band's rehearsal schedule

### Subtask: Create Rehearsal Form UI

#### Subtask Acceptance Criteria

**Given** the create rehearsal screen renders
**When** it loads
**Then** date/time picker, location, and notes fields are visible

### Subtask: Create Rehearsal API

#### Subtask Acceptance Criteria

**Given** POST /rehearsals is called with valid data
**When** it is processed
**Then** the rehearsal is created and 201 is returned


### User Story: Assign Band to Rehearsal (REHE-002)

As a band leader, I want to assign a band to a rehearsal event so that the correct members are notified.

```
MoSCoW Story Pts Business Value Priority MVP Status
SHOULD 2 7 Medium Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** a rehearsal is being created and a band is selected
**When** it is saved
**Then** the rehearsal is linked to that band

**Given** the band is assigned
**When** the event is saved
**Then** all members of the band receive a notification about the rehearsal

### Subtask: Band Assignment UI

#### Subtask Acceptance Criteria

**Given** the rehearsal creation form renders
**When** a band picker is shown
**Then** the user's bands are listed for selection

### User Story: RSVP System (REHE-003)

As a band member, I want to RSVP to rehearsal events so that the band knows who is attending.

```
MoSCoW Story Pts Business Value Priority MVP Status
SHOULD 3 7 Medium Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** a rehearsal invite is received
**When** the member taps Going
**Then** their RSVP is recorded as Attending

**Given** the member taps Not Going
**When** the response is saved
**Then** their status is recorded as Not Attending

**Given** the band leader views the rehearsal
**When** RSVP data is loaded
**Then** a count of confirmed attendees is shown


### Subtask: RSVP Response UI

#### Subtask Acceptance Criteria

**Given** a rehearsal card is shown
**When** it renders
**Then** Going / Maybe / Not Going buttons are displayed

### Subtask: RSVP Backend

#### Subtask Acceptance Criteria

**Given** POST /rehearsals/:id/rsvp is called with a valid status
**When** processed
**Then** the RSVP is saved and 200 OK is returned

### User Story: View Rehearsal Schedule (REHE-004)

As a band member, I want to view upcoming rehearsal events so that I can plan my schedule accordingly.

```
MoSCoW Story Pts Business Value Priority MVP Status
MUST 2 9 High YES - MVP
```
#### Acceptance Criteria (User Story Level)

**Given** the user opens the rehearsal section
**When** data is fetched
**Then** all upcoming rehearsals for their bands are listed

**Given** no rehearsals are scheduled
**When** the section loads
**Then** an empty state No upcoming rehearsals is shown

**Given** the list renders
**When** it is displayed
**Then** each rehearsal shows date, time, location, and band name

### Subtask: Rehearsal Schedule List UI

#### Subtask Acceptance Criteria

**Given** the schedule screen loads
**When** rehearsal data is available
**Then** cards with date, time, and location are displayed in order


### Subtask: Fetch Rehearsals API

**Subtask Acceptance Criteria**

**Given** GET /rehearsals is called
**When** the user is authenticated
**Then** a list of upcoming rehearsals is returned

### User Story: Edit Rehearsal (REHE-005)

As a band leader, I want to edit rehearsal details so that I can update time, location, or notes if plans
change.

```
MoSCoW Story Pts Business Value Priority MVP Status
COULD 2 6 Low Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** the leader taps Edit Rehearsal
**When** the edit form opens
**Then** existing rehearsal data is pre-filled
**Given** changes are saved
**When** the form is submitted
**Then** the rehearsal is updated and members are notified of the change

### Subtask: Edit Rehearsal Form

#### Subtask Acceptance Criteria

**Given** the edit form loads
**When** it renders
**Then** all editable fields show the current values

### User Story: Delete Rehearsal (REHE-006)

As a band leader, I want to delete a rehearsal so that cancelled sessions are removed from the schedule.

```
MoSCoW Story Pts Business Value Priority MVP Status
COULD 1 5 Low Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** the leader taps Delete Rehearsal
**When** a confirmation dialog is shown
**Then** the rehearsal is permanently deleted upon confirmation


**Given** deletion succeeds
**When** the list refreshes
**Then** the deleted rehearsal no longer appears in the schedule

### User Story: Calendar View (REHE-007)

As a band member, I want to see rehearsals in a calendar view so that I can visually plan my month.

```
MoSCoW Story Pts Business Value Priority MVP Status
COULD 5 6 Low Not MVP
```
#### Acceptance Criteria (User Story Level)

**Given** the user switches to calendar view
**When** the calendar renders
**Then** rehearsal dates are marked on the correct days
**Given** a marked date is tapped
**When** it is selected
**Then** the rehearsal details for that day are shown

### Subtask: Calendar Component

#### Subtask Acceptance Criteria

**Given** the calendar loads
**When** rehearsal data is mapped
**Then** each rehearsal appears as a badge on its scheduled date


### Epic Summary Table

```
Epic Stories MVP Task IDs High Priority Task IDs
EPIC 1: Onboarding 4 ONB-001, ONB- 002 ONB-001, ONB- 002
EPIC 2: Authentication 6 AUTH-001, AUTH-002, AUTH-003,
AUTH- 004
```
```
AUTH-001, AUTH- 002
```
```
EPIC 3: Profile 4 PROF-001, PROF-002, PROF- 003 PROF-001, PROF- 003
EPIC 4: Access Control 2 None None
EPIC 5: Band Management 8 BAND-001, BAND-002, BAND-
003, BAND-004, BAND- 005
```
```
BAND-001, BAND- 005
```
```
EPIC 6: Song Management 7 SONG-001, SONG- 003 SONG- 001
EPIC 7: Chord Transposition 5 CHRD- 003 None
EPIC 8: AI Key Detection 8 None None
EPIC 9: Rehearsal Management 7 REHE-001, REHE- 004 REHE- 004
```

