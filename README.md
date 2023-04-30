Download Link: https://assignmentchef.com/product/solved-csc370-assignment3-imdb-queries
<br>
This assignment will be accepted electronically. See the ‘Submission and Evaluation’ section below for details on the submission process and expected formatting of your answers. For all of the questions below, your answer must be <strong>one </strong>SQL query (including a terminating semicolon) which runs without errors on the studdb1.csc.uvic.ca or studdb2.csc.uvic.ca PostgreSQL database servers. Note that timeout errors (in which the server terminates your query for exceeding the maximum execution time) are considered errors. Queries which have errors or which produce incorrect output will receive a mark of zero. Queries which run without errors and produce the correct output will be marked out of two, with full marks given only to queries that contain no assumptions besides what is given in the question (see the advice sections below for more details).

The ordering of rows in your query result will not be considered during marking (so it is not necessary that your query produce the same row ordering as the model output, just the same set of rows). However, your query must have the same set of columns (with the same names, in the same order) as the model output to be considered correct.

<strong>Question 1</strong>: IMDB Queries

Create queries for each of the data retrieval problems below, using the imdb database. Place your answers in the appropriate positions in the a3q1_queries.txt file. In the questions below, any reference to ‘films’ refers to titles with title_type = ‘movie’.

Hint: When you need the ‘primary name’ of a title, add the following to the WITH clause of your query and then join the resulting primary_names subquery to titles as needed.

primary_names as (select title_id, name as primary_name from title_names where is_primary = true)

For example, the query below uses the ‘primary name’ to find the production year, title ID and duration of all films (title_type = ‘movie’) with primary title ‘The Shining’.

with

primary_names as (select title_id, name as primary_name from title_names where is_primary = true)

select * from

titles

natural join

primary_names

where primary_name = ‘The Shining’ and title_type = ‘movie’; The result of the above query is shown below.

<table width="372">

 <tbody>

  <tr>

   <td width="67"> </td>

   <td colspan="3" width="211">Query Result</td>

   <td width="94"> </td>

  </tr>

  <tr>

   <td width="67">title id</td>

   <td width="71">title type</td>

   <td width="46">year</td>

   <td width="94">length minutes</td>

   <td width="94">primary name</td>

  </tr>

  <tr>

   <td width="67">6812278</td>

   <td width="71">movie</td>

   <td width="46">2017</td>

   <td width="94">136</td>

   <td width="94">The Shining</td>

  </tr>

  <tr>

   <td width="67">81505</td>

   <td width="71">movie</td>

   <td width="46">1980</td>

   <td width="94">146</td>

   <td width="94">The Shining</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>Find the primary name, year and title ID of all titles from the year 1989 with a length of 180 minutes and a title type of ‘tvSpecial’.</li>

</ul>

<table width="400">

 <tbody>

  <tr>

   <td width="287">Expected Query Result</td>

   <td width="46"> </td>

   <td width="67"> </td>

  </tr>

  <tr>

   <td width="287">primary name</td>

   <td width="46">year</td>

   <td width="67">title id</td>

  </tr>

  <tr>

   <td width="287">Survivor Series</td>

   <td width="46">1989</td>

   <td width="67">264059</td>

  </tr>

  <tr>

   <td width="287">Starrcade</td>

   <td width="46">1989</td>

   <td width="67">348114</td>

  </tr>

  <tr>

   <td width="287">The 16th Annual American Music Awards</td>

   <td width="46">1989</td>

   <td width="67">790592</td>

  </tr>

  <tr>

   <td width="287">The 1989 Miss Tennessee Pageant</td>

   <td width="46">1989</td>

   <td width="67">1837666</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>Find the primary name, year and length (in minutes) of all films whose total length in minutes is at least 4320 (72 hours).</li>

</ul>

