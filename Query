-- HOSPITAL MANAGEMENT SYSTEM 

DROP DATABASE IF EXISTS hospital_db;
CREATE DATABASE hospital_db;
USE hospital_db;


CREATE TABLE Patients (
    patient_id INT AUTO_INCREMENT PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    date_of_birth DATE,
    gender ENUM('Male', 'Female', 'Other'),
    phone VARCHAR(15),
    address TEXT,
    city VARCHAR(50),
    state VARCHAR(50)
);


CREATE TABLE Departments (
    department_id INT AUTO_INCREMENT PRIMARY KEY,
    department_name VARCHAR(100) NOT NULL,
    department_head VARCHAR(100)
);


CREATE TABLE Doctors (
    doctor_id INT AUTO_INCREMENT PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    specialization VARCHAR(100),
    department_id INT,
    phone VARCHAR(15),
    consultation_fee DECIMAL(10, 2),
    qualification VARCHAR(100),
    FOREIGN KEY (department_id) REFERENCES Departments(department_id)
);


CREATE TABLE Appointments (
    appointment_id INT AUTO_INCREMENT PRIMARY KEY,
    patient_id INT,
    doctor_id INT,
    appointment_date DATE,
    appointment_time TIME,
    status ENUM('Scheduled', 'Completed', 'Cancelled') DEFAULT 'Scheduled',
    diagnosis TEXT,
    FOREIGN KEY (patient_id) REFERENCES Patients(patient_id),
    FOREIGN KEY (doctor_id) REFERENCES Doctors(doctor_id)
);


CREATE TABLE Medicines (
    medicine_id INT AUTO_INCREMENT PRIMARY KEY,
    medicine_name VARCHAR(100) NOT NULL,
    manufacturer VARCHAR(100),
    price DECIMAL(10, 2),
    stock_quantity INT,
    medicine_type ENUM('Allopathy', 'Ayurvedic', 'Homeopathy')
);


CREATE TABLE Bills (
    bill_id INT AUTO_INCREMENT PRIMARY KEY,
    patient_id INT,
    appointment_id INT,
    bill_date DATE DEFAULT (CURRENT_DATE),
    total_amount DECIMAL(12, 2),
    payment_status ENUM('Paid', 'Pending', 'Partial') DEFAULT 'Pending',
    payment_mode ENUM('Cash', 'UPI', 'Card', 'Insurance'),
    FOREIGN KEY (patient_id) REFERENCES Patients(patient_id),
    FOREIGN KEY (appointment_id) REFERENCES Appointments(appointment_id)
);


CREATE TABLE Prescriptions (
    prescription_id INT AUTO_INCREMENT PRIMARY KEY,
    appointment_id INT,
    medicine_id INT,
    quantity INT,
    dosage VARCHAR(50),
    duration VARCHAR(50),
    FOREIGN KEY (appointment_id) REFERENCES Appointments(appointment_id),
    FOREIGN KEY (medicine_id) REFERENCES Medicines(medicine_id)
);


INSERT INTO Departments (department_name, department_head) VALUES
('Cardiology', 'Dr. Rajesh Sharma'),
('Neurology', 'Dr. Priya Singh'),
('Pediatrics', 'Dr. Arun Kumar'),
('Orthopedics', 'Dr. Sunita Patel'),
('Gynecology', 'Dr. Meera Desai'),
('General Medicine', 'Dr. Vikram Malhotra');

INSERT INTO Patients (first_name, last_name, date_of_birth, gender, phone, address, city, state) VALUES
('Rahul', 'Sharma', '1985-08-12', 'Male', '9876543210', 'A-102, Sunshine Apartments, MG Road', 'Mumbai', 'Maharashtra'),
('Priya', 'Patel', '1992-03-25', 'Female', '8765432109', 'B-45, Green Valley Society', 'Ahmedabad', 'Gujarat'),
('Arjun', 'Singh', '1978-11-30', 'Male', '7654321098', 'C-78, Krishna Nagar', 'Delhi', 'Delhi'),
('Sneha', 'Reddy', '1988-07-14', 'Female', '6543210987', 'D-23, Banjara Hills', 'Hyderabad', 'Telangana'),
('Vikram', 'Kumar', '1965-12-08', 'Male', '9432109876', 'E-56, JP Nagar', 'Bangalore', 'Karnataka'),
('Ananya', 'Iyer', '1995-04-18', 'Female', '8321098765', 'F-89, Anna Nagar', 'Chennai', 'Tamil Nadu'),
('Rohan', 'Verma', '1982-09-22', 'Male', '7210987654', 'G-12, Salt Lake City', 'Kolkata', 'West Bengal');

