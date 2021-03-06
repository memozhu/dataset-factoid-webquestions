Freebase Branched Relation Paths
================================

This specific dataset records a set of relation paths that connect
the key Freebase concept with some answer of the respective question.
Additionally, it conects the key Freebase conceot with some concept from
question dump if this path share relation with path from key Freebase concept 
to some answer. The dataset contains an attribute **relPaths**, which is
a list of path objects; each path object is represented by an
array-stored tuple of

	[path, nMatches]

with **path** being a list of strings with relation names and
**nMatches** being number of answer matches within this path.

The first two relation represents path from key concept to answer
and first and third relation represents path from key concept to
some other in-question concept.

This data has been generated from the Freebase Google API using following command:

	googleapikey=....
	for split in devtest val trainmodel test; do
		echo $split
		scripts/freebase_relpaths_g.py $split brp $googleapikey
	done

Apikey is the key for google freebase api and can be obtained here: https://console.developers.google.com/
The freebase response is stored into fbconcepts directory into the file named <mid>.json.
If the apikey is not provided then the script tries to read existing JSON freebase data dumps from the directory fbconcepts/.

N.B. as of May 4, the Freebase API accessible via the API key is not available anymore.
The latest version of the fbconcepts/ directory, containing webquestions + moviesF
concepts, is available at:

	http://pasky.or.cz/dev/brmson/fbconcepts-2016-05-04.tar.gz