<table width="302">

 <tbody>

  <tr>

   <td colspan="3" width="302">Expected Query Result</td>

  </tr>

  <tr>

   <td width="162">primary name</td>

   <td width="46">year</td>

   <td width="94">length minutes</td>

  </tr>

  <tr>

   <td width="162">Modern Times Forever</td>

   <td width="46">2011</td>

   <td width="94">14400</td>

  </tr>

  <tr>

   <td width="162">Beijing 2003</td>

   <td width="46">2004</td>

   <td width="94">9000</td>

  </tr>

  <tr>

   <td width="162">Nari</td>

   <td width="46">2017</td>

   <td width="94">6017</td>

  </tr>

  <tr>

   <td width="162">Hunger!</td>

   <td width="46">2015</td>

   <td width="94">6000</td>

  </tr>

  <tr>

   <td width="162">London EC1</td>

   <td width="46">2015</td>

   <td width="94">5460</td>

  </tr>

  <tr>

   <td width="162">The Cure for Insomnia</td>

   <td width="46">1987</td>

   <td width="94">5220</td>

  </tr>

  <tr>

   <td width="162">Ember Glow</td>

   <td width="46">2015</td>

   <td width="94">4980</td>

  </tr>

  <tr>

   <td width="162">Fail</td>

   <td width="46">2016</td>

   <td width="94">4680</td>

  </tr>

  <tr>

   <td width="162">Writing on Snow</td>

   <td width="46">2017</td>

   <td width="94">4320</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>Find the primary name, year and length (in minutes) of all films which have ‘Meryl Streep’ in the cast/crew <strong>and </strong>have a production year of 1985 or earlier. Note: Use the cast_crew table, not the known_for</li>

</ul>

<table width="365">

 <tbody>

  <tr>

   <td colspan="2" width="271">Expected Query Result</td>

   <td width="94"> </td>

  </tr>

  <tr>

   <td width="225">primary name</td>

   <td width="46">year</td>

   <td width="94">length minutes</td>

  </tr>

  <tr>

   <td width="225">Kramer vs. Kramer</td>

   <td width="46">1979</td>

   <td width="94">105</td>

  </tr>

  <tr>

   <td width="225">The Seduction of Joe Tynan</td>

   <td width="46">1979</td>

   <td width="94">108</td>

  </tr>

  <tr>

   <td width="225">The French Lieutenant’s Woman</td>

   <td width="46">1981</td>

   <td width="94">124</td>

  </tr>

  <tr>

   <td width="225">Sophie’s Choice</td>

   <td width="46">1982</td>

   <td width="94">150</td>

  </tr>

  <tr>

   <td width="225">Still of the Night</td>

   <td width="46">1982</td>

   <td width="94">93</td>

  </tr>

  <tr>

   <td width="225">Silkwood</td>

   <td width="46">1983</td>

   <td width="94">131</td>

  </tr>

  <tr>

   <td width="225">Falling in Love</td>

   <td width="46">1984</td>

   <td width="94">106</td>

  </tr>

  <tr>

   <td width="225">Out of Africa</td>

   <td width="46">1985</td>

   <td width="94">161</td>

  </tr>

  <tr>

   <td width="225">Plenty</td>

   <td width="46">1985</td>

   <td width="94">121</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>Find the primary name, year and length (in minutes) of all films which are associated with <strong>both </strong>of the genres ‘Film-Noir’ and ‘Action’. Use the title_genres table to map titles to their genres (titles may have any number of genres).</li>

</ul>

<table width="327">

 <tbody>

  <tr>

   <td colspan="3" width="327">Expected Query Result</td>

  </tr>

  <tr>

   <td width="187">primary name</td>

   <td width="46">year</td>

   <td width="94">length minutes</td>

  </tr>

  <tr>

   <td width="187">Blackmail</td>

   <td width="46">1947</td>

   <td width="94">67</td>

  </tr>

  <tr>

   <td width="187">Dangerous Mission</td>

   <td width="46">1954</td>

   <td width="94">75</td>

  </tr>

  <tr>

   <td width="187">Dick Tracy</td>

   <td width="46">1945</td>

   <td width="94">61</td>

  </tr>

  <tr>

   <td width="187">Dick Tracy vs. Cueball</td>

   <td width="46">1946</td>

   <td width="94">62</td>

  </tr>

  <tr>

   <td width="187">His Kind of Woman</td>

   <td width="46">1951</td>

   <td width="94">120</td>

  </tr>

  <tr>

   <td width="187">Peking Express</td>

   <td width="46">1951</td>

   <td width="94">95</td>

  </tr>

  <tr>

   <td width="187">Road House</td>

   <td width="46">1948</td>

   <td width="94">95</td>

  </tr>

  <tr>

   <td width="187">Rogues’ Regiment</td>

   <td width="46">1948</td>

   <td width="94">86</td>

  </tr>

  <tr>

   <td width="187">Scotland Yard Investigator</td>

   <td width="46">1945</td>

   <td width="94">68</td>

  </tr>

  <tr>

   <td width="187">Sirocco</td>

   <td width="46">1951</td>

   <td width="94">98</td>

  </tr>

  <tr>

   <td width="187">The Pay Off</td>

   <td width="46">1942</td>

   <td width="94">74</td>

  </tr>

  <tr>

   <td width="187">Unmasked</td>

   <td width="46">1950</td>

   <td width="94">60</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>Find the names of all people who were associated as writers or directors (using the appropriate relationship tables) with the movie ‘Die Hard’. There is only one title in the database which is both a movie and has primary name ‘Die Hard’.</li>

