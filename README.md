# DBMS
# practice set 1,2 and 4 queries are related to given table here
CREATE TABLE dept_class154(
    DEPTNO NUMBER primary key,
    DNAME varchar(15) NOT NULL,
    LOC varchar(15)
);

desc dept_class154;

INSERT INTO dept_class154 VALUES (10, 'ACCOUNTING','NEW YORK');
INSERT INTO dept_class154 VALUES (20,'RESEARCH','DALLAS');
INSERT INTO dept_class154 VALUES (30,'SALES','CHICAGO');
INSERT INTO dept_class154 VALUES (40,'OPERATIONS','BOSTON');

SELECT * FROM dept_class154;

CREATE TABLE EMP_154(
    EMNO NUMBER primary key,
    EMNAME varchar(15) NOT NULL,
    JOB varchar(15),
    MGR NUMBER,
    HIREDATE DATE,
    SAL NUMBER NOT NULL,
    CIMM NUMBER,
    DEPTNO NUMBER REFERENCES DEPT_CLASS154
);

desc EMP_154;

INSERT INTO EMP_154 VALUES (7839,'KING', 'PRESIDENT','','NOV-17-81',5000,'', 10);
INSERT INTO EMP_154 VALUES (7698,'BLAKE', 'MANAGER',7839,'MAY-01-81',2850,'', 30);
INSERT INTO EMP_154 VALUES (7782,'CLARK', 'MANAGER',7839,'JUN-09-81',2450,'', 10);
INSERT INTO EMP_154 VALUES (7566,'JONES', 'MANAGER',7839,'APR-19-81',2975,'', 20);
INSERT INTO EMP_154 VALUES (7788,'SCOTT', 'ANALYST',7766,'APR-19-87',3000,'', 20);
INSERT INTO EMP_154 VALUES (7902,'FORD', 'ANALYST',7566,'DEC-17-81',3000,'', 20);
INSERT INTO EMP_154 VALUES (7369,'SMITH', 'CLERK',7902,'DEC-20-80',800,'', 20);
INSERT INTO EMP_154 VALUES (7499,'ALLEN', 'SALESMAN',7698,'FEB-20-81',1600,300, 30);

# practice set 3 queries are related to given table here

CREATE TABLE Client_master(
    client_no VARCHAR2(6) PRIMARY KEY CHECK (client_no LIKE 'C%'),
    name varchar2(20) NOT NULL,
    address1 varchar2(30),
    address2 varchar2(30),
    city varchar2(15),
    state varchar2(15),
    pincode number(8),
    bal_due number(10,2)
);
INSERT INTO client_master (client_no, name, city, pincode, state, bal_due)
VALUES ('C00001', 'Ivan Bayross', 'Bombay', '400054', 'Maharashtra', 15000);

INSERT INTO client_master (client_no, name, city, pincode, state, bal_due)
VALUES ('C00002', 'Vandana Saitwal', 'Madras', '780001', 'Tamil Nadu', 0);

INSERT INTO client_master (client_no, name, city, pincode, state, bal_due)
VALUES ('C00003', 'Pramada Jaguste', 'Bombay', '400057', 'Maharashtra', 5000);

INSERT INTO client_master (client_no, name, city, pincode, state, bal_due)
VALUES ('C00004', 'Basu Navindgi', 'Bombay', '400056', 'Maharashtra', 0);

INSERT INTO client_master (client_no, name, city, pincode, state, bal_due)
VALUES ('C00005', 'Ravi Sreedharan', 'Delhi', '100001', 'Delhi', 2000);

INSERT INTO client_master (client_no, name, city, pincode, state, bal_due)
VALUES ('C00006', 'Rukmini', 'Bombay', '400050', 'Maharashtra', 0);

Drop table product_master;
Drop table sales_order_details;
CREATE TABLE product_master (
    product_no VARCHAR2(6) PRIMARY KEY CHECK (product_no LIKE 'P%'),
    description VARCHAR2(50) NOT NULL,
    profit_percent NUMBER(4,2) NOT NULL,
    unit_measure VARCHAR2(10) NOT NULL,
    qty_on_hand NUMBER(8) NOT NULL,
    reorder_lvl NUMBER(8) NOT NULL,
    sell_price NUMBER(8,2) NOT NULL CHECK (sell_price <> 0),
    cost_price NUMBER(8,2) NOT NULL CHECK (cost_price <> 0)
);
INSERT INTO product_master
VALUES ('P00001', '1.44 Floppies', 5, 'Piece', 100, 20, 525, 500);

INSERT INTO product_master
VALUES ('P03453', 'Monitors', 6, 'Piece', 10, 3, 12000, 11280);

INSERT INTO product_master
VALUES ('P06734', 'Mouse', 5, 'Piece', 20, 5, 1050, 1000);

INSERT INTO product_master 
VALUES ('P07865', '1.22 Floppies', 5, 'Piece', 100, 20, 525, 500);

