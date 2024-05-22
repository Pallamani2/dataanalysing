for creating HR table schemas
  CREATE TABLE "HR"."DAILY_EXPENSES" 
   (	"SPEND_DATE" DATE, 
	"PURPOSE" VARCHAR2(128 BYTE), 
	"INCOME" VARCHAR2(26 BYTE), 
	"EXPENSE" VARCHAR2(26 BYTE), 
	"CATEGORY" VARCHAR2(26 BYTE), 
	"DESCRIPTION" NUMBER(38,0), 
	"ACCOUNT" VARCHAR2(26 BYTE), 
	"EXPENSE_NUMBER" NUMBER(*,0)
   ) SEGMENT CREATION IMMEDIATE 
  PCTFREE 10 PCTUSED 40 INITRANS 1 MAXTRANS 255 NOCOMPRESS LOGGING
  STORAGE(INITIAL 65536 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645
  PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1 BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT)
  TABLESPACE "USERS" ;
  for crop data 
  
  CREATE TABLE "HR"."CROP_DATA" 
   (	"CROP_ID" NUMBER(*,0), 
	"CROP_NAME" VARCHAR2(50 BYTE), 
	"CROP_TYPE" VARCHAR2(50 BYTE), 
	"GROWTH_STAGE" VARCHAR2(50 BYTE), 
	"PEST_TYPE" VARCHAR2(50 BYTE), 
	"FERTILIZER_TYPE" VARCHAR2(50 BYTE), 
	"YIELD_QUANTITY" NUMBER(*,0), 
	"HARVEST_DATE" DATE, 
	 PRIMARY KEY ("CROP_ID")
  USING INDEX PCTFREE 10 INITRANS 2 MAXTRANS 255 COMPUTE STATISTICS 
  STORAGE(INITIAL 65536 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645
  PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1 BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT)
  TABLESPACE "USERS"  ENABLE
   ) SEGMENT CREATION IMMEDIATE 
  PCTFREE 10 PCTUSED 40 INITRANS 1 MAXTRANS 255 NOCOMPRESS LOGGING
  STORAGE(INITIAL 65536 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645
  PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1 BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT)
  TABLESPACE "USERS" ;
for DIM_CUSTOMER

  CREATE TABLE "HR"."DIM_CUSTOMER" 
   (	"CUSTOMER_SK" NUMBER, 
	"CUSTOMER_ID" VARCHAR2(50 BYTE) NOT NULL ENABLE, 
	"CUSTOMER_NAME" VARCHAR2(100 BYTE), 
	"ADDRESS" VARCHAR2(255 BYTE), 
	 PRIMARY KEY ("CUSTOMER_SK")
  USING INDEX PCTFREE 10 INITRANS 2 MAXTRANS 255 COMPUTE STATISTICS 
  STORAGE(INITIAL 65536 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645
  PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1 BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT)
  TABLESPACE "USERS"  ENABLE
   ) SEGMENT CREATION IMMEDIATE 
  PCTFREE 10 PCTUSED 40 INITRANS 1 MAXTRANS 255 NOCOMPRESS LOGGING
  STORAGE(INITIAL 65536 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645
  PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1 BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT)
  TABLESPACE "USERS" ;
  for  FCT_CREDIT_CARD
  
  CREATE TABLE "HR"."FCT_CREDIT_CARD" 
   (	"CREDIT_CARD_SK" NUMBER, 
	"CUSTOMER_SK" NUMBER, 
	"DATE_SK" NUMBER, 
	"CARD_NUMBER" VARCHAR2(50 BYTE), 
	"BALANCE" NUMBER, 
	"MERCHANT" VARCHAR2(100 BYTE), 
	"TRANSACTION_ID" VARCHAR2(50 BYTE), 
	"CREDIT_CARD_LIMIT" VARCHAR2(20 BYTE), 
	 PRIMARY KEY ("CREDIT_CARD_SK")
  USING INDEX PCTFREE 10 INITRANS 2 MAXTRANS 255 COMPUTE STATISTICS 
  STORAGE(INITIAL 65536 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645
  PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1 BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT)
  TABLESPACE "USERS"  ENABLE, 
	 FOREIGN KEY ("CUSTOMER_SK")
	  REFERENCES "HR"."DIM_CUSTOMER" ("CUSTOMER_SK") ENABLE, 
	 FOREIGN KEY ("DATE_SK")
	  REFERENCES "HR"."DIM_DATE" ("DATE_SK") ENABLE
   ) SEGMENT CREATION IMMEDIATE 
  PCTFREE 10 PCTUSED 40 INITRANS 1 MAXTRANS 255 NOCOMPRESS LOGGING
  STORAGE(INITIAL 65536 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645
  PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1 BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT)
  TABLESPACE "USERS" ;
  for   FCT_HEALTH_INSURANCE
    CREATE TABLE "HR"."FCT_HEALTH_INSURANCE" 
   (	"HEALTH_INSURANCE_SK" NUMBER, 
	"CUSTOMER_SK" NUMBER, 
	"DATE_SK" NUMBER, 
	"PREMIUM_PAYMENT" NUMBER, 
	"CLAIM_ID" VARCHAR2(50 BYTE), 
	"MEMBERS_COVERED" NUMBER(*,0), 
	"HOSPITAL" VARCHAR2(100 BYTE), 
	 PRIMARY KEY ("HEALTH_INSURANCE_SK")
  USING INDEX PCTFREE 10 INITRANS 2 MAXTRANS 255 COMPUTE STATISTICS 
  STORAGE(INITIAL 65536 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645
  PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1 BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT)
  TABLESPACE "USERS"  ENABLE, 
	 FOREIGN KEY ("CUSTOMER_SK")
	  REFERENCES "HR"."DIM_CUSTOMER" ("CUSTOMER_SK") ENABLE, 
	 FOREIGN KEY ("DATE_SK")
	  REFERENCES "HR"."DIM_DATE" ("DATE_SK") ENABLE
   ) SEGMENT CREATION IMMEDIATE 
  PCTFREE 10 PCTUSED 40 INITRANS 1 MAXTRANS 255 NOCOMPRESS LOGGING
  STORAGE(INITIAL 65536 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645
  PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1 BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT)
  TABLESPACE "USERS" ;

