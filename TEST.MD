Create Table  HAND_STUDENT
(
 STUDENT_NO Varchar(10) Not Null,
 STUDENT_NAME Varchar(20),
 STUDENT_AGE BigInt,
 STUDENT_GENDER Varchar(5),
 OBJECT_VERSION_NUMBER BigInt Not Null Default 1,
 CREATION_DATE  datetime Not Null Default CURRENT_TIMESTAMP,
 CREATED_BY BigInt Not Null Default -1,
 LAST_UPDATED_BY BigInt Not Null Default -1,
 LAST_UPDATE_DATE datetime Not Null Default CURRENT_TIMESTAMP,
 LAST_UPDATE_LOGIN BigInt Default -1
);
ALTER TABLE  HAND_STUDENT COMMENT '学生信息表';
ALTER TABLE  HAND_STUDENT MODIFY `STUDENT_NO` Varchar(10) Not Null Comment '学号';
ALTER TABLE  HAND_STUDENT MODIFY `STUDENT_NAME` Varchar(20) Comment '姓名';
ALTER TABLE  HAND_STUDENT MODIFY `STUDENT_AGE` BigInt Comment '年龄';
ALTER TABLE  HAND_STUDENT MODIFY `STUDENT_GENDER` Varchar(5) Comment '性别';
ALTER TABLE  HAND_STUDENT MODIFY `OBJECT_VERSION_NUMBER` BigInt Not Null Default 1 Comment '行版本号，用来处理锁';

ALTER TABLE `HAND_STUDENT` ADD UNIQUE (`STUDENT_NO`);

Create Table  HAND_TEACHER
(
 TEACHER_NO Varchar(10) Not Null,
 TEACHER_NAME Varchar(20),
 MANAGER_NO Varchar(10),
 OBJECT_VERSION_NUMBER BigInt Not Null Default 1,
 CREATION_DATE  datetime Not Null Default CURRENT_TIMESTAMP,
 CREATED_BY BigInt Not Null Default -1,
 LAST_UPDATED_BY BigInt Not Null Default -1,
 LAST_UPDATE_DATE datetime Not Null Default CURRENT_TIMESTAMP,
 LAST_UPDATE_LOGIN BigInt Default -1
);
ALTER TABLE  HAND_TEACHER COMMENT '教师信息表';
ALTER TABLE  HAND_TEACHER MODIFY `TEACHER_NO` Varchar(10) Not Null Comment '教师编号';
ALTER TABLE  HAND_TEACHER MODIFY `TEACHER_NAME` Varchar(20) Comment '教师名称';
ALTER TABLE  HAND_TEACHER MODIFY `MANAGER_NO` Varchar(10) Comment '上级编号';
ALTER TABLE  HAND_TEACHER MODIFY `OBJECT_VERSION_NUMBER` BigInt Not Null Default 1 Comment '行版本号，用来处理锁';

ALTER TABLE `HAND_TEACHER` ADD UNIQUE (`TEACHER_NO`);


Create Table  HAND_COURSE
(
 COURSE_NO Varchar(10) Not Null,
 COURSE_NAME Varchar(20),
 TEACHER_NO Varchar(10) Not Null,
 OBJECT_VERSION_NUMBER BigInt Not Null Default 1,
 CREATION_DATE  datetime Not Null Default CURRENT_TIMESTAMP,
 CREATED_BY BigInt Not Null Default -1,
 LAST_UPDATED_BY BigInt Not Null Default -1,
 LAST_UPDATE_DATE datetime Not Null Default CURRENT_TIMESTAMP,
 LAST_UPDATE_LOGIN BigInt Default -1
);
ALTER TABLE  HAND_COURSE COMMENT '课程信息表';
ALTER TABLE  HAND_COURSE MODIFY `COURSE_NO` Varchar(10) Not Null Comment '课程号';
ALTER TABLE  HAND_COURSE MODIFY `COURSE_NAME` Varchar(20) Comment '课程名称';
ALTER TABLE  HAND_COURSE MODIFY `TEACHER_NO` Varchar(10) Not Null Comment '教师编号';
ALTER TABLE  HAND_COURSE MODIFY `OBJECT_VERSION_NUMBER` BigInt Not Null Default 1 Comment '行版本号，用来处理锁';