INSERT INTO product_master
VALUES ('P07868', 'Keyboards', 2, 'Piece', 10, 3, 3150, 3050);

INSERT INTO product_master
VALUES ('P07885', 'CD Drive', 2.5, 'Piece', 10, 3, 5250, 5100);

INSERT INTO product_master
VALUES ('P07965', '540 HDD', 4, 'Piece', 10, 3, 8400, 8000);

INSERT INTO product_master 
VALUES ('P07975', '1.44 Drive', 5, 'Piece', 10, 3, 1050, 1000);

INSERT INTO product_master 
VALUES ('P08865', '1.22 Drive', 5, 'Piece', 2, 3, 1050, 1000);

CREATE TABLE salesman_master (
    salesman_no VARCHAR2(6) PRIMARY KEY CHECK (salesman_no LIKE 'S%'),
    salesman_name varchar2(20) NOT NULL,
    address1 varchar2(30) NOT NULL,
    address2 varchar2(30),
    city varchar2(20),
    pincode varchar2(8),
    state varchar2(20),
    sal_amt Number(8,2) NOT NULL CHECK (sal_amt <> 0),
    tgt_to_get Number(6,2) NOT NULL CHECK (tgt_to_get <> 0),
    ytd_sales Number(6,2) NOT NULL,
    remarks varchar2(60)
);
INSERT INTO salesman_master (salesman_no, salesman_name, address1, address2, city, pincode, state, sal_amt, tgt_to_get, ytd_sales, remarks)
VALUES ('S00001', 'Kirar', 'A/14', 'Worli', 'Bombay', '400002', 'Maharashtra', 3000, 100, 50, 'Good');

INSERT INTO salesman_master (salesman_no, salesman_name, address1, address2, city, pincode, state, sal_amt, tgt_to_get, ytd_sales, remarks)
VALUES ('S00002', 'Manish', '65', 'Nariman', 'Bombay', '400001', 'Maharashtra', 3000, 200, 100, 'Good');

INSERT INTO salesman_master (salesman_no, salesman_name, address1, address2, city, pincode, state, sal_amt, tgt_to_get, ytd_sales, remarks)
VALUES ('S00003', 'Ravi', 'P-7', 'Bandra', 'Bombay', '400032', 'Maharashtra', 3000, 200, 100, 'Good');

INSERT INTO salesman_master (salesman_no, salesman_name, address1, address2, city, pincode, state, sal_amt, tgt_to_get, ytd_sales, remarks)
VALUES ('S00004', 'Ashish', 'A/5', 'Juhu', 'Bombay', '400044', 'Maharashtra', 3500, 200, 150, 'Good');

CREATE TABLE sales_order (
    order_no VARCHAR2(6) PRIMARY KEY CHECK (order_no LIKE 'O%'),
    order_date DATE,
    client_no VARCHAR2(6),
    dely_addr VARCHAR2(25),
    salesman_no VARCHAR2(6),
    dely_type CHAR(1) DEFAULT 'F' CHECK (dely_type IN ('P', 'F')),
    billed_yn CHAR(1),
    dely_date DATE,
    order_status VARCHAR2(10) CHECK (order_status IN ('In Process', 'Fulfilled', 'BackOrder', 'Cancelled')),
    FOREIGN KEY (client_no) REFERENCES Client_master(client_no),
    FOREIGN KEY (salesman_no) REFERENCES salesman_master(salesman_no)
);
CREATE OR REPLACE TRIGGER check_dely_date
BEFORE INSERT OR UPDATE ON sales_order
FOR EACH ROW
BEGIN
    IF :NEW.dely_date < :NEW.order_date THEN
        RAISE_APPLICATION_ERROR(-20001, 'Delivery date cannot be less than order date');
    END IF;
END;
INSERT INTO sales_order (order_no, order_date, client_no, dely_type, billed_yn, salesman_no, dely_date, order_status)
VALUES ('O19001', TO_DATE('12-Jan-96', 'DD-Mon-YY'), 'C00001', 'F', 'N', 'S00001', TO_DATE('20-Jan-96', 'DD-Mon-YY'), 'In Process');

INSERT INTO sales_order (order_no, order_date, client_no, dely_type, billed_yn, salesman_no, dely_date, order_status)
VALUES ('O19002', TO_DATE('25-Jan-96', 'DD-Mon-YY'), 'C00002', 'P', 'N', 'S00002', TO_DATE('27-Jan-96', 'DD-Mon-YY'), 'Cancelled');

INSERT INTO sales_order (order_no, order_date, client_no, dely_type, billed_yn, salesman_no, dely_date, order_status)
VALUES ('O46865', TO_DATE('18-Feb-96', 'DD-Mon-YY'), 'C00003', 'F', 'Y', 'S00003', TO_DATE('20-Feb-96', 'DD-Mon-YY'), 'Fulfilled');

