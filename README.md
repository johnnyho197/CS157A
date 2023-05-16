# CS157A
# SQL codes for Final Project:




CREATE TABLE "Tickets" (
	"ticket_id"	INTEGER NOT NULL,
	"ticket_type"	VARCHAR(50),
	"ticket_price"	INTEGER,
	PRIMARY KEY("ticket_id")
);

CREATE TABLE "Spectators" (
	"spectator_id"	INTEGER NOT NULL,
	"ticket_id"	INTEGER NOT NULL,
	"event_id"	INTEGER NOT NULL,
	"first_name"	VARCHAR(50),
	"last_name"	VARCHAR(50),
	"email_address"	VARCHAR(100),
	"last_purchase_date"	VARCHAR(50),
	PRIMARY KEY("spectator_id"),
	FOREIGN KEY("ticket_id") REFERENCES "Tickets"("ticket_id"),
	FOREIGN KEY("event_id") REFERENCES "Events"("event_id")
);

CREATE TABLE "Events" (
	"event_id"	INTEGER NOT NULL,
	"event_name"	VARCHAR(50),
	"event_date"	VARCHAR(50),
	"location"	VARCHAR(50),
	PRIMARY KEY("event_id")
);

CREATE TABLE "Officials" (
	"official_id"	INTEGER NOT NULL,
	"event_id"	INTEGER NOT NULL,
	"first_name"	VARCHAR(50),
	"last_name"	VARCHAR(50),
	"email_address"	VARCHAR(100),
	"phone_number"	VARCHAR(50),
	PRIMARY KEY("official_id"),
	FOREIGN KEY("event_id") REFERENCES "Events"("event_id")
);

CREATE TABLE "Athletes" (
	"athlete_id"	INTEGER NOT NULL,
	"team_id"	INTEGER NOT NULL,
	"first_name"	VARCHAR(50),
	"last_name"	VARCHAR(50),
	"date_of_birth"	VARCHAR(50),
	"gender"	VARCHAR(50),
	"nationality"	VARCHAR(50),
	PRIMARY KEY("athlete_id"),
	FOREIGN KEY("team_id") REFERENCES "Teams"("team_id")
);

CREATE TABLE "Teams" (
	"team_id"	INTEGER NOT NULL,
	"country_id"	INTEGER NOT NULL,
	"team_name"	VARCHAR(50),
	"coach_name"	VARCHAR(50),
	FOREIGN KEY("country_id") REFERENCES "Countries"("country_id"),
	PRIMARY KEY("team_id")
);

CREATE TABLE "Countries" (
	"country_id"	INTEGER NOT NULL,
	"country_name"	VARCHAR(50),
	"continent"	VARCHAR(50),
	PRIMARY KEY("country_id")
);

CREATE TABLE "Results" (
	"result_id"	INTEGER NOT NULL,
	"athlete_id"	INTEGER NOT NULL,
	"event_id"	INTEGER NOT NULL,
	"descipline_id"	INTEGER NOT NULL,
	"result_value"	VARCHAR(50),
	"result_date"	VARCHAR(50),
	FOREIGN KEY("athlete_id") REFERENCES "Athletes"("athlete_id"),
	FOREIGN KEY("descipline_id") REFERENCES "Disciplines"("discipline_id"),
	FOREIGN KEY("event_id") REFERENCES "Events"("event_id"),
	PRIMARY KEY("result_id")
);

CREATE TABLE "Disciplines" (
	"discipline_id"	INTEGER NOT NULL,
	"discipline_name"	VARCHAR(100),
	"description"	VARCHAR(255),
	PRIMARY KEY("discipline_id")
);


INSERT INTO Countries (country_id, country_name, continent)
VALUES 
  (1, 'United States', 'North America'),
  (2, 'Canada', 'North America'),
  (3, 'Mexico', 'North America'),
  (4, 'Brazil', 'South America'),
  (5, 'Argentina', 'South America'),
  (6, 'Peru', 'South America'),
  (7, 'France', 'Europe'),
  (8, 'Germany', 'Europe');

INSERT INTO Teams (team_id, country_id, team_name, coach_name)
VALUES 
  (1, 1, 'Team USA', 'John Smith'),
  (2, 1, 'Team Canada', 'Jane Doe'),
  (3, 4, 'Team Brazil', 'Carlos Silva'),
  (4, 4, 'Team Argentina', 'Maria Gonzalez'),
  (5, 7, 'Team France', 'Luc Dupont'),
  (6, 7, 'Team Germany', 'Hans Mueller'),
  (7, 7, 'Team Italy', 'Giovanni Rossi'),
  (8, 8, 'Team China', 'Li Wei');

INSERT INTO Athletes (athlete_id, team_id, first_name, last_name, date_of_birth, gender, nationality)
VALUES (1, 1,'John','Hank','1995-02-15','M', 'USA'),
 (2, 2, 'Jane','Harry','1998-06-22','M','Canada'),
 (3, 3, 'Mike','Johnson','1990-10-01','M','Australia'),
 (4, 4, 'Sarah','Lee','1992-08-10','F','USA'),
 (5, 5, 'David','Kim','1996-04-05','M','South Korea'),
 (6, 6, 'Emma','Wilson','1993-12-18','F','Canada'),
 (7, 7, 'James','Brown','1994-09-22','M','USA'),
 (8, 8, 'Sophia','Nguyen','1997-01-30','F','Vietnam'),
 (9, 7, 'Adam','Taylor','1991-06-20','M','Australia'),
 (10, 5, 'Emily','Chen','1999-03-12','F','China');