</ul>

<table width="165">

 <tbody>

  <tr>

   <td width="165">Expected Query Result</td>

  </tr>

  <tr>

   <td width="165">name</td>

  </tr>

  <tr>

   <td width="165">Jeb Stuart</td>

  </tr>

  <tr>

   <td width="165">John McTiernan</td>

  </tr>

  <tr>

   <td width="165">Roderick Thorp</td>

  </tr>

  <tr>

   <td width="165">Steven E. de Souza</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>Find the primary name, year and length (in minutes) of all films which have <strong>both </strong>‘Tom Hanks’ and ‘Meryl Streep’ as cast/crew. Use the cast_crew table, not the known_for</li>

</ul>

<table width="280">

 <tbody>

  <tr>

   <td colspan="3" width="280">Expected Query Result</td>

  </tr>

  <tr>

   <td width="140">primary name</td>

   <td width="46">year</td>

   <td width="94">length minutes</td>

  </tr>

  <tr>

   <td width="140">Everything Is Copy</td>

   <td width="46">2015</td>

   <td width="94">89</td>

  </tr>

  <tr>

   <td width="140">The Ant Bully</td>

   <td width="46">2006</td>

   <td width="94">88</td>

  </tr>

  <tr>

   <td width="140">The Post</td>

   <td width="46">2017</td>

   <td width="94">115</td>

  </tr>

 </tbody>

</table>

<strong>Question 2</strong>: BC Ferries Queries [16 marks]

The queries you write below should work correctly on all of the BC Ferries databases (ferries_1month, ferries_3months, ferries_6months, ferries_9months, ferries_1year or ferries_3years). For comparison, sample output is shown for both ferries_1month and ferries_3years (but for marking, your query will be compared to a model solution on all of the different databases).

<ul>

 <li>Print the total number of sailings for each route number for all routes in the routes table, including routes that have zero sailings in the dataset.</li>

</ul>

<table width="286">

 <tbody>

  <tr>

   <td colspan="2" width="286">Expected Query Result (ferries 1month)</td>

  </tr>

  <tr>

   <td width="83">route number</td>

   <td width="204">num sailings</td>

  </tr>

  <tr>

   <td width="83">1</td>

   <td width="204">297</td>

  </tr>

  <tr>

   <td width="83">2</td>

   <td width="204">0</td>

  </tr>

  <tr>

   <td width="83">3</td>

   <td width="204">342</td>

  </tr>

  <tr>

   <td width="83">4</td>

   <td width="204">234</td>

  </tr>

  <tr>

   <td width="83">8</td>

   <td width="204">440</td>

  </tr>

  <tr>

   <td width="83">30</td>

   <td width="204">395</td>

  </tr>

  <tr>

   <td colspan="2" width="286">Expected Query Result (ferries 3years)</td>

  </tr>

  <tr>

   <td width="83">route number</td>

   <td width="204">num sailings</td>

  </tr>

  <tr>

   <td width="83">1</td>

   <td width="204">24160</td>

  </tr>

  <tr>

   <td width="83">2</td>

   <td width="204">16895</td>

  </tr>

  <tr>

   <td width="83">3</td>

   <td width="204">17544</td>

  </tr>

  <tr>

   <td width="83">4</td>

   <td width="204">8419</td>

  </tr>

  <tr>

   <td width="83">8</td>

   <td width="204">15419</td>

  </tr>

  <tr>

   <td width="83">30</td>

   <td width="204">15504</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>Print the total number of sailings per vessel in the database, showing only those vessels with at least one sailing.</li>