ALTER TABLE `HAND_COURSE` ADD UNIQUE (`COURSE_NO`);

Create Table  HAND_STUDENT_CORE
(
 STUDENT_NO Varchar(10) Not Null,
 COURSE_NO Varchar(10) Not Null,
 CORE Decimal(4,2),
 OBJECT_VERSION_NUMBER BigInt Not Null Default 1,
 CREATION_DATE  datetime Not Null Default CURRENT_TIMESTAMP,
 CREATED_BY BigInt Not Null Default -1,
 LAST_UPDATED_BY BigInt Not Null Default -1,
 LAST_UPDATE_DATE datetime Not Null Default CURRENT_TIMESTAMP,
 LAST_UPDATE_LOGIN BigInt Default -1
);
ALTER TABLE  HAND_STUDENT_CORE COMMENT '学生成绩表';
ALTER TABLE  HAND_STUDENT_CORE MODIFY `STUDENT_NO` Varchar(10) Not Null Comment '学号';
ALTER TABLE  HAND_STUDENT_CORE MODIFY `COURSE_NO` Varchar(10) Not Null Comment '课程号';
ALTER TABLE  HAND_STUDENT_CORE MODIFY `CORE` Decimal(4,2) Comment '分数';
ALTER TABLE  HAND_STUDENT_CORE MODIFY `OBJECT_VERSION_NUMBER` BigInt Not Null Default 1 Comment '行版本号，用来处理锁';

ALTER TABLE `HAND_STUDENT_CORE` ADD UNIQUE (`STUDENT_NO`,`COURSE_NO`);