INSERT INTO Doctors (first_name, last_name, specialization, department_id, phone, consultation_fee, qualification) VALUES
('Rajesh', 'Sharma', 'Cardiologist', 1, '9876543201', 800.00, 'MD, DM Cardiology'),
('Priya', 'Singh', 'Neurologist', 2, '8765432102', 1200.00, 'DM Neurology'),
('Arun', 'Kumar', 'Pediatrician', 3, '7654321093', 600.00, 'MD Pediatrics'),
('Sunita', 'Patel', 'Orthopedic Surgeon', 4, '6543210984', 1500.00, 'MS Orthopedics'),
('Meera', 'Desai', 'Gynecologist', 5, '5432109875', 1000.00, 'MD Gynecology'),
('Vikram', 'Malhotra', 'General Physician', 6, '4321098766', 500.00, 'MD Medicine'),
('Anil', 'Kapoor', 'Cardiologist', 1, '3210987657', 900.00, 'DM Cardiology');

INSERT INTO Medicines (medicine_name, manufacturer, price, stock_quantity, medicine_type) VALUES
('Paracetamol', 'Cipla', 15.50, 1000, 'Allopathy'),
('Azithromycin', 'Sun Pharma', 85.75, 500, 'Allopathy'),
('Amoxicillin', 'Dr. Reddy''s', 45.25, 750, 'Allopathy'),
('Atorvastatin', 'Lupin', 68.90, 600, 'Allopathy'),
('Metformin', 'Glenmark', 32.40, 1200, 'Allopathy'),
('Ashwagandha', 'Dabur', 120.00, 300, 'Ayurvedic'),
('Chyawanprash', 'Baidyanath', 250.00, 200, 'Ayurvedic'),
('Liv 52', 'Himalaya', 95.00, 400, 'Ayurvedic'),
('Omeprazole', 'Zydus', 55.60, 800, 'Allopathy'),
('Losartan', 'Torrent', 42.30, 700, 'Allopathy');

INSERT INTO Appointments (patient_id, doctor_id, appointment_date, appointment_time, status, diagnosis) VALUES
(1, 1, '2024-01-15', '09:00:00', 'Completed', 'Hypertension - prescribed medication'),
(2, 2, '2024-01-15', '10:30:00', 'Completed', 'Migraine - follow up in 2 weeks'),
(3, 3, '2024-01-16', '11:00:00', 'Completed', 'Child vaccination - DPT booster'),
(1, 1, '2024-01-20', '14:00:00', 'Completed', 'Routine checkup - BP under control'),
(4, 4, '2024-01-18', '15:30:00', 'Completed', 'Knee pain - advised physiotherapy'),
(5, 1, '2024-01-19', '16:00:00', 'Completed', 'Heart condition - ECG normal'),
(6, 5, '2024-01-21', '09:30:00', 'Completed', 'Pregnancy checkup - 6 months'),
(2, 2, '2024-01-22', '11:00:00', 'Scheduled', NULL),
(7, 6, '2024-01-23', '10:00:00', 'Completed', 'Fever and cold - viral infection'),
(3, 3, '2024-01-24', '14:00:00', 'Scheduled', NULL),
(4, 4, '2024-01-25', '15:00:00', 'Scheduled', NULL);

