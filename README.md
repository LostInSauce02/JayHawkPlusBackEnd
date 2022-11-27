# JayHawkPlusBackend

Hello, this ReadMe is for the JayHawk+ Backend Implementation for the JayHawk+ Web Application. All of the follwing source code is placed within the zip file. I will discuss how to setup the database with the respective tables for this backend solution to work.

**Depedencies**
- .NET Core 3.1
- MS Visual Studios
- NO CORS Chrome (https://alfilatov.com/posts/run-chrome-without-cors/#:~:text=Run%20Chrome%20browser%20without%20CORS%201%20Windows%20Just,will%20get%20an%20error%20message%20that%20says%3A%20)

**SQL Express Database**

Before we create the respective tables, we need to create a SQL Express Database within MS Visual Studios. You can achieve this by clicking on the view tab and selecting Server Explorer in MS Visual Studios. Then right click on Data Connections, where you should be able to add a new connection for a local database.

**AUTH Table**

Use the follwing SQL Code generate a proper configuration for the AUTH table.

_SQL CODE:_

    CREATE TABLE [dbo].[AUTH] (
   
    [username]   VARCHAR (50) NOT NULL,
    
    [password]   VARCHAR (50) NOT NULL,
   
    [patient_id] INT          NOT NULL,
    
    PRIMARY KEY CLUSTERED ([username] ASC),
    
    CONSTRAINT [uk_patient_id] UNIQUE NONCLUSTERED ([patient_id] ASC)
    );

**PATIENTS Table**

Use the follwing SQL Code generate a proper configuration for the AUTH table.

_SQL CODE:_

    CREATE TABLE [dbo].[PATIENTS] (
    
    [patient_id]        INT       NOT NULL,
    
    [patient_firstname] CHAR (35) NOT NULL,
    
    [patient_lastname]  CHAR (35) NOT NULL,
    
    PRIMARY KEY CLUSTERED ([patient_id] ASC),
    
    CONSTRAINT [FK_P_ID] FOREIGN KEY ([patient_id]) REFERENCES [dbo].[AUTH] ([patient_id])
    );

**DOCTORS Table**

Use the follwing SQL Code generate a proper configuration for the AUTH table.

_SQL CODE:_

    CREATE TABLE [dbo].[DOCTORS] (
    
    [doc_id]         INT       IDENTITY (1, 1) NOT NULL,
    
    [doc_username]   CHAR (35) NOT NULL,
    
    [doc_password]   CHAR (35) NOT NULL,
    
    [doc_name]       CHAR (35) NOT NULL,
    
    [doc_speciality] CHAR (35) NOT NULL,
    
    PRIMARY KEY CLUSTERED ([doc_id] ASC)
    );

**APPOINTMENTS Table**

Use the follwing SQL Code generate a proper configuration for the AUTH table.

_SQL CODE:_

    CREATE TABLE [dbo].[APPOINTMENTS] (
    
    [patient_id] INT        NOT NULL,
    
    [appt_id]    INT        NOT NULL,
    
    [appt_date]  CHAR (35)  NOT NULL,
    
    [appt_time]  CHAR (35)  NOT NULL,
    
    [appt_notes] CHAR (180) NOT NULL,
    
    [doc_id]     INT        NOT NULL,
    
    CONSTRAINT [PK_APPT] PRIMARY KEY CLUSTERED ([patient_id] ASC, [appt_id] ASC),
    
    CONSTRAINT [FK_APPT_PATIENT_ID] FOREIGN KEY ([patient_id]) REFERENCES [dbo].[AUTH] ([patient_id]),
    
    CONSTRAINT [FK_DOC_ID] FOREIGN KEY ([doc_id]) REFERENCES [dbo].[DOCTORS] ([doc_id])
    );

**ADMINISTRATION Table**

Use the follwing SQL Code generate a proper configuration for the AUTH table.

_SQL CODE:_

    CREATE TABLE [dbo].[ADMINISTRATION] (
    
    [admin_id]       INT       IDENTITY (1, 1) NOT NULL,
    
    [admin_username] CHAR (35) NOT NULL,
    
    [admin_password] CHAR (35) NOT NULL,
    
    PRIMARY KEY CLUSTERED ([admin_id] ASC)
    );


