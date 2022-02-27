# Ad-Movies-Phase-1-Project

JavaScript App that fetches a response from movies.json file and displays the movies in categories. Users can also post reviews and favourite a movie.

## Demo



## Setup

Run this command to get the backend started:

```console
$ json-server --watch movies.json
```

Test your server by visiting this route in the browser:

[http://localhost:3000/movies](http://localhost:3000/movies)

Then, open the `index.html` file on your browser to run the application.


## Core Deliverables

As a user, I can:

1. See the first movie's details, including its **poster, title, release date,
   vote count, popularity etc** when the page loads. You will need to make a GET
   request to the following endpoint to retrieve the film data:

   ```txt
   GET /movies/1

   Example Response:
   {
			"adult": false,
			"backdrop_path": "/iQFcwSGbZXMkeyKrxbPnwnRo5fl.jpg",
			"genre_ids": [
				28,
				12,
				878
			],
			"id": 634649,
			"original_language": "en",
			"original_title": "Spider-Man: No Way Home",
			"overview": "Peter Parker is unmasked and no longer able to separate his normal life from the high-stakes of being a super-hero. When he asks for help from Doctor Strange the stakes become even more dangerous, forcing him to discover what it truly means to be Spider-Man.",
			"popularity": 6990.201,
			"poster_path": "/1g0dhYtq4irTY1GPXvft6k4YLjm.jpg",
			"release_date": "2021-12-15",
			"title": "Spider-Man: No Way Home",
			"video": false,
			"vote_average": 8.3,
			"vote_count": 8415
		}
   ```

2. See a menu of all movies on  the page in the `ul#films`
   element when the page loads. You
   will need to make a GET request to the following endpoint to retrieve the
   film data:

   ```txt
   GET /films

   Example response:
   [
      {
			"adult": false,
			"backdrop_path": "/iQFcwSGbZXMkeyKrxbPnwnRo5fl.jpg",
			"genre_ids": [
				28,
				12,
				878
			],
			"id": 634649,
			"original_language": "en",
			"original_title": "Spider-Man: No Way Home",
			"overview": "Peter Parker is unmasked and no longer able to separate his normal life from the high-stakes of being a super-hero. When he asks for help from Doctor Strange the stakes become even more dangerous, forcing him to discover what it truly means to be Spider-Man.",
			"popularity": 6990.201,
			"poster_path": "/1g0dhYtq4irTY1GPXvft6k4YLjm.jpg",
			"release_date": "2021-12-15",
			"title": "Spider-Man: No Way Home",
			"video": false,
			"vote_average": 8.3,
			"vote_count": 8415
		},
		{
			"adult": false,
			"backdrop_path": "/3G1Q5xF40HkUBJXxt2DQgQzKTp5.jpg",
			"genre_ids": [
				16,
				35,
				10751,
				14
			],
			"id": 568124,
			"original_language": "en",
			"original_title": "Encanto",
			"overview": "The tale of an extraordinary family, the Madrigals, who live hidden in the mountains of Colombia, in a magical house, in a vibrant town, in a wondrous, charmed place called an Encanto. The magic of the Encanto has blessed every child in the family with a unique gift from super strength to the power to heal—every child except one, Mirabel. But when she discovers that the magic surrounding the Encanto is in danger, Mirabel decides that she, the only ordinary Madrigal, might just be her exceptional family's last hope.",
			"popularity": 3561.945,
			"poster_path": "/4j0PNHkMr5ax3IA8tjtxcmPU3QT.jpg",
			"release_date": "2021-11-24",
			"title": "Encanto",
			"video": false,
			"vote_average": 7.8,
			"vote_count": 4723
		}
   ]
   ```

3. Buy a ticket for a movie. After clicking the "Buy Ticket" button, I should
   see the number of available tickets decreasing on the frontend. I should not
   be able to buy a ticket if the showing is sold out (if there are 0 tickets
   available). **No persistence is needed for this feature**.

### Bonus Deliverables

These bonus deliverables are here if you want an extra challenge and won't
affect your score. **Make sure to commit your work to save your progress before
attempting the bonus deliverables!**

1. Click on a movie in the menu to replace the currently displayed movie's
   details with the new movie's details. Note that you may have to make an
   additional GET request to access the movie's details.

2. When a movie is sold out (when there are no available tickets remaining),
   indicate that the movie is sold out by changing the button text to "Sold
   Out". Also update the film item in the `ul#films` menu by adding a class of
   `sold-out` to the film. For reference, here's what the contents of the
   `ul#films` element should look like with a sold out film:

   ```html
   <li class="film item">(Title of film)</li>
   <li class="sold-out film item">(Title of a sold-out film)</li>
   <li class="film item">(Title of film)</div>
   ```

## Extra Bonus

These extra bonus deliverables involve using `fetch` to update data on the
`json-server` backend by using `POST`, `PATCH`, and `DELETE` requests. These are
meant for an extra, extra challenge and won't affect your grade. **Make sure to
commit your work to save your progress before attempting the extra bonus
deliverables!**

1. When a ticket is purchased, persist the updated number of `tickets_sold` on
   the server. Remember, the frontend shows the number of available tickets
   based on the `tickets_sold` and the `capacity`, so only the `tickets_sold`
   should be updated on the backend when a ticket is purchased. You will need to
   make a request that follows this structure:

   ```txt
   PATCH /films/:id

   Request Headers: {
     Content-Type: application/json
   }

   Request Body: {
     "tickets_sold": 28
   }
   ----
   Example Response:
   {
      "id": "1",
      "title": "The Giant Gila Monster",
      "runtime": "108",
      "capacity": 30,
      "showtime": "04:00PM",
      "tickets_sold": 28,
      "description": "A giant lizard terrorizes a rural Texas community and a heroic teenager attempts to destroy the creature.",
      "poster": "https://www.gstatic.com/tv/thumb/v22vodart/2157/p2157_v_v8_ab.jpg"
   }
   ```

2. Delete a film from the server. Add a delete button next to each film in the
   `ul#films` menu. When the button is clicked, remove the film from the list
   and also delete the film on the server:

   ```txt
   DELETE /films/:id

   Example Response:
   {}
   ```
