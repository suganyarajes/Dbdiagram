# Guvi Zen Class Database Model

This project contains the database model for the Guvi Zen Class. It includes tables for users, batches, problems, codekata, topics, attendance, tasks, and zen_class.

## Project Structure

The database is modeled using PostgreSQL. Below are the tables and their relationships:

### Tables

1. **users**
   - `id` (Primary Key)
   - `userName`: Name of the user.
   - `userEmail`: Email of the user (unique).
   - `userContactDetails`: Contact details of the user.
   - `userBatchId`: Foreign key referencing `Batch.id`.
   - `feesPaid`: Boolean indicating if the fees are paid.
   - `placementEnabled`: Boolean indicating if placement is enabled.
   - `userPrimaryLanguage`: Primary language of the user.
   - `userSecondaryLanguage`: Secondary language of the user.
   - `isCourseRestarted`: Boolean indicating if the course is restarted.
   - `userRole`: Role of the user.

2. **Batch**
   - `id` (Primary Key)
   - `batchName`: Name of the batch.
   - `batchStartTiming`: Start time of the batch.
   - `batchEndTiming`: End time of the batch.
   - `batchCourse`: Course name of the batch.
   - `mentorId`: ID of the mentor.
   - `batchCoordinatorId`: ID of the batch coordinator.
   - `studentCoordinatorId`: ID of the student coordinator.
   - `closureDate`: Closure date of the batch.
   - `batchStrength`: Strength of the batch.

3. **Problems**
   - `id` (Primary Key)
   - `problemName`: Name of the problem.
   - `problemStatement`: Statement of the problem.
   - `problemDifficultyLevel`: Difficulty level of the problem.
   - `problemCompletionPoints`: Completion points of the problem.

4. **Codekata**
   - `id` (Primary Key)
   - `problemId`: Foreign key referencing `Problems.id`.
   - `userId`: Foreign key referencing `users.id`.
   - `createdOn`: Timestamp when the codekata was created.
   - `updatedOn`: Timestamp when the codekata was last updated.
   - `progress`: Progress of the codekata.
   - `earnedPoints`: Points earned from the codekata.

5. **Topics**
   - `id` (Primary Key)
   - `topicName`: Name of the topic.
   - `topicContent`: Content of the topic.
   - `topicPreread`: Preread material for the topic.
   - `topicDate`: Date of the topic.
   - `topicActivity`: Activity associated with the topic.
   - `topicTags`: Tags associated with the topic.
   - `topicTimelineId`: Foreign key referencing `zen_class.day`.
   - `topicType`: Type of the topic (Regular/Additional).
   - `topicTaskId`: Foreign key referencing `Tasks.id`.

6. **Attendance**
   - `id` (Primary Key)
   - `batchId`: Foreign key referencing `Batch.id`.
   - `userId`: Foreign key referencing `users.id`.
   - `isPresent`: Boolean indicating if the user is present.
   - `taskId`: Foreign key referencing `Tasks.id`.
   - `date`: Date of the attendance.

7. **Tasks**
   - `id` (Primary Key)
   - `student_id`: Foreign key referencing `users.id`.
   - `day`: Foreign key referencing `zen_class.day`.
   - `task_completion`: Status of task completion.

8. **zen_class**
   - `day` (Primary Key)
   - `topic`: Topic covered on the day.
   - `task`: Task assigned on the day.
   - `recorded_link`: Link to the recorded session.
   - `mentor`: Mentor for the session.

## How to Use

1. Clone the repository:
   ```sh
   git clone https://github.com/suganyarajes/Dbdiagram.git
   cd guvi-zen-class-db