/*******初始化学生表的数据******/
insert into HAND_STUDENT(STUDENT_NO,STUDENT_NAME,STUDENT_AGE,STUDENT_GENDER) values ('s001','张三',23,'男');
insert into HAND_STUDENT(STUDENT_NO,STUDENT_NAME,STUDENT_AGE,STUDENT_GENDER) values ('s002','李四',23,'男');
insert into HAND_STUDENT(STUDENT_NO,STUDENT_NAME,STUDENT_AGE,STUDENT_GENDER) values ('s003','吴鹏',25,'男');
insert into HAND_STUDENT(STUDENT_NO,STUDENT_NAME,STUDENT_AGE,STUDENT_GENDER) values ('s004','琴沁',20,'女');
insert into HAND_STUDENT(STUDENT_NO,STUDENT_NAME,STUDENT_AGE,STUDENT_GENDER) values ('s005','王丽',20,'女');
insert into HAND_STUDENT(STUDENT_NO,STUDENT_NAME,STUDENT_AGE,STUDENT_GENDER) values ('s006','李波',21,'男');
insert into HAND_STUDENT(STUDENT_NO,STUDENT_NAME,STUDENT_AGE,STUDENT_GENDER) values ('s007','刘玉',21,'男');
insert into HAND_STUDENT(STUDENT_NO,STUDENT_NAME,STUDENT_AGE,STUDENT_GENDER) values ('s008','萧蓉',21,'女');
insert into HAND_STUDENT(STUDENT_NO,STUDENT_NAME,STUDENT_AGE,STUDENT_GENDER) values ('s009','陈萧晓',23,'女');
insert into HAND_STUDENT(STUDENT_NO,STUDENT_NAME,STUDENT_AGE,STUDENT_GENDER) values ('s010','陈美',22,'女');
commit;
/******************初始化教师表***********************/
insert into HAND_TEACHER(TEACHER_NO,TEACHER_NAME,MANAGER_NO) values ('t001', '刘阳','');
insert into HAND_TEACHER(TEACHER_NO,TEACHER_NAME,MANAGER_NO)  values ('t002', '谌燕','t001');
insert into HAND_TEACHER(TEACHER_NO,TEACHER_NAME,MANAGER_NO)  values ('t003', '胡明星','t002');
commit;
/***************初始化课程表****************************/
insert into HAND_COURSE(COURSE_NO,COURSE_NAME,TEACHER_NO) values ('c001','J2SE','t002');
insert into HAND_COURSE(COURSE_NO,COURSE_NAME,TEACHER_NO) values ('c002','Java Web','t002');
insert into HAND_COURSE(COURSE_NO,COURSE_NAME,TEACHER_NO) values ('c003','SSH','t001');
insert into HAND_COURSE(COURSE_NO,COURSE_NAME,TEACHER_NO) values ('c004','Oracle','t001');
insert into HAND_COURSE(COURSE_NO,COURSE_NAME,TEACHER_NO) values ('c005','SQL SERVER 2005','t003');
insert into HAND_COURSE(COURSE_NO,COURSE_NAME,TEACHER_NO) values ('c006','C#','t003');
insert into HAND_COURSE(COURSE_NO,COURSE_NAME,TEACHER_NO) values ('c007','JavaScript','t002');
insert into HAND_COURSE(COURSE_NO,COURSE_NAME,TEACHER_NO) values ('c008','DIV+CSS','t001');
insert into HAND_COURSE(COURSE_NO,COURSE_NAME,TEACHER_NO) values ('c009','PHP','t003');
insert into HAND_COURSE(COURSE_NO,COURSE_NAME,TEACHER_NO) values ('c010','EJB3.0','t002');
commit;
/***************初始化成绩表***********************/
insert into HAND_STUDENT_CORE(STUDENT_NO,COURSE_NO,CORE) values ('s001','c001',58.9);
insert into HAND_STUDENT_CORE(STUDENT_NO,COURSE_NO,CORE) values ('s002','c001',80.9);
insert into HAND_STUDENT_CORE(STUDENT_NO,COURSE_NO,CORE) values ('s003','c001',81.9);
insert into HAND_STUDENT_CORE(STUDENT_NO,COURSE_NO,CORE) values ('s004','c001',60.9);
insert into HAND_STUDENT_CORE(STUDENT_NO,COURSE_NO,CORE) values ('s001','c002',82.9);
insert into HAND_STUDENT_CORE(STUDENT_NO,COURSE_NO,CORE) values ('s002','c002',72.9);
insert into HAND_STUDENT_CORE(STUDENT_NO,COURSE_NO,CORE) values ('s003','c002',81.9);
insert into HAND_STUDENT_CORE(STUDENT_NO,COURSE_NO,CORE) values ('s001','c003','59');
commit;

-- 1、查询没学过“谌燕”老师课的同学，显示（学号、姓名）
SELECT STUDENT_NO, STUDENT_NAME FROM HAND_STUDENT 
	WHERE HAND_STUDENT.STUDENT_NO NOT IN (
		SELECT HAND_STUDENT_CORE.STUDENT_NO FROM HAND_STUDENT_CORE, HAND_COURSE, HAND_TEACHER
		WHERE HAND_COURSE.TEACHER_NO = HAND_TEACHER.TEACHER_NO AND HAND_STUDENT_CORE.COURSE_NO = HAND_COURSE.COURSE_NO AND 				   HAND_TEACHER.TEACHER_NAME = '谌燕');

-- 2、查询没有学全所有课的同学，显示（学号、姓名）
SELECT STUDENT_NO, STUDENT_NAME FROM HAND_STUDENT
	WHERE HAND_STUDENT.STUDENT_NO IN (
	SELECT DISTINCT HAND_STUDENT_CORE.STUDENT_NO FROM HAND_STUDENT_CORE 
	WHERE HAND_STUDENT_CORE.COURSE_NO > ANY(SELECT HAND_COURSE.COURSE_NO FROM HAND_COURSE ORDER BY HAND_COURSE.COURSE_NO DESC));
                  
-- 3、查询“c001”课程比“c002”课程成绩高的所有学生，显示（学号、姓名）
SELECT STUDENT_NO, STUDENT_NAME FROM HAND_STUDENT
	WHERE HAND_STUDENT.STUDENT_NO IN (
	SELECT A.STUDENT_NO FROM HAND_STUDENT_CORE A, HAND_STUDENT_CORE B 
	WHERE A.COURSE_NO = 'c001' AND B.COURSE_NO = 'c002' AND A.CORE > B.CORE);	

                  
