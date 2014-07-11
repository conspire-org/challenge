# Conspire Challenge
--

Thanks for your interest in Conspire and for offering to complete our coding exercise. Our goal is to get to know you, your code and your problem-solving skills while being respectful of your time.

For this exercise, you'll use Ruby on Rails to build a REST API endpoint that reads from flat files stored on Amazon S3 via the S3 REST API and provides structured data to the client.


##Requirements

###Authenticated S3 reads

When a client accesses the /query endpoint, it should read in all of the files in the Amazon S3 bucket conspire-challenge and return their contents as a JSON blob as specified below.

The AWS access key id and secret key will be provided to you over email. To browse the conspire-challenge bucket, log into the AWS console through Conspire's IAM login page via:

    https://726449977433.signin.aws.amazon.com/console 
    username: challenge
    password: domorefaster 
    click on S3 -> conspire-challenge

###Output

The /query endpoint should return a JSON blob consisting of a single, one-dimensional array of "line" objects, each representing one nonempty line of text from the files, with the following properties, all strings:

* **filename**: The name of the S3 object (i.e. file) from which the line came
* **key**: The part of the line preceding the first tab character, without leading or trailing whitespace
* **value**: The remainder of the line, without leading or trailing whitespace

###Sorting

The /query endpoint should accept a single URL parameter, sort, a string of length zero or greater consisting of only the characters f,k and v that will determine the sort order of the returned line objects.

The line objects returned by the /query endpoint should be sorted according to the following rules:

1. If the argument is not provided or is empty, the line objects should be sorted as though a value of fkv had been provided.
1. If the argument is of length 1 or greater, the line objects should be sorted as follows:
  1. If the first character of sort is f, in alphabetical order of filename
  1. If the first character of sort is k, in alphabetical order of key
  1. If the first character of sort is v, in alphabetical order of value
1. Line objects with identical values for the property indicated by the first character of sort should be sorted as though a sort value had been provided equal to sort[1..-1].

So, for example, a call to <http://localhost:3000/query?sort=kv> should return a JSON array of objects sorted by key, then value, then filename, in descending order of precedence. Note the inclusion of filename as a sort parameter under rule 3 above.

## Guidelines

Feel free to search the web, read online documentation, etc. the way you would if this were a real project. In particular, if you aren't familiar with Ruby, you may find it useful to bookmark www.ruby-doc.org.

Send us an email when you're done and we'll pull down your github repository, verify the output and take a close look at your code.

Thanks for giving us this chance to get to know you and your code!