</ul>

<table width="286">

 <tbody>

  <tr>

   <td colspan="3" width="286">Expected Query Result (ferries 1month)</td>

  </tr>

  <tr>

   <td width="183">vessel name</td>

   <td colspan="2" width="103">count</td>

  </tr>

  <tr>

   <td width="183">Coastal Inspiration</td>

   <td colspan="2" width="103">232</td>

  </tr>

  <tr>

   <td width="183">Coastal Renaissance</td>

   <td colspan="2" width="103">39</td>

  </tr>

  <tr>

   <td width="183">Queen of Alberni</td>

   <td colspan="2" width="103">163</td>

  </tr>

  <tr>

   <td width="183">Queen of Capilano</td>

   <td colspan="2" width="103">440</td>

  </tr>

  <tr>

   <td width="183">Queen of Coquitlam</td>

   <td colspan="2" width="103">68</td>

  </tr>

  <tr>

   <td width="183">Queen of Surrey</td>

   <td colspan="2" width="103">274</td>

  </tr>

  <tr>

   <td width="183">Skeena Queen</td>

   <td colspan="2" width="103">234</td>

  </tr>

  <tr>

   <td width="183">Spirit of British Columbia</td>

   <td colspan="2" width="103">164</td>

  </tr>

  <tr>

   <td width="183">Spirit of Vancouver Island</td>

   <td colspan="2" width="103">94</td>

  </tr>

  <tr>

   <td colspan="3" width="286">Expected Query Result (ferries 3years)</td>

  </tr>

  <tr>

   <td colspan="2" width="190">vessel name</td>

   <td width="96">count</td>

  </tr>

  <tr>

   <td colspan="2" width="190">Bowen Queen</td>

   <td width="96">1268</td>

  </tr>

  <tr>

   <td colspan="2" width="190">Coastal Celebration</td>

   <td width="96">6506</td>

  </tr>

  <tr>

   <td colspan="2" width="190">Coastal Inspiration</td>

   <td width="96">6545</td>

  </tr>

  <tr>

   <td colspan="2" width="190">Coastal Renaissance</td>

   <td width="96">5637</td>

  </tr>

  <tr>

   <td colspan="2" width="190">Mayne Queen</td>

   <td width="96">1</td>

  </tr>

  <tr>

   <td colspan="2" width="190">Queen of Alberni</td>

   <td width="96">6903</td>

  </tr>

  <tr>

   <td colspan="2" width="190">Queen of Capilano</td>

   <td width="96">14277</td>

  </tr>

  <tr>

   <td colspan="2" width="190">Queen of Coquitlam</td>

   <td width="96">6650</td>

  </tr>

  <tr>

   <td colspan="2" width="190">Queen of Cowichan</td>

   <td width="96">7071</td>

  </tr>

  <tr>

   <td colspan="2" width="190">Queen of Cumberland</td>

   <td width="96">974</td>

  </tr>

  <tr>

   <td colspan="2" width="190">Queen of New Westminster</td>

   <td width="96">3966</td>

  </tr>

  <tr>

   <td colspan="2" width="190">Queen of Oak Bay</td>

   <td width="96">6609</td>

  </tr>

  <tr>

   <td colspan="2" width="190">Queen of Surrey</td>

   <td width="96">12759</td>

  </tr>

  <tr>

   <td colspan="2" width="190">Quinitsa</td>

   <td width="96">8</td>

  </tr>

  <tr>

   <td colspan="2" width="190">Skeena Queen</td>

   <td width="96">7312</td>

  </tr>

  <tr>

   <td colspan="2" width="190">Spirit of British Columbia</td>

   <td width="96">5539</td>

  </tr>

  <tr>

   <td colspan="2" width="190">Spirit of Vancouver Island</td>

   <td width="96">5916</td>

  </tr>

  <tr>

   <td width="183"></td>

   <td width="7"></td>

   <td width="96"></td>

  </tr>

 </tbody>

</table>

<ul>

 <li>Print the route number and number of vessels serving that route for every route which was served by at least two vessels (that is, all routes for which at least two distinct vessels each had at least one sailing)</li>

</ul>

