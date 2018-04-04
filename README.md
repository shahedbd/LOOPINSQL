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

