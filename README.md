Download Link: https://assignmentchef.com/product/solved-project-2-managing-a-hierarchy-using-a-general-tree
<br>
<h1>Learning Objectives</h1>

Apply object-oriented programming concepts in C


Choose and implement an appropriate internal representation for a specified abstract data type

Design, implement, and use a general tree data structure

Analyze operations for time complexity

<h1>Overview</h1>

Your task for this assignment is to implement a general tree that can store, manipulate, and query the organizational chart for a company. The organizational chart contains the title and full name of every employee in the company. The structure of the chart shows who works for whom within the company. For example, the following organizational chart might represent the fictional company Magic Bags, Incorporated (MBI):

<img decoding="async" data-recalc-dims="1" data-src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2018/03/456.png?w=980&amp;ssl=1" class="aligncenter lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

 <noscript>

  <img decoding="async" class="aligncenter" src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2018/03/456.png?w=980&amp;ssl=1" data-recalc-dims="1">

 </noscript>




<h1>The Organization Tree</h1>

You will store the organization chart as a general tree. You may choose any of the general tree implementations we have discussed in class. Your tree should satisfy the following specifications:

So that we can test your code, we need to know if you will use a TreeNode* (for linked implementations) or an unsigned integer (for array implementations) to point to a TreeNode. In your OrgTree.h file, you should use one of the following two code blocks:

For array-based implementations, you should use:

#define TREENODEPTR unsigned int

#define TREENULLPTR -1

For linked node implementations, you should use:

#define TREENODEPTR TreeNode*

#define TREENULLPTR NULL

Each tree node should store a title and a name. You can use the C++ string class for both of these data elements. (Don’t forget to <sub>#include &lt;string&gt;</sub>)

<sub> void OrgTree::addRoot(title, name)</sub> – Creates a root node for the tree. If the tree already has a root, the entire tree becomes a subtree of the new root.  unsigned int OrgTree::getSize() – Returns the number of employees in the tree.

TREENODEPTR OrgTree::getRoot() – Returns a pointer to the root node in the tree. Depending on your implementation, this function may return a TreeNode* or an unsigned integer that will be used as an array index.

TREENODEPTR OrgTree::leftmostChild(TREENODEPTR node) – Returns a pointer to the leftmost child of the node passed to the function. If the node has no children, returns TREENULLPTR.

TREENODEPTR OrgTree::rightSibling(TREENODEPTR node) – Returns a pointer to the right sibling of the node passed to the function. If the node has no right sibling, returns TREENULLPTR.

void OrgTree::printSubTree(TREENODEPTR subTreeRoot) – print out the subtree starting at the node pointed to by subTreeRoot. This function should use indentation to show the tree structure. For example, if you called printSubTree on the tree shown above, and passed it a pointer to the “VP Sales” node, you would see the following:

VP Sales: Mark Zuckerberg

Director of Marketing: George Lucas

Digital Media Specialist: Al Gore

Head of Television and Print Advertising: George R.R. Martin

Director of Public Relations: Kurt Vonnegut

TREENODEPTR OrgTree::find(title) – returns a TREENODEPTR to the node listing the given title (exact string match with the title string in a TreeNode object). If the title is not found, the function should return TREENULLPTR. For simplicity, you may assume that all titles in the company are unique.

<sub> bool OrgTree::read(filename)</sub> – reads an organization tree from a file. The file will contain one tree node per line, except for lines containing only ‘)’ characters, which mark the ends of subtrees. The organization tree illustrated above would be represented by the file shown below. If the file is found and read successfully, this function should return true. If the file is not found or the file is improperly formatted, the function should return false.

<table width="619">

 <tbody>

  <tr>

   <td width="619">President, George OrwellVP Sales, Mark ZuckerbergDirector of Marketing, George LucasDigital Media Specialist, Al Gore)Head of Television and Print Advertising, George Martin))Director of Public Relations, Kurt Vonnegut))VP Operations, Bill Gates)VP Software Development, Ayn RandMagicBag Team Leader, Wil Wheaton Software Engineer I, Donald Knuth)Software Engineer II, Marvin Minsky))Cloud Development, Bob Ross)))</td>

  </tr>

 </tbody>

</table>

void OrgTree::write(filename) – write out the OrgTree to a file, using the same file format described in the read() function above.

void OrgTree::hire(TREENODEPTR, newTitle, newName) – Hire an employee. The employee should be added to the tree as the last child of the node pointed to by TREENODEPTR.

bool OrgTree::fire(formerTitle) – Fire the employee who’s title matches the argument to this function. If the title is found the employee’s node in the tree is deleted and the function returns true. All employees of the fired employee now work directly for the fired employee’s boss (e.g. all children of the deleted

node become children of the deleted node’s parent). If no match is found the function returns false. For simplicity, you can assume that titles in the company are unique. Note that you cannot fire the root node. If the formerTitle matches the root node, the function should return false.

Your tree should be able to hold any number of employees. If you use an array-based tree implementation, your array must re-size when full.

<h1>Analysis and Documentation</h1>

Each class and function should have appropriate header documentation/comments

Each of the functions specified above must include the asymptotic run time, in Θ(n) notation, for a tree of size n, in the header comment block of the function.

The OrgTree class comment block should include the space requirement for a tree of n employees.