INSERT INTO Prescriptions (appointment_id, medicine_id, quantity, dosage, duration) VALUES
(1, 4, 30, '1 tablet', 'Once daily at night'),
(1, 10, 30, '1 tablet', 'Once daily morning'),
(2, 1, 20, '1 tablet', 'When needed for pain'),
(4, 4, 30, '1 tablet', 'Once daily at night'),
(4, 3, 15, '1 tablet', 'Twice daily for 7 days'),
(5, 6, 2, '1 teaspoon', 'Twice daily with milk'),
(6, 4, 60, '1 tablet', 'Once daily at night'),
(7, 8, 1, '2 tablets', 'Twice daily after food'),
(9, 1, 10, '1 tablet', 'Every 6 hours for fever'),
(9, 3, 10, '1 tablet', 'Twice daily for 5 days');

INSERT INTO Bills (patient_id, appointment_id, total_amount, payment_status, payment_mode) VALUES
(1, 1, 1200.50, 'Paid', 'UPI'),
(2, 2, 1850.75, 'Paid', 'Card'),
(3, 3, 650.00, 'Pending', 'Cash'),
(1, 4, 950.25, 'Paid', 'UPI'),
(4, 5, 3200.00, 'Partial', 'Insurance'),
(5, 6, 2750.30, 'Pending', 'Cash'),
(6, 7, 1500.00, 'Paid', 'Card'),
(7, 9, 850.75, 'Paid', 'UPI');


-- Query 1: Doctor with most patients
SELECT '=== TOP DOCTORS BY PATIENT COUNT ===' AS '';
SELECT 
    CONCAT(d.first_name, ' ', d.last_name) AS doctor_name,
    d.specialization,
    d.qualification,
    COUNT(DISTINCT a.patient_id) AS patient_count,
    CONCAT('₹', FORMAT(AVG(d.consultation_fee), 2)) AS consultation_fee
FROM Doctors d
JOIN Appointments a ON d.doctor_id = a.doctor_id
WHERE a.status = 'Completed'
GROUP BY d.doctor_id, d.first_name, d.last_name, d.specialization, d.qualification
ORDER BY patient_count DESC;

-- Query 2: Patients with multiple visits
SELECT '=== PATIENTS WITH MULTIPLE VISITS ===' AS '';
SELECT 
    CONCAT(p.first_name, ' ', p.last_name) AS patient_name,
    p.city,
    p.state,
    p.phone,
    COUNT(a.appointment_id) AS total_visits,
    MIN(a.appointment_date) AS first_visit,
    MAX(a.appointment_date) AS last_visit
FROM Patients p
JOIN Appointments a ON p.patient_id = a.patient_id
WHERE a.status = 'Completed'
GROUP BY p.patient_id, p.first_name, p.last_name, p.city, p.state, p.phone
HAVING COUNT(a.appointment_id) > 1
ORDER BY total_visits DESC;

-- 4. ADDITIONAL USEFUL QUERIES

-- Query 3: Today's appointments
SELECT '=== TODAY''S APPOINTMENTS ===' AS '';
SELECT 
    p.first_name AS patient_first,
    p.last_name AS patient_last,
    d.first_name AS doctor_first,
    d.last_name AS doctor_last,
    d.specialization,
    a.appointment_time,
    a.status
FROM Appointments a
JOIN Patients p ON a.patient_id = p.patient_id
JOIN Doctors d ON a.doctor_id = d.doctor_id
WHERE a.appointment_date = CURDATE()
ORDER BY a.appointment_time;

-- Query 4: Medicine inventory status
SELECT '=== MEDICINE INVENTORY STATUS ===' AS '';
SELECT 
    medicine_name,
    manufacturer,
    medicine_type,
    CONCAT('₹', price) AS price_per_unit,
    stock_quantity,
    CASE 
        WHEN stock_quantity < 100 THEN 'LOW STOCK'
        WHEN stock_quantity BETWEEN 100 AND 300 THEN 'MEDIUM STOCK'
        ELSE 'GOOD STOCK'
    END AS stock_status
FROM Medicines
ORDER BY stock_quantity ASC;

-- Query 5: Department-wise doctor distribution
SELECT '=== DEPARTMENT-WISE DOCTOR DISTRIBUTION ===' AS '';
SELECT 
    d.department_name,
    COUNT(doc.doctor_id) AS number_of_doctors,
    GROUP_CONCAT(CONCAT(doc.first_name, ' ', doc.last_name) SEPARATOR ', ') AS doctors_list