<table width="286">

 <tbody>

  <tr>

   <td colspan="2" width="286">Expected Query Result (ferries 1month)</td>

  </tr>

  <tr>

   <td width="83">route number</td>

   <td width="204">num vessels</td>

  </tr>

  <tr>

   <td width="83">1</td>

   <td width="204">3</td>

  </tr>

  <tr>

   <td width="83">3</td>

   <td width="204">2</td>

  </tr>

  <tr>

   <td width="83">30</td>

   <td width="204">2</td>

  </tr>

  <tr>

   <td colspan="2" width="286">Expected Query Result (ferries 3years)</td>

  </tr>

  <tr>

   <td width="83">route number</td>

   <td width="204">num vessels</td>

  </tr>

  <tr>

   <td width="83">1</td>

   <td width="204">6</td>

  </tr>

  <tr>

   <td width="83">2</td>

   <td width="204">5</td>

  </tr>

  <tr>

   <td width="83">3</td>

   <td width="204">6</td>

  </tr>

  <tr>

   <td width="83">4</td>

   <td width="204">5</td>

  </tr>

  <tr>

   <td width="83">8</td>

   <td width="204">2</td>

  </tr>

  <tr>

   <td width="83">30</td>

   <td width="204">6</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>For each route which appears at least once in the sailings table, print the route number and the name and production year of the oldest vessel(s) on the route. Note that there may be multiple vessels tied for oldest (each should be printed separately). Hint: You will likely need a join on a subquery.</li>

</ul>

<table width="337">

 <tbody>

  <tr>

   <td width="4"> </td>

   <td colspan="5" width="337">Expected Query Result (ferries 1month)</td>

   <td width="4"> </td>

  </tr>

  <tr>

   <td width="4"> </td>

   <td colspan="2" width="83">route number</td>

   <td width="183">vessel name</td>

   <td colspan="2" width="71">year built</td>

   <td width="4"> </td>

  </tr>

  <tr>

   <td width="4"> </td>

   <td colspan="2" width="83">1</td>

   <td width="183">Spirit of British Columbia</td>

   <td colspan="2" width="71">1993</td>

   <td width="4"> </td>

  </tr>

  <tr>

   <td width="4"> </td>

   <td colspan="2" width="83">3</td>

   <td width="183">Queen of Coquitlam</td>

   <td colspan="2" width="71">1976</td>

   <td width="4"> </td>

  </tr>

  <tr>

   <td width="4"> </td>

   <td colspan="2" width="83">4</td>

   <td width="183">Skeena Queen</td>

   <td colspan="2" width="71">1997</td>

   <td width="4"> </td>

  </tr>

  <tr>

   <td width="4"> </td>

   <td colspan="2" width="83">8</td>

   <td width="183">Queen of Capilano</td>

   <td colspan="2" width="71">1991</td>

   <td width="4"> </td>

  </tr>

  <tr>

   <td width="4"> </td>

   <td colspan="2" width="83">30</td>

   <td width="183">Queen of Alberni</td>

   <td colspan="2" width="71">1976</td>

   <td width="4"> </td>

  </tr>

  <tr>

   <td colspan="7" width="344">Expected Query Result (ferries 3years)</td>

  </tr>

  <tr>

   <td colspan="2" width="83">route number</td>

   <td colspan="3" width="190">vessel name</td>

   <td colspan="2" width="71">year built</td>

  </tr>

  <tr>

   <td colspan="2" width="83">1</td>

   <td colspan="3" width="190">Queen of New Westminster</td>

   <td colspan="2" width="71">1964</td>

  </tr>

  <tr>

   <td colspan="2" width="83">2</td>

   <td colspan="3" width="190">Queen of Coquitlam</td>

   <td colspan="2" width="71">1976</td>

  </tr>

  <tr>

   <td colspan="2" width="83">2</td>

   <td colspan="3" width="190">Queen of Cowichan</td>

   <td colspan="2" width="71">1976</td>

  </tr>

  <tr>

   <td colspan="2" width="83">3</td>

   <td colspan="3" width="190">Bowen Queen</td>

   <td colspan="2" width="71">1965</td>

  </tr>

  <tr>

   <td colspan="2" width="83">4</td>

   <td colspan="3" width="190">Bowen Queen</td>

   <td colspan="2" width="71">1965</td>

  </tr>

  <tr>

   <td colspan="2" width="83">4</td>

   <td colspan="3" width="190">Mayne Queen</td>

   <td colspan="2" width="71">1965</td>

  </tr>

  <tr>

   <td colspan="2" width="83">8</td>

   <td colspan="3" width="190">Bowen Queen</td>

   <td colspan="2" width="71">1965</td>

  </tr>

  <tr>

   <td colspan="2" width="83">30</td>

   <td colspan="3" width="190">Queen of New Westminster</td>

   <td colspan="2" width="71">1964</td>

  </tr>

  <tr>

   <td width="4"></td>

   <td width="77"></td>

   <td width="4"></td>

   <td width="178"></td>

   <td width="4"></td>

   <td width="67"></td>

   <td width="4"></td>

  </tr>

 </tbody>

