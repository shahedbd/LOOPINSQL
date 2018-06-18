# LOOP IN SQL with MSSQL data insert example.

USE [DevTest] <br />
GO

---Create Table****************** <br />
/****** Object:  Table [dbo].[Customers]    Script Date: 7/18/2017 11:42:47 PM ******/ <br />
SET ANSI_NULLS ON <br />
GO <br />

SET QUOTED_IDENTIFIER ON <br />
GO

SET ANSI_PADDING ON <br />
GO <br />

CREATE TABLE [dbo].[Customers]( <br />
	[CustomerID] [int] IDENTITY(1,1) NOT NULL, <br />
	[CustomerName] [varchar](50) NULL, <br />
	[CustomerEmail] [varchar](50) NULL, <br />
	[CustomerZipCode] [int] NULL, <br />
	[CustomerCountry] [varchar](50) NULL, <br />
	[CustomerCity] [varchar](50) NULL, <br />
 CONSTRAINT [PK_Customers] PRIMARY KEY CLUSTERED <br />
(
	[CustomerID] ASC <br />
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY] <br />
) ON [PRIMARY] <br />
GO <br />

SET ANSI_PADDING ON <br />
GO <br />


----truncate <br />
truncate table Customers <br />
---SQL loop insert <br />
DECLARE @ID int; <br />
SET @ID=0; <br />
WHILE @ID < 25 <br />
BEGIN <br />
	insert into Customers values('Name ' + CAST(@ID AS VARCHAR),'email01@gmail.com',1240,'Country ' + CAST(@ID AS VARCHAR),'City ' + CAST(@ID AS VARCHAR)) <br />
	SET @ID = @ID + 1; <br />
END <br />


## Option-2 Bulck data insert for R&D

#### Table script <br />
USE [DevTest] <br />
GO <br />
/****** Object:  Table [dbo].[PersonalInfo]    Script Date: 6/18/2018 1:13:01 PM ******/ <br />
SET ANSI_NULLS ON <br />
GO <br />
SET QUOTED_IDENTIFIER ON <br />
GO <br />
CREATE TABLE [dbo].[PersonalInfo]( <br />
	[PersonalInfoID] [bigint] IDENTITY(1,1) NOT NULL, <br />
	[FirstName] [nvarchar](150) NULL, <br />
	[LastName] [nvarchar](150) NULL, <br />
	[DateOfBirth] [datetime] NULL, <br />
	[City] [nvarchar](150) NULL, <br />
	[Country] [nvarchar](150) NULL, <br />
	[MobileNo] [nvarchar](150) NULL, <br />
	[NID] [nvarchar](150) NULL, <br />
	[Email] [nvarchar](150) NULL, <br />
	[Status] [tinyint] NULL, <br />
 CONSTRAINT [PK_PersonalInfo] PRIMARY KEY CLUSTERED <br />
( <br />
	[PersonalInfoID] ASC <br />
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY] <br />
) ON [PRIMARY] <br />

GO <br />

#### Bulck data insertion
----truncate <br />
truncate table PersonalInfo <br />
---SQL loop insert <br />
DECLARE @ID int =0; <br />
DECLARE @StartDate AS DATETIME = '1980-01-01' <br />
WHILE @ID < 200000 <br />
BEGIN  <br />
insert into PersonalInfo values('First Name ' + CAST(@ID AS nvarchar),'Last Name ' + CAST(@ID AS VARCHAR),dateadd(day,1, @StartDate), <br />
'City ' + CAST(@ID AS VARCHAR),'Country ' + CAST(@ID AS VARCHAR),ABS(CAST(NEWID() AS binary(12)) % 1000) + 111111, <br />
ABS(CAST(NEWID() AS binary(12)) % 1000) + 999999999,'email' + CAST(@ID AS nvarchar) +'@gmail.com',1)  <br />
SET @ID = @ID + 1; <br />
set @StartDate=dateadd(day,1, @StartDate) <br />
END  <br />








