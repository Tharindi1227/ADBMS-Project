# ADBMS-Project
SET  SERVEROUTPUT ON;
-- Create sequence for auto-increment
CREATE SEQUENCE membership_id_seq START WITH 1 INCREMENT BY 1;
drop sequence membership_id_seq;
CREATE SEQUENCE members_id_seq START WITH 1 INCREMENT BY 1;
CREATE SEQUENCE trainers_id_seq START WITH 1 INCREMENT BY 1;


-- Members Table
CREATE TABLE Doctors (
    doctor_id NUMBER PRIMARY KEY, 
    doctor _name VARCHAR2 (100) NOT NULL, 
    specialization VARCHAR2 (50), 
    contact _info VARCHAR2 (255)
);
drop table Members;
-- Trainers Table
CREATE TABLE Trainers (
    trainer_id NUMBER PRIMARY KEY,
    first_name VARCHAR2(100),
    last_name VARCHAR2(100),
    age NUMBER,
    phone_num VARCHAR2(100),
    email VARCHAR2(100) UNIQUE,
    specialty VARCHAR2(100)
);

drop table Trainers;
-- Memberships Table
CREATE TABLE Memberships (
    membership_id NUMBER PRIMARY KEY,
    member_id NUMBER,
    start_date DATE,
    end_date DATE,
    fee NUMBER,
    CONSTRAINT fk_member FOREIGN KEY (member_id) REFERENCES Members(member_id)
);
drop table Memberships;

-- Sessions Table
CREATE TABLE Sessions (
    session_id NUMBER PRIMARY KEY,
    trainer_id NUMBER,
    session_name VARCHAR2(100),
    session_date DATE,
    CONSTRAINT fk_trainer FOREIGN KEY (trainer_id) REFERENCES Trainers(trainer_id)
);
drop table Sessions;

--Insert data into Members Table
INSERT INTO Members (member_id, first_name, last_name, age, phone_num, email) VALUES(1, 'Arjun', 'Perera', 28, '+94 77 123 4567', 'arjunperera@example.com');
INSERT INTO Members (member_id, first_name, last_name, age, phone_num, email) VALUES(2, 'Nisha', 'Fernando', 35, '+94 71 987 6543', 'nishaf@gmail.com');
INSERT INTO Members (member_id, first_name, last_name, age, phone_num, email) VALUES(3, 'Lakshmi', 'Wijesekera', 22, '+94 76 456 7890', 'lakshmiwijesekera@example.com');
INSERT INTO Members (member_id, first_name, last_name, age, phone_num, email) VALUES(4, 'Rohan', 'Samarasinghe', 42, '+94 77 321 9876', 'rohansamarasinghe@example.com');
INSERT INTO Members (member_id, first_name, last_name, age, phone_num, email) VALUES(5, 'Samantha', 'Gunaratne', 30, '+94 75 654 3210', 'samanthagunaratne@example.com');
INSERT INTO Members (member_id, first_name, last_name, age, phone_num, email) VALUES(6, 'Dinesh', 'Kumarasiri', 26, '+94 71 789 1234', 'dineshkumarasiri@example.com');

--Insert data into Trainers Table
INSERT INTO Trainers (trainer_id, first_name, last_name, age, phone_num, email, specialty) VALUES(1, 'Chamika', 'Silva', 33, '+94 77 555 1234', 'chamikasilva@example.com', 'Weightlifting');
INSERT INTO Trainers (trainer_id, first_name, last_name, age, phone_num, email, specialty) VALUES(2, 'Shehan', 'Liyanage', 29, '+94 76 888 6543', 'shehanliyanage@example.com', 'Cardio');
INSERT INTO Trainers (trainer_id, first_name, last_name, age, phone_num, email, specialty) VALUES(3, 'Priya', 'De Silva', 40, '+94 71 444 3219', 'priyadesilva@example.com', 'Yoga'); 
INSERT INTO Trainers (trainer_id, first_name, last_name, age, phone_num, email, specialty) VALUES(4, 'Vijay', 'Mendis', 27, '+94 75 222 7654', 'vijaymendis@example.com', 'Crossfit');
INSERT INTO Trainers (trainer_id, first_name, last_name, age, phone_num, email, specialty) VALUES(5, 'Tamara', 'Gamage', 34, '+94 77 333 4561', 'tamaragamage@example.com', 'Pilates');
INSERT INTO Trainers (trainer_id, first_name, last_name, age, phone_num, email, specialty) VALUES(6, 'Tharindu', 'Jayasinghe', 38, '+94 71 999 0987', 'tharindujayasinghe@example.com', 'HIIT');