-- 4、按各科平均成绩和及格率的百分数，按及格率高到低顺序，显示（课程号、平均分、及格率）
SELECT A.COURSE_NO, AVG(A.CORE), COUNT(A.STUDENT_NO)
	FROM HAND_STUDENT_CORE A
	GROUP BY A.COURSE_NO;

 
-- 5、1992年之后出生的学生名单找出年龄最大和最小的同学，显示（学号、姓名、年龄）
SELECT DISTINCT A.STUDENT_NO, A.STUDENT_NAME, A.STUDENT_AGE
	FROM HAND_STUDENT A, HAND_STUDENT B
	WHERE A.STUDENT_AGE < 27 AND A.STUDENT_AGE = ALL(SELECT MIN( HAND_STUDENT.STUDENT_AGE) FROM HAND_STUDENT) OR A.STUDENT_AGE = 		ALL(SELECT MAX( HAND_STUDENT.STUDENT_AGE) FROM HAND_STUDENT);

-- 6、统计列出矩阵类型各分数段人数，横轴为分数段[100-85]、[85-70]、[70-60]、[<60]，纵轴为课程号、课程名称


 
-- 7、查询各科成绩前三名的记录:(不考虑成绩并列情况)，显示（学号、课程号、分数）
SELECT  HAND_STUDENT_CORE.STUDENT_NO, HAND_STUDENT_CORE.COURSE_NO, HAND_STUDENT_CORE.CORE
FROM HAND_STUDENT_CORE
GROUP BY HAND_STUDENT_CORE.COURSE_NO
ORDER BY HAND_STUDENT_CORE.CORE DESC
LIMIT 3;

 
-- 8、查询选修“谌燕”老师所授课程的学生中每科成绩最高的学生，显示（学号、姓名、课程名称、成绩）
SELECT HAND_STUDENT_CORE.STUDENT_NO, A.STUDENT_NAME, B.COURSE_NAME, HAND_STUDENT_CORE.CORE
FROM HAND_STUDENT A, HAND_COURSE B, HAND_STUDENT_CORE, HAND_TEACHER D
WHERE A.STUDENT_NO = HAND_STUDENT_CORE.STUDENT_NO AND B.TEACHER_NO = D.TEACHER_NO AND B.COURSE_NO = HAND_STUDENT_CORE.COURSE_NO AND D.TEACHER_NAME = '谌燕' AND HAND_STUDENT_CORE.CORE IN (SELECT MAX(HAND_STUDENT_CORE.CORE) FROM HAND_STUDENT_CORE)
GROUP BY HAND_STUDENT_CORE.COURSE_NO;

 
-- 9、查询两门及以上不及格课程的同学及平均成绩，显示（学号、姓名、平均成绩（保留两位小数））
 
-- 10、查询姓氏数量最多的学生名单，显示（学号、姓名、人数）
SELECT A.STUDENT_NO, A.STUDENT_NAME, COUNT(A.STUDENT_NO)
FROM HAND_STUDENT A 
   
-- 11、查询课程名称为“J2SE”的学生成绩信息，90以上为“优秀”、80-90为“良好”、60-80为“及格”、60分以下为“不及格”，显示（学号、姓名、课程名称、成绩、等级）
   
-- 12、查询教师“胡明星”的所有主管及姓名:（无主管的教师也需要显示），显示（教师编号、教师名称、主管编号、主管名称）

-- 13、查询分数高于课程“J2SE”的所有学生课程信息，显示（学号，姓名，课程名称、分数）
   
-- 14、分别根据教师、课程、教师和课程三个条件统计选课的学生数量：(使用rollup),显示（教师名称、课程名称、选课数量）
 
-- 15、查询所有课程成绩前三名的按照升序排在最开头，其余数据排序保持默认（7分）,显示（学号、成绩）




