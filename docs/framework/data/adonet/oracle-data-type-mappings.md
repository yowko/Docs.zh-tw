---
title: Oracle 資料類型對應
ms.date: 03/30/2017
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
ms.openlocfilehash: c1fb3a6838e6a1b242255d4035c10ab0ec07d536
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104568"
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
|**FLOAT**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|此資料型別為其別名**數字**資料類型，其設計目的是讓<xref:System.Data.OracleClient.OracleDataReader>傳回**System.Decimal**或<xref:System.Data.OracleClient.OracleNumber>而非浮點數的值。 使用 .NET Framework 資料型別會造成溢位。|  
|**INTEGER**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|此資料型別為其別名**NUMBER(38**資料類型，其設計目的是讓<xref:System.Data.OracleClient.OracleDataReader>會傳回**System.Decimal**或<xref:System.Data.OracleClient.OracleNumber>而不是整數值。 使用 .NET Framework 資料型別會造成溢位。|  
|**INTERVAL YEAR TO MONTH**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**INTERVAL DAY TO SECOND**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**LONG**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**LONG RAW**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**String**|<xref:System.Data.OracleClient.OracleLob>||  
|**NUMBER**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|使用 .NET Framework 資料型別會造成溢位。|  
|**NVARCHAR2**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**RAW**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**REF CURSOR**|||Oracle **REF CURSOR**資料類型不支援<xref:System.Data.OracleClient.OracleDataReader>物件。|  
|**ROWID**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**TIMESTAMP**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**TIMESTAMP WITH LOCAL TIME ZONE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**TIMESTAMP WITH TIME ZONE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**UNSIGNED INTEGER**|**number**|<xref:System.Data.OracleClient.OracleNumber>|這個資料型別為其別名**NUMBER(38**資料類型，其設計目的是讓<xref:System.Data.OracleClient.OracleDataReader>會傳回**System.Decimal**或<xref:System.Data.OracleClient.OracleNumber>而非不帶正負號的整數值。 使用 .NET Framework 資料型別會造成溢位。|  
|**VARCHAR2**|**String**|<xref:System.Data.OracleClient.OracleString>||  
  
 下表列出 Oracle 資料型別和.NET Framework 資料型別 (**System.Data.DbType**和<xref:System.Data.OracleClient.OracleType>) 做為參數進行繫結時使用。  
  
|Oracle 資料型別|要以參數來繫結的 DbType 列舉型別|要以參數來繫結的 OracleType 列舉型別|備註|  
|----------------------|-----------------------------------------------|---------------------------------------------------|-------------|  
|**BFILE**||**BFile**|Oracle 僅允許繫結**BFILE**作為**BFILE**參數。 .NET Data Provider for Oracle 將不會不會自動建構為您如果您嘗試繫結非**BFILE**值，例如**byte**或<xref:System.Data.OracleClient.OracleBinary>。|  
|**BLOB**||**Blob**|Oracle 僅允許繫結**BLOB**作為**BLOB**參數。 .NET Data Provider for Oracle 將不會不會自動建構為您如果您嘗試繫結非**BLOB**值，例如**byte**或<xref:System.Data.OracleClient.OracleBinary>。|  
|**CHAR**|**AnsiStringFixedLength**|**Char**||  
|**CLOB**||**Clob**|Oracle 僅允許繫結**CLOB**作為**CLOB**參數。 .NET Data Provider for Oracle 將不會不會自動建構為您如果您嘗試繫結非**CLOB**值，例如**System.String**或<xref:System.Data.OracleClient.OracleString>。|  
|**DATE**|**DateTime**|**DateTime**||  
|**FLOAT**|**Single、Double、Decimal**|**Float、Double、Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> 決定**System.Data.DBType**和<xref:System.Data.OracleClient.OracleType>。|  
|**INTEGER**|**SByte、Int16、Int32、Int64、Decimal**|**SByte、Int16、Int32、Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> 決定**System.Data.DBType**和<xref:System.Data.OracleClient.OracleType>。|  
|**INTERVAL YEAR TO MONTH**|**Int32**|**IntervalYearToMonth**|<xref:System.Data.OracleClient.OracleType> 只有當使用這兩個 Oracle 9i 用戶端和伺服器軟體。|  
|**INTERVAL DAY TO SECOND**|**Object**|**IntervalDayToSecond**|<xref:System.Data.OracleClient.OracleType> 只有當使用這兩個 Oracle 9i 用戶端和伺服器軟體。|  
|**LONG**|**AnsiString**|**LongVarChar**||  
|**LONG RAW**|**二元**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**NChar**||  
|**NCLOB**||**NClob**|Oracle 僅允許繫結**NCLOB**作為**NCLOB**參數。 .NET Data Provider for Oracle 將不會不會自動建構為您如果您嘗試繫結非**NCLOB**值，例如**System.String**或<xref:System.Data.OracleClient.OracleString>。|  
|**NUMBER**|**VarNumeric**|**number**||  
|**NVARCHAR2**|**String**|**NVarChar**||  
|**RAW**|**二元**|**Raw**||  
|**REF CURSOR**||**Cursor**|如需詳細資訊，請參閱 < [Oracle REF Cursor](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)。|  
|**ROWID**|**AnsiString**|**Rowid**||  
|**TIMESTAMP**|**DateTime**|**時間戳記**|<xref:System.Data.OracleClient.OracleType> 只有當使用這兩個 Oracle 9i 用戶端和伺服器軟體。|  
|**TIMESTAMP WITH LOCAL TIME ZONE**|**DateTime**|**TimestampLocal**|<xref:System.Data.OracleClient.OracleType> 只有當使用這兩個 Oracle 9i 用戶端和伺服器軟體。|  
|**TIMESTAMP WITH TIME ZONE**|**DateTime**|**TimestampWithTz**|<xref:System.Data.OracleClient.OracleType> 只有當使用這兩個 Oracle 9i 用戶端和伺服器軟體。|  
|**UNSIGNED INTEGER**|**Byte、UInt16、UInt32、UInt64、Decimal**|**Byte、UInt16、Uint32、Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> 決定**System.Data.DBType**和<xref:System.Data.OracleClient.OracleType>。|  
|**VARCHAR2**|**AnsiString**|**VarChar**||  
  
 **InputOutput**，**輸出**，並**ReturnValue** **ParameterDirection**所使用的值<xref:System.Data.OracleClient.OracleParameter.Value%2A>屬性<xref:System.Data.OracleClient.OracleParameter>物件就會是.NET Framework 資料型別，除非輸入的值是 Oracle 資料類型 (例如<xref:System.Data.OracleClient.OracleNumber>或<xref:System.Data.OracleClient.OracleString>)。 這不適用於**REF CURSOR**， **BFILE**，或**LOB**資料型別。  
  
## <a name="see-also"></a>另請參閱

- [Oracle 和 ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [ADO.NET Managed 提供者和DataSet開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
