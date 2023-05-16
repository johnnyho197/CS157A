# CS157A
SQL code for Final Project


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