</table>

<ul>

 <li>List all vessels which used any port (source or destination) that was at any time used (as either source or destination) by the vessel ‘Coastal Renaissance’. The result should contain the Coastal Renaissance itself. Remember not to make any assumptions about the data.</li>

</ul>

<table width="286">

 <tbody>

  <tr>

   <td width="286">Expected Query Result (ferries 1month)</td>

  </tr>

  <tr>

   <td width="286">vessel name</td>

  </tr>

  <tr>

   <td width="286">Coastal Inspiration</td>

  </tr>

  <tr>

   <td width="286">Coastal Renaissance</td>

  </tr>

  <tr>

   <td width="286">Queen of Alberni</td>

  </tr>

  <tr>

   <td width="286">Skeena Queen</td>

  </tr>

  <tr>

   <td width="286">Spirit of British Columbia</td>

  </tr>

  <tr>

   <td width="286">Spirit of Vancouver Island</td>

  </tr>

  <tr>

   <td width="286">Expected Query Result (ferries 3years)</td>

  </tr>

  <tr>

   <td width="286">vessel name</td>

  </tr>

  <tr>

   <td width="286">Bowen Queen</td>

  </tr>

  <tr>

   <td width="286">Coastal Celebration</td>

  </tr>

  <tr>

   <td width="286">Coastal Inspiration</td>

  </tr>

  <tr>

   <td width="286">Coastal Renaissance</td>

  </tr>

  <tr>

   <td width="286">Mayne Queen</td>

  </tr>

  <tr>

   <td width="286">Queen of Alberni</td>

  </tr>

  <tr>

   <td width="286">Queen of Capilano</td>

  </tr>

  <tr>

   <td width="286">Queen of Coquitlam</td>

  </tr>

  <tr>

   <td width="286">Queen of Cowichan</td>

  </tr>

  <tr>

   <td width="286">Queen of Cumberland</td>

  </tr>

  <tr>

   <td width="286">Queen of New Westminster</td>

  </tr>

  <tr>

   <td width="286">Queen of Oak Bay</td>

  </tr>

  <tr>

   <td width="286">Queen of Surrey</td>

  </tr>

  <tr>

   <td width="286">Quinitsa</td>

  </tr>

  <tr>

   <td width="286">Skeena Queen</td>

  </tr>

  <tr>

   <td width="286">Spirit of British Columbia</td>

  </tr>

  <tr>

   <td width="286">Spirit of Vancouver Island</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>Print the route number and the number of vessels serving that route for every route served by the largest number of distinct vessels (compared to other routes). Notice that there may be multiple routes which are tied for having the most vessels (so the reesult may have multiple rows).</li>

</ul>

<table width="286">

 <tbody>

  <tr>

   <td colspan="2" width="286">Expected Query Result (ferries 1month)</td>

  </tr>

  <tr>

   <td width="83">route number</td>

   <td width="204">num vessels</td>

  </tr>

  <tr>

   <td width="83">1</td>

   <td width="204">3</td>

  </tr>

  <tr>

   <td colspan="2" width="286">Expected Query Result (ferries 3years)</td>

  </tr>

  <tr>

   <td width="83">route number</td>

   <td width="204">num vessels</td>

  </tr>

  <tr>

   <td width="83">1</td>

   <td width="204">6</td>

  </tr>

  <tr>

   <td width="83">3</td>

   <td width="204">6</td>

  </tr>

  <tr>

   <td width="83">30</td>

   <td width="204">6</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>For each port and route number, list the total number of sailings for that route that served that port (as either a source or destination). Only list port/route pairs that have at least one sailing.</li>

