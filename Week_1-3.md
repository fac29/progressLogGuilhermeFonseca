## Guidance

Answer the following questions considering the learning outcomes for

- [Week 1](https://learn.foundersandcoders.com/course/syllabus/developer/project-1-server/learning-outcomes/)
- [Week 2](https://learn.foundersandcoders.com/course/syllabus/developer/project-1-frontend/learning-outcomes/)
- [Week 3](https://learn.foundersandcoders.com/course/syllabus/developer/project-1-test-deploy/learning-outcomes/)

Make sure to record evidence of your processes. You can use code snippets, screenshots or any other material to support your answers.

Do not fill in the feedback section. The Founders and Coders team will update this with feedback on your progress.

## Assessment

### 1. Show evidence of some of the learning outcomes you have achieved this week.

> **[Learning outcomes...]**  
> Backend Development using TypeScript and Express:

TypeScript and Express:

Develop a server using Express and TypeScript for backend applications (K9, S1, S11, S12)
RESTFUL APIs: Construct and implement RESTful APIs effectively (S1, S11, S12, S16)

Evidence:

Database schema design (

    app.delete('/questions/:id', async (req: Request, res: Response) => {
    let id = req.params.id;
    let deleteData = await fsPromises.readFile(library, 'utf8');
    let jsonDeleteData = JSON.parse(deleteData);
    let questionYass = jsonDeleteData.questions.filter(
    (question: Question) => question.id === parseInt(id)
    );
    if (questionYass.length > 0) {
    try {
    let qMatch = jsonDeleteData.questions.filter(
    (question: any) => question.id !== parseInt(id)
    );
    let updatedJsonString = JSON.stringify({ questions: qMatch }, null, ' ');
    await fsPromises.writeFile(library, updatedJsonString);
    console.log('the question has been deleted');
    res.send({ message: 'question has successfully been deleted' });
    } catch (err) {
    console.log(err);
    }
    } else {
    console.log('please revise question id');
    res.send({ message: 'please revise question id' });
    }
    });

)

### 2. Show an example of some of the learning outcomes you have struggled with and/or would like to re-visit.

> [**Learning outcome...**]  
> Node File System:

One of the areas I struggled with is using the Node File System (fs) to set up an interim database. While I managed to get basic operations working, I encountered challenges related to error handling, performance optimization, and ensuring data consistency.

Evidence:

CRUD operations implementation (

    app.put('/reset', async (req: Request, res: Response) => {
    try {
    	let reWriteData = await fsPromises.readFile(library, 'utf8');
    	let jsonReWriteData = JSON.parse(reWriteData);

    	// Loop through each question and reset properties

    	let parsedJsonReWriteData = jsonReWriteData.questions.map(
    		(question: any) => ({
    			...question,
    			favourited: false,
    			completed: false,
    		})
    	);

    	// Rewrite database with updated data
    	let addingFalse = JSON.stringify(
    		{ questions: parsedJsonReWriteData },
    		null,
    		2
    	); // Assuming "questions" is the key for your array of questions
    	await fsPromises.writeFile(library, addingFalse);

    	res.send({ message: 'Favourite has been reset & Completed been reset' });
    } catch (error) {
    	console.error('Error occurred while resetting favourite:', error);
    	res
    		.status(500)
    		.send({ message: 'Error occurred while attempting to reset favourite' });
    }

});

)

## Feedback (For CF's)

> [**Course Facilitator name**]  
> [*What went well*]  
> Made good progress in designing and implementing the database schema and CRUD operations.
> React components and state management and use of useContext API.

> [*Even better if*]
> Improve your testing skills by writing more comprehensive tests and increasing test coverage.
