# Advanced-Mysql

# creating a database with name IMDB
Create database IMDB;
use IMDB;
# creating a table with name movies
create table movies(
movie_id int PRIMARY KEY,
title varchar(50),
director varchar(50),
release_year int,
genre varchar(50)
);
# inserting values into the movies table
insert  into movies (movie_id, title, director, release_year, genre)
Values(1, 'Kanthara', 'Ramesh', 2025, 'Horror');
insert  into movies(movie_id, title, director, release_year, genre)
Values(2,'Bahubali', 'RajaMouli', 2015, 'Historic');
insert  into movies(movie_id, title, director, release_year, genre)
Values(3,'Bahubali-2', 'RajaMouli', 2019, 'Historic');
insert  into movies(movie_id, title, director, release_year, genre)
Values(4, 'Kaidi', 'Lokesh', 2022, 'Thriller');
insert  into movies(movie_id, title, director, release_year, genre)
Values(5, 'Vikram', 'Lokesh Kanagaraj', 2023, 'Thriller');

# creating a table with name media
create table media (
    media_id int AUTO_INCREMENT PRIMARY KEY,
    movie_id int,
    media_type VARCHAR(10),
    media_url VARCHAR(600),
    FOREIGN KEY (movie_id) REFERENCES movies(movie_id)
);

# inserting values into the media table
insert  into media(movie_id,media_type,media_url)
Values(1,'image','Kanthara_poster.com');
insert  into media(movie_id,media_type,media_url)
Values(2,'video','Bahubali_poster.com');

# creating a table with name genre
create table genre(
genre_id int AUTO_INCREMENT PRIMARY KEY,
genre_name VARCHAR(100)
);

# creating a table with name movie_genre
create table movie_genre(
movie_id int,
genre_id int,
foreign key (movie_id) references movies(movie_id),
foreign key (genre_id) references genre(genre_id)
);

# inserting values into the genre table
insert into genre (genre_name)
values
('Action'),
('Drama'),
('Thriller'),
('Historic'),
('Comedy');

# inserting values into the movie_genre table
insert into movie_genre (movie_id, genre_id)
values
(1,1),
(1,2),
(2,1),
(2,3),
(3,3);

# creating a table with name users
create table users (
    user_id int AUTO_INCREMENT PRIMARY KEY,
    user_name VARCHAR(50)
);

# creating a table with name Reviews
create table Reviews(
Review_id int  AUTO_INCREMENT PRIMARY KEY,
movie_id int,
user_id int,
Rating int,
Comments varchar(500),
foreign key (movie_id) references movies(movie_id),
foreign key (user_id) references users(user_id)
);

# inserting values into the users table
insert into users(user_name)
values
('Ramya'),
('Prakash'),
('Hathvik');


# inserting values into the Reviews table
insert into Reviews(movie_id,user_id,Rating,Comments)
values
(1,1,5,'Excellent Movie'),
(2,2,4,'Good for one time watch'),
(2,3,4,'Blockbuster movie');

# creating a table with name artist
create table artist (
    artist_id int AUTO_INCREMENT PRIMARY KEY,
    artist_name VARCHAR(50)
);

# creating a table with name skills
create table skills(
skill_id int AUTO_INCREMENT PRIMARY KEY,
skill_name varchar(50)
);

# creating a table with name artist_skills
create table artist_skills(
artist_id int,
skill_id int,
primary key(artist_id,skill_id),
foreign key (artist_id) references artist(artist_id),
foreign key (skill_id) references skills(skill_id)
);

# inserting values into the artist table
insert into artist(artist_name)
values
('Vijay'),
('siva karthikeyan'),
('Surya');

# inserting values into the skills table
insert into skills(skill_name)
values
('Acting'),
('Dancing'),
('Singing');

# inserting values into the artist_skills table
insert into artist_skills(artist_id,skill_id)
values
(1,2),
(1,3),
(2,3),
(3,2);

# creating a table with name movie_artist_roles
create table movie_artist_roles(
movie_id int,
artist_id int,
role varchar(200),
primary key(movie_id,artist_id,role),
foreign key (movie_id) references movies(movie_id),
foreign key (artist_id) references artist(artist_id)
);

# inserting values into the movie_artist_roles table
insert into movie_artist_roles(movie_id, artist_id, role)
values
(1,1,'Actor'),
(1,1,'Singer'),
(1,2,'Director'),
(2,3,'Actor'),
(2,3,'Producer');

# check output of each tables
select* from movies;
select* from media;
select* from genre;
select* from movie_genre;
select* from users;
select* from reviews;
select* from artist;
select* from skills;
select* from artist_skills;
select* from movie_artist_roles;