for FCT_INVESTMENT

  CREATE TABLE "HR"."FCT_INVESTMENT" 
   (	"INVESTMENT_SK" NUMBER, 
	"CUSTOMER_SK" NUMBER, 
	"DATE_SK" NUMBER, 
	"DMAT_ACCOUNT_NUMBER" VARCHAR2(50 BYTE), 
	"HOLDING" NUMBER, 
	"TRADING_TRANSACTION_ID" VARCHAR2(50 BYTE), 
	"BROKER" VARCHAR2(100 BYTE), 
	"STOCK_SYMBOL" VARCHAR2(50 BYTE), 
	"EXCHANGE" VARCHAR2(100 BYTE), 
	 PRIMARY KEY ("INVESTMENT_SK")
  USING INDEX PCTFREE 10 INITRANS 2 MAXTRANS 255 COMPUTE STATISTICS 
  STORAGE(INITIAL 65536 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645
  PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1 BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT)
  TABLESPACE "USERS"  ENABLE, 
	 FOREIGN KEY ("CUSTOMER_SK")
	  REFERENCES "HR"."DIM_CUSTOMER" ("CUSTOMER_SK") ENABLE, 
	 FOREIGN KEY ("DATE_SK")
	  REFERENCES "HR"."DIM_DATE" ("DATE_SK") ENABLE
   ) SEGMENT CREATION IMMEDIATE 
  PCTFREE 10 PCTUSED 40 INITRANS 1 MAXTRANS 255 NOCOMPRESS LOGGING
  STORAGE(INITIAL 65536 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645
  PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1 BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT)
  TABLESPACE "USERS" ;

  for FCT_LOAN
    CREATE TABLE "HR"."FCT_LOAN" 
   (	"LOAN_SK" NUMBER, 
	"CUSTOMER_SK" NUMBER, 
	"DATE_SK" NUMBER, 
	"LOAN_TYPE" VARCHAR2(50 BYTE), 
	"BALANCE" NUMBER, 
	"DISBURSEMENT" NUMBER, 
	"EMI_PAYMENT" NUMBER, 
	"BRANCH" VARCHAR2(100 BYTE), 
	"INTEREST_RATE" NUMBER, 
	"LOAN_LIMIT" VARCHAR2(20 BYTE), 
	 PRIMARY KEY ("LOAN_SK")
  USING INDEX PCTFREE 10 INITRANS 2 MAXTRANS 255 COMPUTE STATISTICS 
  STORAGE(INITIAL 65536 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645
  PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1 BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT)
  TABLESPACE "USERS"  ENABLE, 
	 FOREIGN KEY ("CUSTOMER_SK")
	  REFERENCES "HR"."DIM_CUSTOMER" ("CUSTOMER_SK") ENABLE, 
	 FOREIGN KEY ("DATE_SK")
	  REFERENCES "HR"."DIM_DATE" ("DATE_SK") ENABLE
   ) SEGMENT CREATION IMMEDIATE 
  PCTFREE 10 PCTUSED 40 INITRANS 1 MAXTRANS 255 NOCOMPRESS LOGGING
  STORAGE(INITIAL 65536 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645
  PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1 BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT)
  TABLESPACE "USERS" ;


  for  FCT_SAVINGS_ACCOUNT


    CREATE TABLE "HR"."FCT_SAVINGS_ACCOUNT" 
   (	"SAVINGS_ACCOUNT_SK" NUMBER, 
	"CUSTOMER_SK" NUMBER, 
	"DATE_SK" NUMBER, 
	"ACCOUNT_NUMBER" VARCHAR2(50 BYTE), 
	"BALANCE" NUMBER, 
	"BRANCH" VARCHAR2(100 BYTE), 
	"DEBIT_CARD_NUMBER" VARCHAR2(50 BYTE), 
	"TRANSACTION_ID" VARCHAR2(50 BYTE), 
	 PRIMARY KEY ("SAVINGS_ACCOUNT_SK")
  USING INDEX PCTFREE 10 INITRANS 2 MAXTRANS 255 COMPUTE STATISTICS 
  STORAGE(INITIAL 65536 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645
  PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1 BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT)
  TABLESPACE "USERS"  ENABLE, 
	 FOREIGN KEY ("CUSTOMER_SK")
	  REFERENCES "HR"."DIM_CUSTOMER" ("CUSTOMER_SK") ENABLE, 
	 FOREIGN KEY ("DATE_SK")
	  REFERENCES "HR"."DIM_DATE" ("DATE_SK") ENABLE
   ) SEGMENT CREATION IMMEDIATE 
  PCTFREE 10 PCTUSED 40 INITRANS 1 MAXTRANS 255 NOCOMPRESS LOGGING
  STORAGE(INITIAL 65536 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645
  PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1 BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT)
  TABLESPACE "USERS" ;