--Insert data into Membership Table
INSERT INTO Memberships (membership_id, member_id, start_date, end_date, fee)VALUES(1, 1, TO_DATE('2023-01-01', 'YYYY-MM-DD'), TO_DATE('2023-12-31', 'YYYY-MM-DD'), 5000);
INSERT INTO Memberships (membership_id, member_id, start_date, end_date, fee)VALUES(2, 2, TO_DATE('2023-02-01', 'YYYY-MM-DD'), TO_DATE('2023-11-30', 'YYYY-MM-DD'), 4500);
INSERT INTO Memberships (membership_id, member_id, start_date, end_date, fee)VALUES(3, 3, TO_DATE('2023-03-01', 'YYYY-MM-DD'), TO_DATE('2023-12-31', 'YYYY-MM-DD'), 4800);
INSERT INTO Memberships (membership_id, member_id, start_date, end_date, fee)VALUES(4, 4, TO_DATE('2023-04-15', 'YYYY-MM-DD'), TO_DATE('2024-04-14', 'YYYY-MM-DD'), 5500);
INSERT INTO Memberships (membership_id, member_id, start_date, end_date, fee)VALUES(5, 5, TO_DATE('2023-05-01', 'YYYY-MM-DD'), TO_DATE('2024-04-30', 'YYYY-MM-DD'), 5300);
INSERT INTO Memberships (membership_id, member_id, start_date, end_date, fee)VALUES(6, 6, TO_DATE('2023-06-01', 'YYYY-MM-DD'), TO_DATE('2024-05-31', 'YYYY-MM-DD'), 6000);

--Insert data into Sessions Table
INSERT INTO Sessions (session_id, trainer_id, session_name, session_date)VALUES(1, 1, 'Weightlifting Basics', TO_DATE('2023-10-01', 'YYYY-MM-DD'));
INSERT INTO Sessions (session_id, trainer_id, session_name, session_date)VALUES(2, 2, 'Sri Lankan Cardio Fun', TO_DATE('2023-10-02', 'YYYY-MM-DD'));
INSERT INTO Sessions (session_id, trainer_id, session_name, session_date)VALUES(3, 3, 'Sunrise Yoga', TO_DATE('2023-10-03', 'YYYY-MM-DD'));
INSERT INTO Sessions (session_id, trainer_id, session_name, session_date)VALUES(4, 4, 'Crossfit Challenge', TO_DATE('2023-10-04', 'YYYY-MM-DD'));
INSERT INTO Sessions (session_id, trainer_id, session_name, session_date)VALUES(5, 5, 'Pilates Flow', TO_DATE('2023-10-05', 'YYYY-MM-DD'));
INSERT INTO Sessions (session_id, trainer_id, session_name, session_date)VALUES(6, 6, 'HIIT in the Park', TO_DATE('2023-10-06', 'YYYY-MM-DD'));


-- Query 1: Select members who have paid a fee greater than 400, group by member_id
SELECT member_id, SUM(fee) 
FROM Memberships 
WHERE fee > 4000 
GROUP BY member_id 
HAVING SUM(fee) > 4000;

-- Query 2: Order trainers by their specialty
SELECT * 
FROM Trainers 
ORDER BY specialty ASC;

-- Query 3: Select members and their memberships
SELECT Members.first_name, Memberships.start_date, Memberships.end_date
FROM Members
JOIN Memberships ON Members.member_id = Memberships.member_id;


-- Single-row Subquery
-- Find the member with the highest fee
SELECT first_name 
FROM Members 
WHERE member_id = (SELECT member_id FROM Memberships ORDER BY fee DESC FETCH FIRST 1 ROWS ONLY);


-- Multiple-row Subquery
-- Find all trainers who are conducting a class on a specific date
SELECT first_name 
FROM Trainers 
WHERE trainer_id IN (SELECT trainer_id FROM Sessions WHERE session_date = TO_DATE('2023-10-06', 'YYYY-MM-DD'));



--PL/SQL Block that contains a Cursor for the Memberships Table
DECLARE
    CURSOR membership_cursor IS
        SELECT membership_id, member_id, start_date, end_date, fee 
        FROM Memberships;
    v_membership_id Memberships.membership_id%TYPE;
    v_member_id Memberships.member_id%TYPE;
    v_start_date Memberships.start_date%TYPE;
    v_end_date Memberships.end_date%TYPE;
    v_fee Memberships.fee%TYPE;
BEGIN
    FOR membership_record IN membership_cursor LOOP       
        v_membership_id := membership_record.membership_id;
        v_member_id := membership_record.member_id;
        v_start_date := membership_record.start_date;
        v_end_date := membership_record.end_date;
        v_fee := membership_record.fee;
        DBMS_OUTPUT.PUT_LINE('Membership ID: ' || v_membership_id || 
                             ', Member ID: ' || v_member_id || 
                             ', Start Date: ' || TO_CHAR(v_start_date, 'YYYY-MM-DD') || 
                             ', End Date: ' || TO_CHAR(v_end_date, 'YYYY-MM-DD') || 
                             ', Fee: ' || v_fee);
    END LOOP;
    