</ul>

<table width="286">

 <tbody>

  <tr>

   <td colspan="3" width="286">Expected Query Result (ferries 1month)</td>

  </tr>

  <tr>

   <td width="121">port</td>

   <td width="83">route number</td>

   <td width="83">sailings</td>

  </tr>

  <tr>

   <td width="121">Bowen Island</td>

   <td width="83">8</td>

   <td width="83">440</td>

  </tr>

  <tr>

   <td width="121">Duke Point</td>

   <td width="83">30</td>

   <td width="83">395</td>

  </tr>

  <tr>

   <td width="121">Fulford Harbour</td>

   <td width="83">4</td>

   <td width="83">234</td>

  </tr>

  <tr>

   <td width="121">Horseshoe Bay</td>

   <td width="83">3</td>

   <td width="83">342</td>

  </tr>

  <tr>

   <td width="121">Horseshoe Bay</td>

   <td width="83">8</td>

   <td width="83">440</td>

  </tr>

  <tr>

   <td width="121">Langdale</td>

   <td width="83">3</td>

   <td width="83">342</td>

  </tr>

  <tr>

   <td width="121">Swartz Bay</td>

   <td width="83">1</td>

   <td width="83">297</td>

  </tr>

  <tr>

   <td width="121">Swartz Bay</td>

   <td width="83">4</td>

   <td width="83">234</td>

  </tr>

  <tr>

   <td width="121">Tsawwassen</td>

   <td width="83">1</td>

   <td width="83">297</td>

  </tr>

  <tr>

   <td width="121">Tsawwassen</td>

   <td width="83">30</td>

   <td width="83">395</td>

  </tr>

  <tr>

   <td colspan="3" width="286">Expected Query Result (ferries 3years)</td>

  </tr>

  <tr>

   <td width="121">port</td>

   <td width="83">route number</td>

   <td width="83">sailings</td>

  </tr>

  <tr>

   <td width="121">Bowen Island</td>

   <td width="83">8</td>

   <td width="83">15419</td>

  </tr>

  <tr>

   <td width="121">Departure Bay</td>

   <td width="83">2</td>

   <td width="83">16895</td>

  </tr>

  <tr>

   <td width="121">Duke Point</td>

   <td width="83">30</td>

   <td width="83">15504</td>

  </tr>

  <tr>

   <td width="121">Fulford Harbour</td>

   <td width="83">4</td>

   <td width="83">8419</td>

  </tr>

  <tr>

   <td width="121">Horseshoe Bay</td>

   <td width="83">2</td>

   <td width="83">16895</td>

  </tr>

  <tr>

   <td width="121">Horseshoe Bay</td>

   <td width="83">3</td>

   <td width="83">17544</td>

  </tr>

  <tr>

   <td width="121">Horseshoe Bay</td>

   <td width="83">8</td>

   <td width="83">15419</td>

  </tr>

  <tr>

   <td width="121">Langdale</td>

   <td width="83">3</td>

   <td width="83">17544</td>

  </tr>

  <tr>

   <td width="121">Swartz Bay</td>

   <td width="83">1</td>

   <td width="83">24160</td>

  </tr>

  <tr>

   <td width="121">Swartz Bay</td>

   <td width="83">4</td>

   <td width="83">8419</td>

  </tr>

  <tr>

   <td width="121">Tsawwassen</td>

   <td width="83">30</td>

   <td width="83">15504</td>

  </tr>

  <tr>

   <td width="121">Tsawwassen</td>

   <td width="83">1</td>

   <td width="83">24160</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>For each port, list the route number and number of sailings of the route(s) with the largest number of sailings which served that port (as either source or destination).</li>

</ul>