for VIDEO_GAME

  CREATE TABLE "HR"."VIDEO_GAME" 
   (	"TITLE" VARCHAR2(128 BYTE), 
	"RELEASE_DATE" DATE, 
	"DEVELOPER" VARCHAR2(128 BYTE), 
	"PUBLISHER" VARCHAR2(128 BYTE), 
	"GENRES" VARCHAR2(128 BYTE), 
	"GENRES_SPLITTED" VARCHAR2(128 BYTE), 
	"PRODUCT_RATING" VARCHAR2(128 BYTE), 
	"USER_SCORE" NUMBER(38,1), 
	"USER_RATINGS_COUNT" NUMBER(38,0), 
	"PLATFORMS_INFO" VARCHAR2(1024 BYTE)
   ) SEGMENT CREATION IMMEDIATE 
  PCTFREE 10 PCTUSED 40 INITRANS 1 MAXTRANS 255 NOCOMPRESS LOGGING
  STORAGE(INITIAL 65536 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645
  PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1 BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT)
  TABLESPACE "USERS" ;

--------------------------------------------------------
--  DDL for Table VIDEO_GAME
--------------------------------------------------------

  CREATE TABLE "HR"."VIDEO_GAME" 
   (	"TITLE" VARCHAR2(128 BYTE), 
	"RELEASE_DATE" DATE, 
	"DEVELOPER" VARCHAR2(128 BYTE), 
	"PUBLISHER" VARCHAR2(128 BYTE), 
	"GENRES" VARCHAR2(128 BYTE), 
	"GENRES_SPLITTED" VARCHAR2(128 BYTE), 
	"PRODUCT_RATING" VARCHAR2(128 BYTE), 
	"USER_SCORE" NUMBER(38,1), 
	"USER_RATINGS_COUNT" NUMBER(38,0), 
	"PLATFORMS_INFO" VARCHAR2(1024 BYTE)
   ) SEGMENT CREATION IMMEDIATE 
  PCTFREE 10 PCTUSED 40 INITRANS 1 MAXTRANS 255 NOCOMPRESS LOGGING
  STORAGE(INITIAL 65536 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645
  PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1 BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT)
  TABLESPACE "USERS" ;
