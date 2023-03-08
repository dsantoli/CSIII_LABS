# CSIII_LABS
All labs from CS III 

# Lab 1 Procedural Diff
The project is due in one week. Specifically, it is due by the midnight on the day of the next lab.
Implement the lab using procedural programming techniques only. That is, you are not allowed to define classes or objects.

Diff. Implement a program that compares two text files character-by-character. The program should output the line numbers that contain different characters and the place where the two lines start to differ. The difference is denoted by ^ (caret) character. If both files are identical, the program should output nothing.

File lengths may differ. If one file is shorter than the other, the shorter file is assumed to have empty lines, i.e. the extra lines of the longer file are considered different from the empty lines of the shorter file.

The file names should be passed as arguments on the command line. Assume the files exist. Assume the file names are the same length. If your program is not invoked with two arguments, it should print an error message and quit. The program operation should look like this:

	prompt% diff file1.txt file2.txt

	file1.txt: 20: Hello
	file2.txt: 20: Hallo
                        ^
	file1.txt: 25: World????
	file2.txt: 25: World!
                            ^
where 20 and 25 are line numbers.
You are allowed to use getline() and string comparison functions in the implementation of this project.
Milestone. Code that inputs two lines from two different files and determines whether they are the same.

Hint. The command line arguments are input as C-style strings arguments to main(). See this program for an example of handling them.

To configure command-line arguments for an MS Visual Studio project, right-click Solution Explorer, select "properties" from the drop-down menu, go to Configuration Properties Debugging and set "Command Arguments" in the properties list.

To create a string of spaces of a particular length use this form of initialization: string spaceString(length, ' '); or
use assign operator: spaceString.assign(length, ' ');


# Lab 2 Word Count
The project is due in one week: by the midnight on the day of the next lab.
Implement a program that reads in a text file, counts how many times each word occurs in the file and outputs the words (and counts) in the increasing order of occurrence, i.e. the counts need to be output in sorted order: rare words first. Word is any sequence of alphanumeric characters separateed by whitespace or punctuation marks. Whitespace and punctuation marks are to be discarded. That is, the punctuation marks should not be counted either as a part of the word or as a separate word. You are free to make your program case sensitive (Hello and hello are counted as separate words) or case insensitive. File name is supplied on command line. You are to use the following classes.

class WordOccurrence {
public:
    WordOccurrence(const string& word="", int num=0);
    bool matchWord(const string &); // returns true if word matches stored
    void increment(); // increments number of occurrences
    string getWord() const; 
    int getNum() const;

private:
    string word_;
    int num_;
};

class WordList{
public:
    // add copy constructor, destructor, overloaded assignment

    // implement comparison as friend
    friend bool equal(const WordList&, const WordList&);

    void addWord(const string &);
    void print();
private:
    WordOccurrence *wordArray_; // a dynamically allocated array of WordOccurrences
                                // may or may not be sorted
    int size_;
};

Using vectors is not allowed. You may use standard sorting algorithms or implement insertion sort form scratch. For the second class (WordList), implement a copy constructor (implementing deep copy), destructor and an overloaded assignment (either classical or copy-and-swap). Make sure your class works correctly with the following code. For your constructors, use member initialization lists where possible, use default values for function parameters where appropriate. Enhance class interface if necessary.
Milestone. Code that inputs a file and prints a list of words (possibly repeating).

Hint: you can use ctype functions to check if a character is alphanumeric. Here is an example use.


# Lab 3 Templated List
The project is due in one week: by the midnight on the day of the next lab. Make sure to include your name in comments of the source files.
Modify the list template example as follows. Create a new templated class Collection that contains this list as a dynamically allocated member, i.e, the list contains a pointer to the first element.

You are not allowed to use STL containers. You are not allowed to use double-linked list. That is, you should use single-liked list only as in the original code. The class has to implement the following methods:

add(): takes an item as the argument and adds it to the collection, does not check for duplicates. You may implement it so that add() appends it either in the front or in the back of the list.
remove(): takes an item as the argument and removes all instances of this item from the collection. The removed nodes should be properly deallocated.
last(): returns the last item added to the collection.
print(): prints all items in the collection. The printout does not have to be in order.
bool equal(const Collection&, const Collection&) : compares two collections for equality. Implement as a friend function. You may implement it only as a specialized template. You may not implement it as a general template. You may not inline friend function definition inside the class template definition. See this for examples.
Make sure that your templated list operates correctly with the following code.

Templated member functions should be implemented out-of-line (outside the class)

You do not have to implement the big three functions (copy constructor, destructor, overloaded assignment). But if you do, you have to implement all three.

Milestone. Collection that successfully implements add().