INSERT INTO Events (event_id, event_name, event_date, location)
VALUES
  (1, "Men's 100m Sprint", '2023-08-01', 'Tokyo Olympic Stadium'),
  (2, "Women's 200m Backstroke", '2023-08-02', 'Tokyo Aquatics Centre'),
  (3, "Artistic Gymnastics Individual All-Around", '2023-08-04', 'Ariake Gymnastics Centre'),
  (4, "Cycling Road Race", '2023-08-06', 'Fuji International Speedway'),
  (5, "Women's 75kg Weightlifting", '2023-08-07', 'Tokyo International Forum'),
  (6, "Men's Boxing Light Flyweight", '2023-08-09', 'Kokugikan Arena'),
  (7, "Mixed Team Judo", '2023-08-10', 'Nippon Budokan'),
  (8, "Women's Taekwondo -49kg", '2023-08-12', 'Makuhari Messe');

INSERT INTO Officials (official_id, event_id, first_name, last_name, email_address, phone_number) 
VALUES 
  (1, 2, 'John', 'Smith', 'john.smith@gmail.com', '123-456-7890'),
  (2, 1, 'Mary', 'Johnson', 'mary.johnson@gmail.com', '234-567-8901'),
  (3, 3, 'David', 'Davis', 'david.davis@gmail.com', '345-678-9012'),
  (4, 5, 'Jennifer', 'Jones', 'jennifer.jones@gmail.com', '456-789-0123'),
  (5, 4, 'Michael', 'Miller', 'michael.miller@gmail.com', '567-890-1234'),
  (6, 7, 'Michelle', 'Martinez', 'michelle.martinez@gmail.com', '678-901-2345'),
  (7, 6, 'Steven', 'Smith', 'steven.smith@gmail.com', '789-012-3456'),
  (8, 8, 'Amanda', 'Allen', 'amanda.allen@gmail.com', '890-123-4567');


INSERT INTO Tickets (ticket_id, ticket_type, ticket_price)
VALUES 
  (1, 'Standard', 50),
  (2, 'Premium', 100),
  (3, 'VIP', 200),
  (4, 'Standard', 60),
  (5, 'Premium', 120),
  (6, 'VIP', 250),
  (7, 'Standard', 70),
  (8, 'Premium', 150),
  (9, 'VIP', 300);


INSERT INTO Spectators (spectator_id, ticket_id, event_id, first_name, last_name, email_address, last_purchase_date)
VALUES
  (1, 7, 1, 'John', 'Doe', 'john.doe@gmail.com', '2022-03-01'),
  (2, 4, 3, 'Jane', 'Smith', 'jane.smith@gmail.com', '2022-03-02'),
  (3, 6, 2, 'Bob', 'Johnson', 'bob.johnson@gmail.com', '2022-03-03'),
  (4, 1, 4, 'Alice', 'Williams', 'alice.williams@gmail.com', '2022-03-04'),
  (5, 8, 5, 'David', 'Brown', 'david.brown@gmail.com', '2022-03-05'),
  (6, 9, 6, 'Karen', 'Taylor', 'karen.taylor@gmail.com', '2022-03-06'),
  (7, 3, 7, 'Mark', 'Anderson', 'mark.anderson@gmail.com', '2022-03-07'),
  (8, 5, 8, 'Amy', 'Thomas', 'amy.thomas@gmail.com', '2022-03-08');


INSERT INTO Disciplines (discipline_id, discipline_name, description)
VALUES
  (1, 'Athletics', 'Track and field events'),
  (2, 'Swimming', 'Competitive swimming events'),
  (3, 'Gymnastics', 'Artistic and rhythmic gymnastics events'),
  (4, 'Cycling', 'Road and track cycling events'),
  (5, 'Weightlifting', 'Strength and powerlifting events'),
  (6, 'Boxing', 'Combat sport with punches'),
  (7, 'Judo', 'Martial art and Olympic sport'),
  (8, 'Taekwondo', 'Korean martial art and Olympic sport');

INSERT INTO Results (result_id, athlete_id, event_id, discipline_id, result_value, result_date)
VALUES 
    (1, 2, 3, 3, '9.81', '2023-03-04'),
    (2, 3, 6, 4, '1.85', '2023-03-05'),
    (3, 4, 7, 5, '43.02', '2023-03-06'),
    (4, 5, 8, 2, '12.63', '2023-03-07'),
    (5, 6, 5, 1, '19.35', '2023-03-08'),
    (6, 7, 4, 8, '5.95', '2023-03-09'),
    (7, 8, 2, 7, '6:32.42', '2023-03-10'),
    (8, 1, 1, 6, '7.45', '2023-03-11');
