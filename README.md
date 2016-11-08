use medialicencinglab;
CREATE TABLE medialicencinglab.ARUser
(
id int primary key ,
first_name varchar(200) NOT NULL,
last_name varchar(200) NOT NULL,
college varchar(200),
level varchar(200),
gender varchar(200),
preference varchar(200),
age int,
major varchar(200),
minor varchar(200),
FOREIGN KEY(id) references User(id) ON DELETE CASCADE ON UPDATE CASCADE);

CREATE TABLE medialicencinglab.Folder
(
id varchar(200),
asset_id varchar(200),
asset_type varchar(100),
primary key (id, asset_id)
);

drop table medialicencinglab.Artist;
drop table medialicencinglab.Genre;
drop table medialicencinglab.Owner;
drop table song;

create table medialicencinglab.song
(asset_id varchar(200) primary key,
 muscian_id varchar(200) references musician(folder_id) ON DELETE CASCADE ON UPDATE CASCADE)
 
alter table user add usertype varchar(20);

create table medialicencinglab.Playlist(
id int primary key,
user_id int,
song_id varchar(200),
foreign key(song_id) references Song(asset_id) ON DELETE CASCADE ON UPDATE CASCADE
);

CREATE TABLE medialicencinglab.Owner
(
id int primary key auto_increment,
song_id varchar(200) not null,
name varchar(200) not null,
divison_of_ownership varchar(50), 
owner_type Enum('WRITER', 'RECORDING') not null,
primary_phone_no varchar(15) not null,
secondary_phone_no varchar(15),
primary_email_id varchar(50) not null,
secondary_email_id varchar(50),
FOREIGN KEY(song_id) references Song(asset_id) ON DELETE CASCADE ON UPDATE CASCADE);

alter table medialicencinglab.Musician
add column gender varchar(200);
alter table medialicencinglab.Musician
add age int;
alter table medialicencinglab.Musician
add folder_id int;
alter table medialicencinglab.Musician
add added_by int;
alter table medialicencinglab.Musician
add constraint foreign key(added_by) references ARUser(id) on delete set null on update cascade;