<table width="286">

 <tbody>

  <tr>

   <td colspan="3" width="286">Expected Query Result (ferries 1month)</td>

  </tr>

  <tr>

   <td width="121">port</td>

   <td width="83">route number</td>

   <td width="83">sailings</td>

  </tr>

  <tr>

   <td width="121">Bowen Island</td>

   <td width="83">8</td>

   <td width="83">440</td>

  </tr>

  <tr>

   <td width="121">Duke Point</td>

   <td width="83">30</td>

   <td width="83">395</td>

  </tr>

  <tr>

   <td width="121">Fulford Harbour</td>

   <td width="83">4</td>

   <td width="83">234</td>

  </tr>

  <tr>

   <td width="121">Horseshoe Bay</td>

   <td width="83">8</td>

   <td width="83">440</td>

  </tr>

  <tr>

   <td width="121">Langdale</td>

   <td width="83">3</td>

   <td width="83">342</td>

  </tr>

  <tr>

   <td width="121">Swartz Bay</td>

   <td width="83">1</td>

   <td width="83">297</td>

  </tr>

  <tr>

   <td width="121">Tsawwassen</td>

   <td width="83">30</td>

   <td width="83">395</td>

  </tr>

  <tr>

   <td colspan="3" width="286">Expected Query Result (ferries 3years)</td>

  </tr>

  <tr>

   <td width="121">port</td>

   <td width="83">route number</td>

   <td width="83">sailings</td>

  </tr>

  <tr>

   <td width="121">Bowen Island</td>

   <td width="83">8</td>

   <td width="83">15419</td>

  </tr>

  <tr>

   <td width="121">Departure Bay</td>

   <td width="83">2</td>

   <td width="83">16895</td>

  </tr>

  <tr>

   <td width="121">Duke Point</td>

   <td width="83">30</td>

   <td width="83">15504</td>

  </tr>

  <tr>

   <td width="121">Fulford Harbour</td>

   <td width="83">4</td>

   <td width="83">8419</td>

  </tr>

  <tr>

   <td width="121">Horseshoe Bay</td>

   <td width="83">3</td>

   <td width="83">17544</td>

  </tr>

  <tr>

   <td width="121">Langdale</td>

   <td width="83">3</td>

   <td width="83">17544</td>

  </tr>

  <tr>

   <td width="121">Swartz Bay</td>

   <td width="83">1</td>

   <td width="83">24160</td>

  </tr>

  <tr>

   <td width="121">Tsawwassen</td>

   <td width="83">1</td>

   <td width="83">24160</td>

  </tr>

 </tbody>

</table>

<h1>Advice: Assume Nothing</h1>

You will lose marks if your query contains any ‘hard-coded’ assumptions about the data in the database other than the assumptions given in the question. For example, suppose you were asked to create the following query.

Using the fruit database, print the first and last names of every customer who placed an order containing the product ‘Pear’, along with the order number of their order. One query which correctly implements the requirements above (and would receive full marks) is select distinct customer_firstname, customer_lastname, order_num from

products

natural join orders

natural join

order_contents

where products.name = ‘Pear’ order by order_num asc;

The result of the above query is shown below.

<table width="293">

 <tbody>

  <tr>

   <td colspan="2" width="227">Query Result</td>

   <td width="66"> </td>

  </tr>

  <tr>

   <td width="117">customer firstname</td>

   <td width="111">customer lastname</td>

   <td width="66">order num</td>

  </tr>

  <tr>

   <td width="117">Franz</td>

   <td width="111">Kafka</td>

   <td width="66">1001</td>

  </tr>

  <tr>

   <td width="117">Fiona</td>

   <td width="111">Framboise</td>

   <td width="66">1002</td>

  </tr>

 </tbody>

</table>

It is possible to write plenty of other queries which produce the same result (and any such query which makes no assumptions about the data would receive full marks). In some cases, it is possible to write a query which takes advantage of properties of the data which cannot generally be assumed. For example, if you happen to know that the product ID number for ‘Pear’ is 2, the query below would produce the same result as above.

<strong>Bad Query 1</strong>:

select distinct customer_firstname, customer_lastname, order_num from

orders

natural join

order_contents

where product_id = 2 order by order_num asc;

Taking the assumptions even further, if you happen to know that the only orders meeting the criteria of the question are orders 1001 and 1002, the query below would produce the correct output as well.

<strong>Bad Query 2</strong>:

select distinct customer_firstname, customer_lastname, order_num from

orders

where order_num = 1001 or order_num = 1002 order by order_num asc;

Both of the queries above would lose marks (and the second bad query would likely receive no marks at all), since both include hard-coded assumptions about the data in the database. If the product ID of Pear were to change, or more orders were added to the database, the two bad queries would no longer work (but the original, correct query would continue to work properly).


