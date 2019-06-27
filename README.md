# World Cup shows which nations back women's soccer — and which don't

France is hosting 24 teams for the Women's World Cup. Though the athletes play professionally in 34 countries, some leagues are better represented than others. Where are conditions for women's football best — and why? In this repository, you will find the methodology, data and code behind the two stories that came out of this analysis.

**Read the full article on DW:** [English](https://www.dw.com/a-49359480) | [German](https://www.dw.com/a-49359448)

*Story by:* [Kira Schacht](https://twitter.com/daten_drang)


# Files

`FWWC 1995-2019 squad lists.xlsx`		Main data file containing squad lists of all players from FIFA Women's World Cups from 1995 to 2019.

`data/...`								Source PDFs with the squad lists.


# Dataset description

| Column name      | Type   | Description                                              | Notes                                                            |
|------------------|--------|----------------------------------------------------------|------------------------------------------------------------------|
| year             | number | Year                                                     |                                                                  |
| edition          | text   | Host country                                             |                                                                  |
| team             | text   | National team                                            | [Country names as used by FIFA](https://www.fifa.com/associations/) |
| number           | number | Shirt number                                             |                                                                  |
| name             | text   | FIFA popular name                                        | also FIFA display name                                           |
| last name        | text   | Last name of player                                      |                                                                  |
| first name       | text   | First name of player                                     |                                                                  |
| shirt name       | text   | Shirt name of player                                     |                                                                  |
| born             | date   | Date of birth                                            | DD.MM.YY                                                         |
| position         | text   | Position                                                 | GK: Goalkeeper, DF: Defender, MF: Midfielder, FW: Forward, Coach |
| club             | text   | Club the player was employed by at the time              |                                                                  |
| clubcountry_code | text   | 3-letter country code                                    | [Country codes as used by FIFA](https://www.fifa.com/associations/) |
| clubcountry      | text   | Name of the country the club is in                       | [Country names as used by FIFA](https://www.fifa.com/associations/) |
| club = team      | number | Are clubcountry and team the same?                       | 0: no1: yes                                                      |
| height           | number | Height of player in cm                                   |                                                                  |
| weight           | number | Weight of player in kg                                   |                                                                  |
| caps             | number | Total number of appearances during that FWWC             |                                                                  |
| goals            | number | Total number of goals the player scored during that FWWC |                                                                  |


# Methodology


## Sources

FIFA uploads tabular squad lists from 2019 back to 2007. For the years before that, the squads are listed in the technical reports published after the World Cup. The 2003 edition is available online, FIFA provided the others as PDFs. You can find the PDF files containing the lists in the `data` folder. Here are the file names and links for the datasets.

| Year | Place   | File Name                                                     | Link                                                                                     |
|------|---------|---------------------------------------------------------------|------------------------------------------------------------------------------------------|
| 1995 | Sweden  | FWWC_1995_Statistics - FIFA Women's World Cup Sweden 1995.PDF | see file in `data` folder                                                                |
| 1999 | USA     | FWWC_1999_Statistics - FIFA Women's World Cup USA 1999.PDF    | see file in `data` folder                                                                |
| 2003 | USA     | FWWC_2003_usa-2003-500807.pdf                                 | [Link](https://resources.fifa.com/image/upload/usa-2003-500807.pdf?cloudid=zb4xdbbsb9igeycudpmo) |
| 2007 | China   | FWWC_2007_SquadLists.pdf                                      | [Link](https://tournament.fifadata.com/document/FWWC/2007/pdf/FWWC_2007_SquadLists.pdf)          |
| 2011 | Germany | FWWC_2011_SquadLists.pdf                                      | [Link](https://tournament.fifadata.com/documents/FWWC/2011/pdf/FWWC_2011_SQUADLISTS.PDF)         |
| 2015 | Canada  | FWWC_2015_SquadLists.pdf                                      | [Link](https://tournament.fifadata.com/document/FWWC/2015/pdf/FWWC_2015_SquadLists.pdf)          |
| 2019 | France  | FWWC_2019_SQUADLISTS.PDF                                      | [Link](https://tournament.fifadata.com/documents/FWWC/2019/pdf/FWWC_2019_SQUADLISTS.PDF)         |


## Data cleaning

We converted the PDF files into the Excel table uploaded here manually:

- Used [Tabula](https://tabula.technology/) to extract tables from PDFs.

- Used Excel and [Sublime](https://www.sublimetext.com/) (for regular expression matching) to clean and standardize resulting tables. 