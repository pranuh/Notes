## Create Table

```sql
CREATE TABLE Netflix_Content (
    Show_ID INT PRIMARY KEY,
    Title VARCHAR(200),
    Type VARCHAR(20),
    Director VARCHAR(150),
    Country VARCHAR(100),
    Release_Year INT,
    Rating VARCHAR(20),
    Duration_Min INT,
    Genre VARCHAR(50)
);
```

## Insert 50 Sample Records

```sql
INSERT INTO Netflix_Content
VALUES
(1,'Stranger Things','TV Show','Duffer Brothers','USA',2016,'TV-14',50,'Sci-Fi'),
(2,'Money Heist','TV Show','Alex Pina','Spain',2017,'TV-MA',47,'Crime'),
(3,'Wednesday','TV Show','Tim Burton','USA',2022,'TV-14',45,'Fantasy'),
(4,'Squid Game','TV Show','Hwang Dong-hyuk','South Korea',2021,'TV-MA',55,'Thriller'),
(5,'Extraction','Movie','Sam Hargrave','USA',2020,'R',116,'Action'),
(6,'RRR','Movie','S. S. Rajamouli','India',2022,'PG-13',182,'Action'),
(7,'Delhi Crime','TV Show','Richie Mehta','India',2019,'TV-MA',50,'Crime'),
(8,'The Irishman','Movie','Martin Scorsese','USA',2019,'R',209,'Drama'),
(9,'Kota Factory','TV Show','Raghav Subbu','India',2021,'TV-14',45,'Drama'),
(10,'Leo','Movie','Lokesh Kanagaraj','India',2023,'UA',164,'Action'),
(11,'Lupin','TV Show','Louis Leterrier','France',2021,'TV-14',45,'Crime'),
(12,'Narcos','TV Show','Jose Padilha','Colombia',2015,'TV-MA',49,'Crime'),
(13,'Darlings','Movie','Jasmeet K Reen','India',2022,'UA',133,'Drama'),
(14,'Dark','TV Show','Baran bo Odar','Germany',2017,'TV-MA',52,'Sci-Fi'),
(15,'Jawan','Movie','Atlee','India',2023,'UA',169,'Action'),
(16,'Sacred Games','TV Show','Anurag Kashyap','India',2018,'TV-MA',50,'Crime'),
(17,'Bird Box','Movie','Susanne Bier','USA',2018,'R',124,'Thriller'),
(18,'The Night Agent','TV Show','Shawn Ryan','USA',2023,'TV-MA',48,'Thriller'),
(19,'Khakee','TV Show','Neeraj Pandey','India',2022,'TV-MA',46,'Crime'),
(20,'The Gray Man','Movie','Russo Brothers','USA',2022,'PG-13',129,'Action'),
(21,'Breaking Bad','TV Show','Vince Gilligan','USA',2008,'TV-MA',49,'Crime'),
(22,'Peaky Blinders','TV Show','Steven Knight','UK',2013,'TV-MA',58,'Crime'),
(23,'Ozark','TV Show','Bill Dubuque','USA',2017,'TV-MA',60,'Drama'),
(24,'Lucifer','TV Show','Tom Kapinos','USA',2016,'TV-14',45,'Fantasy'),
(25,'The Witcher','TV Show','Lauren Hissrich','Poland',2019,'TV-MA',60,'Fantasy'),
(26,'All Of Us Are Dead','TV Show','Lee Jae-kyoo','South Korea',2022,'TV-MA',55,'Thriller'),
(27,'Kingdom','TV Show','Kim Seong-hun','South Korea',2019,'TV-MA',50,'Thriller'),
(28,'Maharaja','Movie','Nithilan Swaminathan','India',2024,'UA',142,'Thriller'),
(29,'Animal','Movie','Sandeep Reddy Vanga','India',2023,'A',201,'Action'),
(30,'Pushpa','Movie','Sukumar','India',2021,'UA',179,'Action'),
(31,'Mission Majnu','Movie','Shantanu Bagchi','India',2023,'UA',129,'Action'),
(32,'Haseen Dillruba','Movie','Vinil Mathew','India',2021,'UA',135,'Thriller'),
(33,'Jaane Jaan','Movie','Sujoy Ghosh','India',2023,'UA',139,'Crime'),
(34,'Minnal Murali','Movie','Basil Joseph','India',2021,'UA',158,'Fantasy'),
(35,'The Adam Project','Movie','Shawn Levy','USA',2022,'PG-13',106,'Sci-Fi'),
(36,'Red Notice','Movie','Rawson Marshall','USA',2021,'PG-13',118,'Action'),
(37,'Glass Onion','Movie','Rian Johnson','USA',2022,'PG-13',139,'Mystery'),
(38,'Enola Holmes','Movie','Harry Bradbeer','UK',2020,'PG-13',123,'Mystery'),
(39,'Heartstopper','TV Show','Euros Lyn','UK',2022,'TV-14',35,'Romance'),
(40,'Bridgerton','TV Show','Chris Van Dusen','USA',2020,'TV-MA',60,'Romance'),
(41,'Emily In Paris','TV Show','Darren Star','France',2020,'TV-MA',30,'Romance'),
(42,'Manifest','TV Show','Jeff Rake','USA',2018,'TV-14',43,'Drama'),
(43,'Black Mirror','TV Show','Charlie Brooker','UK',2011,'TV-MA',60,'Sci-Fi'),
(44,'The Crown','TV Show','Peter Morgan','UK',2016,'TV-MA',58,'Drama'),
(45,'Queen Charlotte','TV Show','Shonda Rhimes','USA',2023,'TV-MA',60,'Romance'),
(46,'Fubar','TV Show','Nick Santora','USA',2023,'TV-MA',50,'Action'),
(47,'Wednesday Addams','TV Show','Tim Burton','USA',2022,'TV-14',50,'Fantasy'),
(48,'3 Body Problem','TV Show','David Benioff','USA',2024,'TV-MA',60,'Sci-Fi'),
(49,'Avatar The Last Airbender','TV Show','Albert Kim','USA',2024,'TV-14',55,'Fantasy'),
(50,'The Railway Men','TV Show','Shiv Rawail','India',2023,'TV-14',52,'Drama');
```

### Dataset Statistics

- Total Records: **50**
- Countries: India, USA, UK, France, Spain, Germany, South Korea, Colombia, Poland
- Genres: Action, Crime, Drama, Fantasy, Mystery, Romance, Sci-Fi, Thriller
- Types: Movie, TV Show
- Release Years: 2008–2024