# Lab 4 Roster with Class Schedule
The project is due in one week: by the midnight on the day of the next lab. Make sure to include your name in comments of the source files.
The project contains two parts.

Recode the roster example we studied in class such that it lists the classes each student is enrolled in. Example roster files are here. Here is an example printout:
All Students
First name Last name:  courses enrolled
Kathleen Anderson: CS1   CS3  CS4
Gerald Edwards: CS1   CS2 CS3
Mary Price: CS1
...
Here is the output for the above example roster files.
The container of the master student roster should be modified as follows: the vector (or other sequential container) should contain student entries. Each entry is a linked list (or other sequential container) where the first entry is the first (or last) name, followed by entries of the courses the student is enrolled in. You are not allowed to use associative containers. The advisable structures are as follows: vector<list<string>> studentEntries or list<list<string>> studentEntries

The printed out list may be tab-separated. You may assume that the text file structure is: one name per line; the line contains a first name followed by last name separated by white space. Each student has exactly two names: first and last (no middle names). The course name is the file name without the extension.

Repeat the assignment for the object-oriented version of the code shown here. You need to modify the class Student to include a list of classes the student is enrolled in.
In this assignment, implement a move constructor and demonsrate its operation in your code. Refer to this example for move semantics implementation.

Milestone: Complete the first part of the project.
	

# Lab 5 Roster With Class Schedule, Associative, Set of Students
The project is due in one week: by the midnight on the day of the next lab. Make sure to include your name in comments of the source files.
Recode the roster example we studied in class such that it prints the list of classes each student is enrolled in. Here is an example printout:
All Students
First name Last name:  courses enrolled 
Kathleen Anderson: CS1   CS3  CS4
Gerald Edwards: CS1   CS2 CS3
Mary Price: CS1
...
Here is the output for the above example roster files.
The project should be done using associative containers and class Student to hold the name of the student. Specifically, you need to use a map keyed by the class Student while value could be a list of classes the student is enrolled in. The map should be the ordered map. That is, the data structure to be used in as follows: map<Student, list<string>>

Recode the roster example so that it prints all the students currently enrolled in at least one course. That is, enrolled in a course and are not in dropout list. The name of each enrolled student has to be printed exactly once. You have to use this data structure: set<Student>. Refer to this set example for guidance. Here is an example printout:
Currently Enrolled Students
Kathleen Anderson
Gerald Edwards
Mary Price
...
Milestone: For the first assignment, print a master list of students (without classes they are enrolled in).
	
	
# Lab 6 Fruit Processing, Container Adapters, Multimaps, STL Algorithms
The project is due in one week: by the midnight on the day of the next lab. Make sure to include your name in comments of the source files. The project contains four parts:
Lemons (container adapters) Recode lemon picking example to use the priority queue container adapter instead of a hand-written loop.
Oranges (multimaps, emplace) Recode orange selection example such that it uses a multimap instead of vector to store fruit as well as upper_bound(), lower_bound() functions and emplace() to populate the multimap.
Apples (algorithms I) Recode apple sorting examples such that they use suggested STL algorithms instead of hand-written loops.
Peaches (algorithms II) Recode peach jamming example to use suggested STL algorithms instead of hand-written loops.
Milestone: Implement the first assignment.

Hint: Refer to this example for priority queue usage.
	

# Lab 7 Updating Hash Container
The project is due in one week: by the midnight on the day of the next lab. Make sure to include your name in comments of the source files.
Use the implementation of the basic hashmap template that we studied and do the following modifications:

modify the implementation of insert() so that it provides "safe insert", i.e.: returns a pair: <pointer, result>, where
pointer is a pointer to the newly inserted value or the old value with the same key
result is a boolean value which is true if the element is inserted
on the basis of your updated insert() implementation, modify the implementation of the overloaded indexing operator [] to eliminate inefficient second invocation of find(). That is, in your implementation, find() should only be invoked once.
modify the implementation of erase() so that it returns a pair <pointer, result>, where
pointer is a pointer to the element past one erased. Note that if the next element in a different bucket, it should still be returned. In case the element with the key specified to erase() does not exist, the value of the returned pointer is unspecified. If erase() removes the last element of the container (the last element of the list of the last bucket), then erase() should return nullptr.
result is a boolean value which is true if the element is successfully erased; result is false if the element with the specified key is not present in the container.
implement void rehash(size_t n) sets the number of buckets in the container to n. Note that the existing elements need to be re-arranged according to their new hash value. Note also that Hash: the object that provides hashing, needs to be updated to contain the new number of buckets. If the parameter n is smaller than the current number of buckets, no actions need to be taken.
Provide test code that declares and populates a container and then demonstrates the operation of the functions you implemented.

Here is an example test code that your implementation should work with.

Milestone: insert() modification.
	
# Lab 8
