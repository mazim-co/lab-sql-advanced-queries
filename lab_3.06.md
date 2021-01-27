-- LAB 3.06 SQL Advanced queries
-- LIST EACH pair of actors that have worked together.
	
SELECT fa1.actor_id AS Actor1, fa2.actor_id AS Actor2, fa1.film_id FROM sakila.film_actor fa1
	JOIN sakila.film_actor fa2 ON fa1.actor_id <> fa2.actor_id AND fa1.film_id = fa2.film_id
	JOIN sakila.film f ON f.film_id = fa1.film_id
	JOIN sakila.actor a ON a.actor_id = fa1.actor_id
	HAVING Actor1 AND Actor2 = fa1.film_id;



-- For each film, list actor that has acted in more films.

SELECT concat(a.first_name,' ',a.last_name) AS 'actor', count(film_id) AS 'acted IN # films' FROM sakila.film_actor fa
JOIN sakila.actor a ON a.actor_id = fa.actor_id
GROUP BY fa.actor_id
ORDER BY count(film_id) DESC;