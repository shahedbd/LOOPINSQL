# LOOP IN SQL with MSSQL data insert example.

```SQL
USE [DevTest] 
GO

---Create Table****************** 
/****** Object:  Table [dbo].[Customers]    Script Date: 7/18/2017 11:42:47 PM ******/ 
SET ANSI_NULLS ON 
GO 

SET QUOTED_IDENTIFIER ON 
GO

SET ANSI_PADDING ON 
GO 

CREATE TABLE [dbo].[Customers]( 
	[CustomerID] [int] IDENTITY(1,1) NOT NULL, 
	[CustomerName] [varchar](50) NULL, 
	[CustomerEmail] [varchar](50) NULL, 
	[CustomerZipCode] [int] NULL, 
	[CustomerCountry] [varchar](50) NULL, 
	[CustomerCity] [varchar](50) NULL, 
 CONSTRAINT [PK_Customers] PRIMARY KEY CLUSTERED 
(
	[CustomerID] ASC 
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY] 
) ON [PRIMARY] 
GO 

SET ANSI_PADDING ON 
GO 


----truncate 
truncate table Customers 
---SQL loop insert 
DECLARE @ID int; 
SET @ID=0; 
WHILE @ID < 25 
BEGIN 
	insert into Customers values('Name ' + CAST(@ID AS VARCHAR),'email01@gmail.com',1240,'Country ' + CAST(@ID AS VARCHAR),'City ' + CAST(@ID AS VARCHAR)) 
	SET @ID = @ID + 1; 
END 
```

### Option-2 Bulck data insert for R&D
```SQL
/****** Object:  Table [dbo].[PersonalInfo]    Script Date: 4/19/2019 2:18:37 AM ******/
SET ANSI_NULLS ON
GO

SET QUOTED_IDENTIFIER ON
GO

CREATE TABLE [dbo].[PersonalInfo](
	[ID] [bigint] IDENTITY(1,1) NOT NULL,
	[FirstName] [nvarchar](max) NULL,
	[LastName] [nvarchar](max) NULL,
	[DateOfBirth] [datetime2](7) NULL,
	[City] [nvarchar](max) NULL,
	[Country] [nvarchar](max) NULL,
	[MobileNo] [nvarchar](max) NULL,
	[NID] [nvarchar](max) NULL,
	[Email] [nvarchar](max) NULL,
	[CreatedDate] [datetime2](7) NULL,
	[LastModifiedDate] [datetime2](7) NULL,
	[CreationUser] [nvarchar](max) NULL,
	[LastUpdateUser] [nvarchar](max) NULL,
	[Status] [tinyint] NOT NULL,
 CONSTRAINT [PK_PersonalInfo] PRIMARY KEY CLUSTERED 
(
	[ID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]

GO
```

### Bulck data insertion
```SQL
----truncate 
truncate table PersonalInfo
---SQL loop insert 
DECLARE @ID int =0; 
DECLARE @StartDate AS DATETIME = '1980-01-01' 
WHILE @ID < 20
BEGIN 
insert into PersonalInfo values('First Name ' + CAST(@ID AS nvarchar),'Last Name ' + CAST(@ID AS VARCHAR),dateadd(day,1, @StartDate), 
'City ' + CAST(@ID AS VARCHAR),'Country ' + CAST(@ID AS VARCHAR),ABS(CAST(NEWID() AS binary(12)) % 1000) + 5555, 
ABS(CAST(NEWID() AS binary(12)) % 1000) + 99998888,'email' + CAST(@ID AS nvarchar) +'@gmail.com',
GETDATE(),null,'Admin' + CAST(@ID AS VARCHAR),null,1) 
SET @ID = @ID + 1; 
set @StartDate=dateadd(day,1, @StartDate) 
END
```


### Select Table Row
```SQL
select ROW_NUMBER() over (order by ID ) as RN from CompanyList
```

### Add New Column as IDENTITY
```SQL
ALTER TABLE CompanyList ADD ID INT IDENTITY(1,1) 
GO 
```
