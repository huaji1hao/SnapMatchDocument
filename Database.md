1.	Users Table
•	UserID (Primary Key): Unique identifier for each user.
•	UserName: User's chosen name.
•	UserAccount: Account number for login in
•	PasswordHash: Hashed password for security.
•	Email: User's email address.
•	Phone: User's phone number
•	RegistrationDate: Date and time the user registered.
•	UpdateDate: Date and time the user account was last updated. This field is automatically updated to the current timestamp when the record is modified.
•	Avatar: Link to the user's avatar image.
•	UserStatus (int, default 0): Status of the user (e.g., 0 for normal, 1 for banned). This field is not nullable and has a default value of 0.
•	IsDelete: Flag to indicate if the user account is deleted (0 for not deleted, 1 for deleted). This field is not nullable and has a default value of 0.




CREATE TABLE Users (
    UserID INTEGER PRIMARY KEY AUTOINCREMENT,
    UserName VARCHAR(255),
    UserAccount VARCHAR(255),
    PasswordHash VARCHAR(255),
    Email VARCHAR(255),
    Phone VARCHAR(20),
    RegistrationDate DATETIME,
    UpdateDate DATETIME DEFAULT CURRENT_TIMESTAMP,
    Avatar VARCHAR(255),
    UserStatus INT NOT NULL DEFAULT 0,
    IsDelete TINYINT NOT NULL DEFAULT 0
);








2.	Challenges Table
•	ChallengeID (Primary Key): Unique identifier for each challenge.
•	UserID (Foreign Key): ID of the user who created the challenge.
•	ImgPath: URL of the challenge image
•	Tags: AI_Categories message
•	CreationDate: Date and time the challenge was created.
•	Caption: Brief description of the challenge.



CREATE TABLE Challenges (
    ChallengeID INTEGER PRIMARY KEY AUTOINCREMENT,
    UserID INT,
    ImgPath VARCHAR(255),
    Tags TEXT,
    CreationDate DATETIME,
    Caption TEXT,
    FOREIGN KEY (UserID) REFERENCES Users(UserID)
);






3.	Friends Table (Optional)
•	UserID1 (Foreign Key): ID of the first user.
•	UserID2 (Foreign Key): ID of the second user.
•	FriendshipDate: Date and time the friendship was established.



CREATE TABLE Friends (
    UserID1 INT,
    UserID2 INT,
    FriendshipDate DATETIME,
    FOREIGN KEY (UserID1) REFERENCES Users(UserID),
    FOREIGN KEY (UserID2) REFERENCES Users(UserID)
);




4.	Responses Table
•	ResponseID (Primary Key): Unique identifier for each comment.
•	ChallengeID (Foreign Key): ID of the challenge the comment is associated with.
•	UserID (Foreign Key): ID of the user who posted the comment.
•	ImagePath: The response image
•	Tags: 
•	CommentText: Text of the comment.
•	PostDate: Date and time the comment was posted.
•	isMatch: Boolean indicating if the user's image matched the challenge.



CREATE TABLE Responses (
    ResponseID INTEGER PRIMARY KEY AUTOINCREMENT,
    ChallengeID INT,
    UserID INT,
    ImagePath VARCHAR(255),
    Tags TEXT,
    CommentText TEXT,
    PostDate DATETIME,
    isMatch BOOLEAN,
    FOREIGN KEY (ChallengeID) REFERENCES Challenges(ChallengeID),
    FOREIGN KEY (UserID) REFERENCES Users(UserID)
);








Relationships:
•	A User can create multiple Challenges.
•	A Challenge can have multiple Images.
•	Images are uploaded by Users and are associated with Challenges.
•	Matches are determined between two Images in a Challenge.
•	Comments are made by Users on Challenges.
•	Users can have friendships with other Users (if implementing a friends system).
Additional Considerations:
•	Ensure that AI_Categories(Tags) in the Images table can store multiple category values (e.g., JSON format or a delimited string).
•	Consider adding indexes on frequently queried fields like UserID in the Challenges, Images, and Comments tables.
•	Ensure that the database schema supports efficient queries for the application's functionality, such as retrieving all challenges by a user, finding matches, and displaying comments with match indicators.


Database Test

Important:
Maybe need transactions in the combination of the scenarios

Scenario 1: User Registration

Objective: Test if a new user can be registered in the system.

INSERT INTO Users (UserName, UserAccount, PasswordHash, Email, Phone, RegistrationDate, Avatar, UserStatus, IsDelete)
VALUES ('Desss', 'Des123', 'hashed_password', 'idk@example.com', '1234567890', CURRENT_TIMESTAMP, 'link_to_avatar', 0, 0);

Scenario 2: Posting a New Challenge

Objective: Test if a user can post a new challenge and it gets recorded correctly.

-- Assuming a user with UserID 1 already exists
INSERT INTO Challenges (UserID, ImgPath, Tags, CreationDate, Caption) 
VALUES (1,'path_to_challenge_image.jpg', 'chair, table', CURRENT_TIMESTAMP,'Find objects that match these! ');


Scenario 3: Commenting on a Challenge

Objective: Test if users can post comments on a challenge.

-- Assuming a challenge with ChallengeID 1 and a user with UserID 2 already exist

INSERT INTO Responses (ChallengeID, UserID, ImagePath, Tags, CommentText, PostDate, isMatch) 
VALUES (1, 2, 'path_to_response_image.jpg', 'table', 'Here is my response!', CURRENT_TIMESTAMP, TRUE);

Scenario 4: Updating User Information

Objective: Test if a user can update their profile information

-- Assuming a user with UserID 1 already exists
UPDATE Users 
SET UserName = 'UpdatedName', Email = 'updated_email@example.com', Phone = '0987654321', Avatar = 'new_avatar_link.jpg'
WHERE UserID = 1;


Scenario 5: Adding a Friend

Objective: Test if users can add each other as friends.

-- User 1 and User 2 become friends
INSERT INTO Friends (UserID1, UserID2, FriendshipDate)
VALUES (1, 2, CURRENT_TIMESTAMP);



Scenario 6: User Account Deletion

Objective: Test if a user can delete their account.

-- Soft delete for User 2
UPDATE Users SET IsDelete = 1 WHERE UserID = 2;