END;
/


--View for the Members Table
CREATE VIEW view_member_details AS
SELECT 
    member_id,
    first_name,
    last_name,
    phone_num,
    email
FROM 
    Members;
SELECT * FROM view_member_details;     
   


--PL/ SQL block to retrieve a records for a given user input.
DECLARE
    
    v_first_name Members.first_name%TYPE;
    v_phone_num Members.phone_num%TYPE;

BEGIN

    SELECT first_name, phone_num 
    INTO v_first_name, v_phone_num
    FROM Members
    WHERE member_id =6;

   DBMS_OUTPUT.PUT_LINE( ' Member Name: ' || v_first_name ||  
                         ', Member Phone: ' || v_phone_num );
                         
END;
/



--PL/SQL Block to Update Record for a given user input.
DECLARE
    fee_increase Memberships.fee%TYPE := 500;  
    updated_fee Memberships.fee%TYPE;         
BEGIN
    UPDATE Memberships
    SET fee = fee + fee_increase
    WHERE membership_id = 6  
    RETURNING fee INTO updated_fee; 
    DBMS_OUTPUT.PUT_LINE('Fee updated successfully.');
    DBMS_OUTPUT.PUT_LINE('Updated fee is: ' || updated_fee);
END;
/


--PL/SQL Block to Delete a Record for a given user input.
DECLARE
    v_member_id Members.member_id%TYPE := 3;  
BEGIN
   
    DELETE FROM Memberships
    WHERE member_id = v_member_id;

    DELETE FROM Members
    WHERE member_id = v_member_id;

    DBMS_OUTPUT.PUT_LINE('Member record with ID ' || v_member_id || ' and related memberships deleted successfully.');
END;
/



--Modified above query
DECLARE
    v_member_id Members.member_id%TYPE := 5;  
    v_memberships_deleted NUMBER;             
    v_members_deleted NUMBER;               
BEGIN
    
    DELETE FROM Memberships
    WHERE member_id = v_member_id;
    v_memberships_deleted := SQL%ROWCOUNT;  
    
    DELETE FROM Members
    WHERE member_id = v_member_id;
    v_members_deleted := SQL%ROWCOUNT; 

    DBMS_OUTPUT.PUT_LINE(v_memberships_deleted || ' memberships deleted.');
    DBMS_OUTPUT.PUT_LINE(v_members_deleted || ' member deleted.');

    DBMS_OUTPUT.PUT_LINE('Member record with ID ' || v_member_id || ' and related memberships deleted successfully.');
END;
/







--modify 
DECLARE    
    v_first_name Members.first_name%TYPE;
    v_phone_num Members.phone_num%TYPE;
    v_member_id Members.member_id%TYPE;
BEGIN

    v_member_id := &v_member_id;

    SELECT first_name, phone_num 
    INTO v_first_name, v_phone_num
    FROM Members
    WHERE member_id = v_member_id;

   DBMS_OUTPUT.PUT_LINE( 'Member Name: ' || v_first_name ||  
                         ', Member Phone: ' || v_phone_num );                         
END;  
/  

DECLARE
    fee_increase Memberships.fee%TYPE;
    updated_fee Memberships.fee%TYPE;         
    v_membership_id Memberships.membership_id%TYPE;
BEGIN
   
    v_membership_id := &v_membership_id;
    fee_increase := &fee_increase;

    UPDATE Memberships
    SET fee = fee + fee_increase
    WHERE membership_id = v_membership_id  
    RETURNING fee INTO updated_fee;

    DBMS_OUTPUT.PUT_LINE('Fee updated successfully.');
    DBMS_OUTPUT.PUT_LINE('Updated fee is: ' || updated_fee);
END;
/  
select *from Memberships;

DECLARE
    v_member_id Members.member_id%TYPE;
    v_memberships_deleted NUMBER;             
    v_members_deleted NUMBER;                
BEGIN
   
    v_member_id := &v_member_id;

  
    DELETE FROM Memberships
    WHERE member_id = v_member_id;
    v_memberships_deleted := SQL%ROWCOUNT;  
    
   
    DELETE FROM Members
    WHERE member_id = v_member_id;
    v_members_deleted := SQL%ROWCOUNT; 

   
    DBMS_OUTPUT.PUT_LINE(v_memberships_deleted || ' memberships deleted.');
    DBMS_OUTPUT.PUT_LINE(v_members_deleted || ' member deleted.');
    DBMS_OUTPUT.PUT_LINE('Member record with ID ' || v_member_id || ' and related memberships deleted successfully.');
END;
/
