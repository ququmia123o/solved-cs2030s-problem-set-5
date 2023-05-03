Download Link: https://assignmentchef.com/product/solved-cs2030s-problem-set-5
<br>
<ol>

 <li>In Java, a Set is a Collection that does not contain duplicate elements (this is in contrast to a List which does allow duplicates). You are given the Point class below:</li>

</ol>

public class Point { private final int x; private final int y;

public Point(int x, int y) { this.x = x; this.y = y;

}

@Override

public String toString() { return “(” + this.x + “, ” + this.y + “)”;

}

}

<ul>

 <li>What is the output of the following program fragment executed in jshell?</li>

</ul>

List&lt;Point&gt; points = new ArrayList&lt;&gt;() points.add(new Point(1, 1)) points.add(new Point(1, 1)) points.indexOf(new Point(1, 1))

<ul>

 <li>By defining an appropriate overriding equals method, demonstrate how the indexOf method can now give the correct behaviour.</li>

 <li>What is the output of the following program fragment executed in jshell?</li>

</ul>

Point p = new Point(1, 1);

Point q = new Point(1, 1); p.equals(q)

Set&lt;Point&gt; set = new HashSet&lt;&gt;()

set.add(p) set.add(q) set

<ul>

 <li>Notice that although equals(q) returns true, the two points are considered distinct by HashSet. How do we ensure that only one point is maintained in the set?</li>

</ul>

<em>Hint: Refer to the definition of the </em>equals <em>method in </em>Object <em>class</em>

<ol start="2">

 <li>The Java Collection&lt;E&gt; interface extends the Iterable&lt;E&gt; interface with the following abstract method declared.</li>

</ol>

Iterator&lt;E&gt; iterator();

<ul>

 <li>Using the methods in the Iterator class, demonstrate how iteration is performed on a List, e.g.</li>

</ul>

List&lt;Point&gt; list = new ArrayList&lt;&gt;(); list.add(new Point(1, 1)); list.add(new Point(2, 2));

<ul>

 <li>How is the use of an Iterator object, different from the following</li>

</ul>

for (Point p : list) {

System.out.println(p);

}

<ol start="3">

 <li>What is the output of the following program fragment? Explain.</li>

</ol>

class A { static void f() throws Exception { try { throw new Exception(); } finally {

System.out.print(“1”);

}

}

static void g() throws Exception { System.out.print(“2”); f();

System.out.print(“3”);

}

public static void main(String[] args) { try {

g();

} catch (Exception e) {

System.out.print(“4”);

}

}

}

<ol start="4">

 <li>You are given two classes MCQ and TFQ that implements a question-answer system:</li>

</ol>

<ul>

 <li>MCQ: multiple-choice questions comprising answers: A B C D E</li>

 <li>TFQ: true/false questions comprising answers: T F</li>

</ul>

class MCQ { String question; char answer;

public MCQ(String question) { this.question = question;

}

void getAnswer() {

System.out.print(question + ” “);

answer = (new Scanner(System.in)).next().charAt(0);

if (answer &lt; ‘A’ || answer &gt; ‘E’) { throw new InvalidMCQException(“Invalid MCQ answer”); }

}

}

class TFQ { String question; char answer;

public TFQ(String question) { this.question = question;

}

void getAnswer() {

System.out.print(question + ” “);

answer = (new Scanner(System.in)).next().charAt(0);

if (answer != ‘T’ &amp;&amp; answer != ‘F’) { throw new InvalidTFQException(“Invalid TFQ answer”); }

}

}

In particular, an invalid answer to any of the questions will cause an exception (either InvalidMCQException or InvalidTFQException) to be thrown.

class InvalidMCQException extends IllegalArgumentException { public InvalidMCQException(String mesg) { super(mesg);

}

}

class InvalidTFQException extends IllegalArgumentException { public InvalidTFQException(String mesg) { super(mesg);

}

}

By employing the various object-oriented design principles, design a <em>more general </em>question-answer class QA that can take the place of both MCQ and TFQ types of questions (and possibly more in future, each with their own type of exceptions).