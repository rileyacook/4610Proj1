# 4610Proj1
4610 Group Project 1: Gym Database

Code:
CREATE TABLE IF NOT EXISTS Equipment (
  `equipmentID` VARCHAR(10) NOT NULL,
  `equipmentName` VARCHAR(45) NULL,
  `equipmentStatus` VARCHAR(45) NULL,
  `equipmentPurchaseDate` DATE NULL,
  `Gym_gymID` VARCHAR(10) NOT NULL,
  PRIMARY KEY (`equipmentID`),
  INDEX `fk_Equipment_Gym1_idx` (`Gym_gymID` ASC) VISIBLE,
  CONSTRAINT `fk_Equipment_Gym1`
    FOREIGN KEY (`Gym_gymID`)
    REFERENCES `ns_Sp25_21482_Group1`.`Gym` (`gymID`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;

INSERT INTO Equipment (equipmentID, equipmentName, equipmentStatus, equipmentPurchaseDate, Gym_gymID) VALUES
('E001', 'Treadmill', 'Operational', '2022-01-10', 'G001'),
('E002', 'Elliptical Machine', 'Under Maintenance', '2021-11-15', 'G001'),
('E003', 'Stationary Bike', 'Operational', '2020-09-05', 'G002'),
('E004', 'Dumbbell Set', 'Operational', '2019-08-20', 'G003'),
('E005', 'Barbell Set', 'Operational', '2021-06-25', 'G002'),
('E006', 'Smith Machine', 'Under Maintenance', '2020-03-12', 'G001'),
('E007', 'Rowing Machine', 'Operational', '2023-02-08', 'G003'),
('E008', 'Leg Press Machine', 'Operational', '2022-12-18', 'G002'),
('E009', 'Chest Press Machine', 'Operational', '2021-05-30', 'G001'),
('E010', 'Lat Pulldown Machine', 'Operational', '2023-01-01', 'G003'),
('E011', 'Cable Crossover Machine', 'Operational', '2020-07-14', 'G002'),
('E012', 'Kettlebell Set', 'Operational', '2018-10-23', 'G001'),
('E013', 'Resistance Bands', 'Operational', '2023-04-05', 'G003'),
('E014', 'Yoga Mats', 'Operational', '2022-09-09', 'G002'),
('E015', 'Foam Rollers', 'Operational', '2019-12-20', 'G001'),
('E016', 'Treadmill', 'Operational', '2022-01-10', 'G004'),
('E017', 'Elliptical Machine', 'Under Maintenance', '2021-11-15', 'G004'),
('E018', 'Stationary Bike', 'Operational', '2020-09-05', 'G005'),
('E019', 'Dumbbell Set', 'Operational', '2019-08-20', 'G006'),
('E020', 'Barbell Set', 'Operational', '2021-06-25', 'G005'),
('E021', 'Smith Machine', 'Under Maintenance', '2020-03-12', 'G004'),
('E022', 'Rowing Machine', 'Operational', '2023-02-08', 'G006'),
('E023', 'Leg Press Machine', 'Operational', '2022-12-18', 'G005'),
('E024', 'Chest Press Machine', 'Operational', '2021-05-30', 'G004'),
('E025', 'Lat Pulldown Machine', 'Operational', '2023-01-01', 'G006'),
('E026', 'Cable Crossover Machine', 'Operational', '2020-07-14', 'G005'),
('E027', 'Kettlebell Set', 'Operational', '2018-10-23', 'G004'),
('E028', 'Resistance Bands', 'Operational', '2023-04-05', 'G006'),
('E029', 'Yoga Mats', 'Operational', '2022-09-09', 'G005'),
('E030', 'Foam Rollers', 'Operational', '2019-12-20', 'G004');

SELECT *
FROM Equipment;
-- -----------------------------------------------------
-- Table `mydb`.`Surveys`
-- -----------------------------------------------------

CREATE TABLE IF NOT EXISTS Surveys(
  `surveyID` VARCHAR(10) NOT NULL,
  `dateSubmitted` DATE NULL,
  `rating` VARCHAR(1) NULL,
  `Classes_classID` VARCHAR(10) NOT NULL,
  PRIMARY KEY (`surveyID`),
  INDEX `fk_Surveys_Classes1_idx` (`Classes_classID` ASC) VISIBLE,
  CONSTRAINT `fk_Surveys_Classes1`
    FOREIGN KEY (`Classes_classID`)
    REFERENCES `ns_Sp25_21482_Group1`.`Classes` (`classID`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;

INSERT INTO Surveys(surveyID, dateSubmitted, rating, Classes_classID) VALUES #NEED CLASSID VALUES
('5001', '2025-02-10', '5', NULL),
('5002','2025-02-11','4', NULL),
('5003','2025-02-12','3', NULL),
('5004', '2025-02-13','5', NULL),
('5005', '2025-02-14', '2', NULL),
('5006', '2025-02-15','4', NULL),
('5007','2025-02-16', '5', NULL);


Members: 

Scenario Description:

Data Model (Image):

Data Dictionary:

Ten Queries(6 complex 4 simple):

