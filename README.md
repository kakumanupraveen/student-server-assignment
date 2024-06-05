# student-server-assignment
# Student Server Assignment  This project is a basic Node.js HTTP server that returns student data based on the provided student ID.  ## How to Run  1. Ensure you have Node.js installed on your machine. 2. Clone the repository:    ```sh    git clone https://github.com/your-username/student-server-assignment.git

https://github.com/kakumanupraveen/student-server-assignment
code:

const http = require('http');
const url = require('url');

// Define student data
const students = {
    11111: { studentId: 11111, studentName: 'Bruce Lee', score: 84 },
    22222: { studentId: 22222, studentName: 'Jackie Chen', score: 93 },
    33333: { studentId: 33333, studentName: 'Jet Li', score: 88 }
};

// Create an HTTP server
const server = http.createServer((req, res) => {
    const queryObject = url.parse(req.url, true).query;
    const studentId = Number(queryObject.student_id); // Convert student_id to a number

    // Check if student ID exists in the data
    if (studentId && students[studentId]) {
        res.writeHead(200, { 'Content-Type': 'application/json' });
        res.end(JSON.stringify(students[studentId]));
    } else {
        res.writeHead(404, { 'Content-Type': 'application/json' });
        res.end(JSON.stringify({ error: 'Student not found' }));
    }
});


google slides link
https://docs.google.com/presentation/d/1QLANYD4dfyMhpzE5Ft9OuFLNd49FQvLLy9kk-8qzOPc/edit#slide=id.p

// Start the server
const port = 8000;
server.listen(port, () => {
    console.log(`Server running at http://localhost:${port}/`);
});