FROM Departments d
LEFT JOIN Doctors doc ON d.department_id = doc.department_id
GROUP BY d.department_id, d.department_name
ORDER BY number_of_doctors DESC;

-- Query 6: Most prescribed medicines
SELECT '=== MOST PRESCRIBED MEDICINES ===' AS '';
SELECT 
    m.medicine_name,
    m.manufacturer,
    m.medicine_type,
    COUNT(p.prescription_id) AS times_prescribed,
    SUM(p.quantity) AS total_quantity_prescribed
FROM Medicines m
JOIN Prescriptions p ON m.medicine_id = p.medicine_id
GROUP BY m.medicine_id, m.medicine_name, m.manufacturer, m.medicine_type
ORDER BY times_prescribed DESC;

-- Query 7: Patient demographic analysis
SELECT '=== PATIENT DEMOGRAPHIC ANALYSIS ===' AS '';
SELECT 
    gender,
    COUNT(*) AS patient_count,
    CONCAT(ROUND((COUNT(*) * 100.0 / (SELECT COUNT(*) FROM Patients)), 2), '%') AS percentage,
    AVG(YEAR(CURDATE()) - YEAR(date_of_birth)) AS average_age
FROM Patients
GROUP BY gender
ORDER BY patient_count DESC;

-- Query 8: Upcoming appointments
SELECT '=== UPCOMING APPOINTMENTS (Next 7 Days) ===' AS '';
SELECT 
    p.first_name AS patient_first,
    p.last_name AS patient_last,
    d.first_name AS doctor_first,
    d.last_name AS doctor_last,
    d.specialization,
    a.appointment_date,
    a.appointment_time,
    a.status
FROM Appointments a
JOIN Patients p ON a.patient_id = p.patient_id
JOIN Doctors d ON a.doctor_id = d.doctor_id
WHERE a.appointment_date BETWEEN CURDATE() AND DATE_ADD(CURDATE(), INTERVAL 7 DAY)
AND a.status = 'Scheduled'
ORDER BY a.appointment_date, a.appointment_time;

-- Query 9: Doctor's appointment schedule
SELECT '=== DOCTOR APPOINTMENT SCHEDULE ===' AS '';
SELECT 
    CONCAT(d.first_name, ' ', d.last_name) AS doctor_name,
    d.specialization,
    COUNT(a.appointment_id) AS total_appointments,
    SUM(CASE WHEN a.status = 'Completed' THEN 1 ELSE 0 END) AS completed_appointments,
    SUM(CASE WHEN a.status = 'Scheduled' THEN 1 ELSE 0 END) AS scheduled_appointments,
    SUM(CASE WHEN a.status = 'Cancelled' THEN 1 ELSE 0 END) AS cancelled_appointments
FROM Doctors d
LEFT JOIN Appointments a ON d.doctor_id = a.doctor_id
GROUP BY d.doctor_id, d.first_name, d.last_name, d.specialization
ORDER BY total_appointments DESC;

-- Query 10: Patient medical history
SELECT '=== COMPLETE PATIENT MEDICAL HISTORY ===' AS '';
SELECT 
    CONCAT(p.first_name, ' ', p.last_name) AS patient_name,
    p.date_of_birth,
    p.gender,
    p.city,
    p.state,
    CONCAT(d.first_name, ' ', d.last_name) AS doctor_name,
    d.specialization,
    a.appointment_date,
    a.diagnosis,
    GROUP_CONCAT(CONCAT(m.medicine_name, ' (', pr.dosage, ')') SEPARATOR ', ') AS prescribed_medicines
FROM Patients p
JOIN Appointments a ON p.patient_id = a.patient_id
JOIN Doctors d ON a.doctor_id = d.doctor_id
LEFT JOIN Prescriptions pr ON a.appointment_id = pr.appointment_id
LEFT JOIN Medicines m ON pr.medicine_id = m.medicine_id
GROUP BY p.patient_id, a.appointment_id, d.doctor_id
ORDER BY p.last_name, p.first_name, a.appointment_date DESC;

-- SELECT '=== HOSPITAL DATABASE SETUP COMPLETE ===' AS '';
-- SELECT '📊 Run the analytical queries to get insights' AS Next_Step;
