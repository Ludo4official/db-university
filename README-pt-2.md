1. Contare quanti iscritti ci sono stati ogni anno
SELECT COUNT(`id`) AS `num_studenti`, YEAR(`enrolment_date`) AS `anno_di_iscrizione`
FROM `students`
GROUP BY `anno_di_iscrizione`;

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
SELECT COUNT(`id`) AS `num_insegnanti`, (`office_address`) AS `ufficio`
FROM `teachers`
GROUP BY `ufficio`;

3. Calcolare la media dei voti di ogni appello d'esame
SELECT AVG(`vote`) AS `media_voto`, `exam_id`
FROM `exam_student`
GROUP BY `exam_id`;

4. Contare quanti corsi di laurea ci sono per ogni dipartimento
SELECT COUNT(`id`), `department_id`
FROM `degrees`
GROUP BY `department_id`;






1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
SELECT `students`.* 
FROM `students`
INNER JOIN `degrees`
ON `students`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = "Corso di Laurea in Economia";


2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
SELECT `degrees`.* 
FROM `degrees`
INNER JOIN `departments`
ON `degrees`.`department_id` = `departments`.`id`
WHERE `departments`.`name` = "Dipartimento di Neuroscienze" 
AND `degrees`.`level` = "magistrale";

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
SELECT `courses`.`name`, `courses`.`period`,`courses`.`year`,`courses`.`cfu`, `courses`.`website`, `course_teacher`.`teacher_id` AS 'ID Insegnante'
FROM `course_teacher`
INNER JOIN `courses`
ON `course_teacher`.`course_id` = `courses`.`id`
WHERE `teacher_id` = 44;

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il
relativo dipartimento, in ordine alfabetico per cognome e nome
SELECT `students`.`name` AS `nome studente`, `students`.`surname` AS `cognome studente`,`degrees`.`name` AS `corso di laurea`, `departments`.`name` AS `dipartimento`, `students`.`registration_number` AS 'Matricola'
FROM `students`
INNER JOIN `degrees`
ON `students`.`degree_id` = `degrees`.`id`
INNER JOIN `departments`
ON `degrees`.`department_id` = `departments`.`id`  
ORDER BY `students`.`surname`,`students`.`name`;

5. BONUS: Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

6. BONUS: Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

7. BONUS: Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per
superare ciascuno dei suoi esami


