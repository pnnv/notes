1 -> 2 -> 3 -> 4 -> **5** -> 6 -> 7 -> null
									^
				1 -> 2 -> 3 
				
[1, 2, 3, 4, 5, 6, 7]
[1, 2, 3, 5, 6, 7]


```cpp

class Subject {
public:
	string name;
	int id; // index
}

class Student {
public:
	string name;
	string rollNumber;
	int *id;
	
	vector <int> Marks;

	Student() {} // default constructor
	
	Student(string n, string roll, int numOfSubjects) {
		name = n;
		rollNumber = roll;
		Marks.resize(numOfSubjects);
	}

	Student(Student &s2) {
		s2.name = name;
		s2.rollNumber = rollNumber;
		s2.id = new int();
	}

	void setMarks(Subject sub, int marks) {
		Marks[sub.id] = marks;
	}

	double average() {
		double m = 0;
		for(auto i: Marks) {
			m += i;
		}
		m /= double(Marks.size());
		return m;
	}
};



```