INSERT INTO sales_order (order_no, order_date, client_no, dely_type, billed_yn, salesman_no, dely_date, order_status)
VALUES ('O19003', TO_DATE('03-Apr-96', 'DD-Mon-YY'), 'C00001', 'F', 'Y', 'S00001', TO_DATE('07-Apr-96', 'DD-Mon-YY'), 'Fulfilled');

INSERT INTO sales_order (order_no, order_date, client_no, dely_type, billed_yn, salesman_no, dely_date, order_status)
VALUES ('O46866', TO_DATE('20-May-96', 'DD-Mon-YY'), 'C00004', 'P', 'N', 'S00002', TO_DATE('22-May-96', 'DD-Mon-YY'), 'Cancelled');

INSERT INTO sales_order (order_no, order_date, client_no, dely_type, billed_yn, salesman_no, dely_date, order_status)
VALUES ('O19008', TO_DATE('24-May-96', 'DD-Mon-YY'), 'C00005', 'F', 'N', 'S00004', TO_DATE('26-May-96', 'DD-Mon-YY'), 'In Process');

CREATE TABLE sales_order_details (
    order_no VARCHAR2(6),
    product_no VARCHAR2(6),
    qty_ordered NUMBER(8),
    qty_disp NUMBER(8),
    product_rate NUMBER(10,2),
    PRIMARY KEY (order_no, product_no),
    FOREIGN KEY (order_no) REFERENCES sales_order(order_no),
    FOREIGN KEY (product_no) REFERENCES product_master(product_no)
);
INSERT INTO sales_order_details (order_no, product_no, qty_ordered, qty_disp, product_rate)
VALUES ('O19001', 'P00001', 4, 4, 525);

INSERT INTO sales_order_details (order_no, product_no, qty_ordered, qty_disp, product_rate)
VALUES ('O19001', 'P07965', 2, 1, 8400);

INSERT INTO sales_order_details (order_no, product_no, qty_ordered, qty_disp, product_rate)
VALUES ('O19001', 'P07885', 2, 1, 5250);

INSERT INTO sales_order_details (order_no, product_no, qty_ordered, qty_disp, product_rate)
VALUES ('O19002', 'P00001', 10, 0, 525);

INSERT INTO sales_order_details (order_no, product_no, qty_ordered, qty_disp, product_rate)
VALUES ('O46865', 'P07868', 3, 3, 3150);

INSERT INTO sales_order_details (order_no, product_no, qty_ordered, qty_disp, product_rate)
VALUES ('O46865', 'P07885', 3, 1, 5250);

INSERT INTO sales_order_details (order_no, product_no, qty_ordered, qty_disp, product_rate)
VALUES ('O46865', 'P00001', 10, 10, 525);

INSERT INTO sales_order_details (order_no, product_no, qty_ordered, qty_disp, product_rate)
VALUES ('O46865', 'P03453', 4, 4, 1050);

INSERT INTO sales_order_details (order_no, product_no, qty_ordered, qty_disp, product_rate)
VALUES ('O19003', 'P03453', 2, 2, 1050);

INSERT INTO sales_order_details (order_no, product_no, qty_ordered, qty_disp, product_rate)
VALUES ('O19003', 'P06734', 1, 1, 12000);

INSERT INTO sales_order_details (order_no, product_no, qty_ordered, qty_disp, product_rate)
VALUES ('O46866', 'P07965', 1, 0, 8400);

INSERT INTO sales_order_details (order_no, product_no, qty_ordered, qty_disp, product_rate)
VALUES ('O46866', 'P07975', 1, 0, 1050);

INSERT INTO sales_order_details (order_no, product_no, qty_ordered, qty_disp, product_rate)
VALUES ('O19008', 'P00001', 10, 5, 525);

INSERT INTO sales_order_details (order_no, product_no, qty_ordered, qty_disp, product_rate)
VALUES ('O19008', 'P07975', 5, 3, 1050);

SELECT * FROM sales_order_details;
INSERT INTO EMP_154 VALUES (7521,'WARD', 'SALESMAN',7698,'FEB-22-81',1250,500, 30);
INSERT INTO EMP_154 VALUES (7654,'MARTIN', 'SALESMAN',7698,'SEP-28-81',1250,1400, 30);
INSERT INTO EMP_154 VALUES (7844,'TURNER', 'SALESMAN',7698,'SEP-08-81',1500,0, 30);
INSERT INTO EMP_154 VALUES (7876,'ADMS', 'CLERK',7688,'MAY-23-87',1100,'', 20);
INSERT INTO EMP_154 VALUES (7900,'JAMES', 'CLERK',7698,'DEC-03-81',950,'', 30);
INSERT INTO EMP_154 VALUES (7934,'MILLER', 'CLERK',7782,'JAN-23-82',1300,'', 10);
