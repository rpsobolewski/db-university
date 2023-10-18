GROUP

1 | SELECT COUNT(_) AS `student_count`, YEAR(`enrolment_date`) FROM `students` GROUP BY YEAR(`enrolment_date`);
2 | SELECT COUNT(_) AS `teachers_count`, `office_address` FROM `teachers` GROUP BY `office_address`;
3 | SELECT COUNT(`exam_id`) AS `exams_count`, AVG(`vote`) AS `average_vote` FROM `exam_student` GROUP BY `exam_id`;
4 | SELECT COUNT(\*) AS `degrees_count`, `department_id`, `departments`.`name` AS `department_name` FROM `degrees` JOIN `departments` ON `department_id` = `departments`.`id` GROUP BY `department_id`;

JOINS

1 | SELECT `students`.`name`, `students`.`surname`, `degrees`.`name` AS `degree_name` FROM `students` JOIN `degrees` ON `degree_id` = `degrees`.`id` WHERE `degrees`.`name` = 'Corso di Laurea in Economia';
2 | SELECT `degrees`.`name`, `degrees`.`level`, `departments`.`name` AS `department_name` FROM `degrees` JOIN `departments` ON `department_id` = `departments`.`id` WHERE `departments`.`name` = 'Dipartimento di Neuroscienze' AND `degrees`.`level` = 'Magistrale';
3 | SELECT `courses`.`name` AS `course_name`, `teachers`.`name` AS `teacher_name`, `teachers`.`surname` AS `teacher_surname` FROM `course_teacher` JOIN `courses` ON `course_id` = `courses`.`id` JOIN `teachers` ON `teacher_id` = `teachers`.`id` WHERE `teacher_id` = 44;
4 | SELECT `students`.`name`, `students`.`surname`, `degrees`.`name` AS `degree_name`, `departments`.`name` AS `department_name` FROM `students` JOIN `degrees` ON `degree_id` = `degrees`.`id` JOIN `departments` ON `department_id` = `departments`.`id` ORDER BY `students`.`surname`, `students`.`name` ASC;
5 | SELECT `degrees`.`name` AS `degree_name`, `courses`.`name` AS `course_name`, `teachers`.`name` AS `teacher_name`, `teachers`.`surname` AS `teacher_surname` FROM `course_teacher` JOIN `courses` ON `course_id` = `courses`.`id` JOIN `degrees` ON `degree_id` = `degrees`.`id` JOIN `teachers` ON `teacher_id` = `teachers`.`id` ORDER BY `degrees`.`name` ASC;
6 | SELECT `teachers`.`name` AS `teacher_name`, `teachers`.`surname` AS `teacher_surname`, `departments`.`name` AS `department_name` FROM `course_teacher` JOIN `courses` ON `course_id` = `courses`.`id` JOIN `degrees` ON `degree_id` = `degrees`.`id` JOIN `departments` ON `department_id` = `departments`.`id` JOIN `teachers` ON `teacher_id` = `teachers`.`id` WHERE `departments`.`name` = 'Dipartimento di Matematica' ORDER BY `teachers`.`name`, `teachers`.`surname`;
