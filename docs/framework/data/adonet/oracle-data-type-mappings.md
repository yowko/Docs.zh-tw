---
title: "Oracle 資料型別 Mappings1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: adb0fc332e00e766a62d0af1c110c5a7ce2d42c3
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="oracle-data-type-mappings"></a>Oracle 資料類型對應
下表列出 Oracle 資料型別及其與 <xref:System.Data.OracleClient.OracleDataReader> 的對應。  
  
|Oracle 資料型別|OracleDataReader.GetValue 傳回的 .NET Framework 資料型別|OracleDataReader.GetOracleValue 傳回的 OracleClient 資料型別|備註|  
|----------------------|--------------------------------------------------------------------|------------------------------------------------------------------------|-------------|  
|**BFILE**|**Byte[]**|<xref:System.Data.OracleClient.OracleBFile>||  
|**BLOB**|**Byte[]**|<xref:System.Data.OracleClient.OracleLob>||  
|**CHAR**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**CLOB**|**String**|<xref:System.Data.OracleClient.OracleLob>||  
|**DATE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**FLOAT**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|此資料類型是一個別名**數目**資料型別，其設計目的是讓<xref:System.Data.OracleClient.OracleDataReader>傳回**System.Decimal**或<xref:System.Data.OracleClient.OracleNumber>而非浮點值。 使用 .NET Framework 資料型別會造成溢位。|  
|**INTEGER**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|此資料類型是一個別名**NUMBER(38)**資料型別，其設計目的是讓<xref:System.Data.OracleClient.OracleDataReader>傳回**System.Decimal**或<xref:System.Data.OracleClient.OracleNumber>而非整數值。 使用 .NET Framework 資料型別會造成溢位。|  
|**INTERVAL YEAR TO MONTH**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**INTERVAL DAY TO 第二個**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**LONG**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**長資料列**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**String**|<xref:System.Data.OracleClient.OracleLob>||  
|**NUMBER**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|使用 .NET Framework 資料型別會造成溢位。|  
|**NVARCHAR2**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**RAW**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**REF CURSOR**|||Oracle **REF CURSOR**所不支援資料類型<xref:System.Data.OracleClient.OracleDataReader>物件。|  
|**ROWID**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**TIMESTAMP**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**使用本地時區的時間戳記**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**時區的時間戳記**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**不帶正負號的整數**|**數字**|<xref:System.Data.OracleClient.OracleNumber>|此資料類型是一個別名**NUMBER(38)**資料型別，其設計目的是讓<xref:System.Data.OracleClient.OracleDataReader>傳回**System.Decimal**或<xref:System.Data.OracleClient.OracleNumber>而非不帶正負號的整數值。 使用 .NET Framework 資料型別會造成溢位。|  
|**VARCHAR2**|**String**|<xref:System.Data.OracleClient.OracleString>||  
  
 下表列出 Oracle 資料型別和.NET Framework 資料型別 (**System.Data.DbType**和<xref:System.Data.OracleClient.OracleType>) 當做參數進行繫結時使用。  
  
|Oracle 資料型別|要以參數來繫結的 DbType 列舉型別|要以參數來繫結的 OracleType 列舉型別|備註|  
|----------------------|-----------------------------------------------|---------------------------------------------------|-------------|  
|**BFILE**||**BFile**|Oracle 僅允許繫結**BFILE**為**BFILE**參數。 .NET Data Provider for Oracle 不會自動建構為您如果您嘗試繫結非**BFILE**值，例如**byte []**或<xref:System.Data.OracleClient.OracleBinary>。|  
|**BLOB**||**Blob**|Oracle 僅允許繫結**BLOB**為**BLOB**參數。 .NET Data Provider for Oracle 不會自動建構為您如果您嘗試繫結非**BLOB**值，例如**byte []**或<xref:System.Data.OracleClient.OracleBinary>。|  
|**CHAR**|**AnsiStringFixedLength**|**Char**||  
|**CLOB**||**Clob**|Oracle 僅允許繫結**CLOB**為**CLOB**參數。 .NET Data Provider for Oracle 不會自動建構為您如果您嘗試繫結非**CLOB**值，例如**System.String**或<xref:System.Data.OracleClient.OracleString>。|  
|**DATE**|**DateTime**|**DateTime**||  
|**FLOAT**|**Single、 Double、 Decimal**|**Float、 Double、 Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>決定**System.Data.DBType**和<xref:System.Data.OracleClient.OracleType>。|  
|**INTEGER**|**SByte、 Int16、 Int32、 Int64、 Decimal**|**SByte、 Int16、 Int32、 Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>決定**System.Data.DBType**和<xref:System.Data.OracleClient.OracleType>。|  
|**INTERVAL YEAR TO MONTH**|**Int32**|**IntervalYearToMonth**|只有當您同時使用 Oracle 9i 用戶端及伺服器軟體時，才可以使用 <xref:System.Data.OracleClient.OracleType>。|  
|**INTERVAL DAY TO 第二個**|**物件**|**IntervalDayToSecond**|只有當您同時使用 Oracle 9i 用戶端及伺服器軟體時，才可以使用 <xref:System.Data.OracleClient.OracleType>。|  
|**LONG**|**AnsiString**|**LongVarChar**||  
|**長資料列**|**Binary**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**NChar**||  
|**NCLOB**||**NClob**|Oracle 僅允許繫結**NCLOB**為**NCLOB**參數。 .NET Data Provider for Oracle 不會自動建構為您如果您嘗試繫結非**NCLOB**值，例如**System.String**或<xref:System.Data.OracleClient.OracleString>。|  
|**NUMBER**|**VarNumeric**|**數字**||  
|**NVARCHAR2**|**String**|**NVarChar**||  
|**RAW**|**Binary**|**Raw**||  
|**REF CURSOR**||**Cursor**|如需詳細資訊，請參閱[Oracle REF Cursor](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)。|  
|**ROWID**|**AnsiString**|**Rowid**||  
|**TIMESTAMP**|**DateTime**|**時間戳記**|只有當您同時使用 Oracle 9i 用戶端及伺服器軟體時，才可以使用 <xref:System.Data.OracleClient.OracleType>。|  
|**使用本地時區的時間戳記**|**DateTime**|**TimestampLocal**|只有當您同時使用 Oracle 9i 用戶端及伺服器軟體時，才可以使用 <xref:System.Data.OracleClient.OracleType>。|  
|**時區的時間戳記**|**DateTime**|**TimestampWithTz**|只有當您同時使用 Oracle 9i 用戶端及伺服器軟體時，才可以使用 <xref:System.Data.OracleClient.OracleType>。|  
|**不帶正負號的整數**|**Byte、 UInt16、 UInt32、 UInt64、 Decimal**|**Byte、 UInt16、 Uint32、 Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>決定**System.Data.DBType**和<xref:System.Data.OracleClient.OracleType>。|  
|**VARCHAR2**|**AnsiString**|**VarChar**||  
  
 **InputOutput**，**輸出**，和**ReturnValue** **ParameterDirection**所使用的值<xref:System.Data.OracleClient.OracleParameter.Value%2A>屬性<xref:System.Data.OracleClient.OracleParameter>物件會是.NET Framework 資料型別，除非輸入的值為 Oracle 資料類型 (例如，<xref:System.Data.OracleClient.OracleNumber>或<xref:System.Data.OracleClient.OracleString>)。 這不適用於**REF CURSOR**， **BFILE**，或**LOB**資料型別。  
  
## <a name="see-also"></a>請參閱  
 [Oracle 和 ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
