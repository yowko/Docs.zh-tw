---
title: Oracle 資料類型對應
ms.date: 03/30/2017
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
ms.openlocfilehash: c1fb3a6838e6a1b242255d4035c10ab0ec07d536
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771978"
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
|**間隔年至月**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**間隔日至秒鐘**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**LONG**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**長資料列**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**String**|<xref:System.Data.OracleClient.OracleLob>||  
|**數字**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|使用 .NET Framework 資料型別會造成溢位。|  
|**NVARCHAR2**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**RAW**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**REF CURSOR**|||Oracle **REF CURSOR**資料類型不支援<xref:System.Data.OracleClient.OracleDataReader>物件。|  
|**ROWID**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**TIMESTAMP**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**使用本地時區的時間戳記**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**時區的時間戳記**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**不帶正負號的整數**|**數字**|<xref:System.Data.OracleClient.OracleNumber>|這個資料型別為其別名**NUMBER(38**資料類型，其設計目的是讓<xref:System.Data.OracleClient.OracleDataReader>會傳回**System.Decimal**或<xref:System.Data.OracleClient.OracleNumber>而非不帶正負號的整數值。 使用 .NET Framework 資料型別會造成溢位。|  
|**VARCHAR2**|**String**|<xref:System.Data.OracleClient.OracleString>||  
  
 下表列出 Oracle 資料型別和.NET Framework 資料型別 (**System.Data.DbType**和<xref:System.Data.OracleClient.OracleType>) 做為參數進行繫結時使用。  
  
|Oracle 資料型別|要以參數來繫結的 DbType 列舉型別|要以參數來繫結的 OracleType 列舉型別|備註|  
|----------------------|-----------------------------------------------|---------------------------------------------------|-------------|  
|**BFILE**||**BFile**|Oracle 僅允許繫結**BFILE**作為**BFILE**參數。 .NET Data Provider for Oracle 將不會不會自動建構為您如果您嘗試繫結非**BFILE**值，例如**byte**或<xref:System.Data.OracleClient.OracleBinary>。|  
|**BLOB**||**Blob**|Oracle 僅允許繫結**BLOB**作為**BLOB**參數。 .NET Data Provider for Oracle 將不會不會自動建構為您如果您嘗試繫結非**BLOB**值，例如**byte**或<xref:System.Data.OracleClient.OracleBinary>。|  
|**CHAR**|**AnsiStringFixedLength**|**Char**||  
|**CLOB**||**Clob**|Oracle 僅允許繫結**CLOB**作為**CLOB**參數。 .NET Data Provider for Oracle 將不會不會自動建構為您如果您嘗試繫結非**CLOB**值，例如**System.String**或<xref:System.Data.OracleClient.OracleString>。|  
|**DATE**|**DateTime**|**DateTime**||  
|**FLOAT**|**Single、 Double、 Decimal**|**Float、 Double、 Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> 決定**System.Data.DBType**和<xref:System.Data.OracleClient.OracleType>。|  
|**INTEGER**|**SByte、 Int16、 Int32、 Int64、 Decimal**|**SByte、 Int16、 Int32 數字**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> 決定**System.Data.DBType**和<xref:System.Data.OracleClient.OracleType>。|  
|**間隔年至月**|**Int32**|**IntervalYearToMonth**|只有當您同時使用 Oracle 9i 用戶端及伺服器軟體時，才可以使用 <xref:System.Data.OracleClient.OracleType>。|  
|**間隔日至秒鐘**|**物件**|**IntervalDayToSecond**|只有當您同時使用 Oracle 9i 用戶端及伺服器軟體時，才可以使用 <xref:System.Data.OracleClient.OracleType>。|  
|**LONG**|**AnsiString**|**LongVarChar**||  
|**長資料列**|**Binary**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**NChar**||  
|**NCLOB**||**NClob**|Oracle 僅允許繫結**NCLOB**作為**NCLOB**參數。 .NET Data Provider for Oracle 將不會不會自動建構為您如果您嘗試繫結非**NCLOB**值，例如**System.String**或<xref:System.Data.OracleClient.OracleString>。|  
|**數字**|**VarNumeric**|**數字**||  
|**NVARCHAR2**|**String**|**NVarChar**||  
|**RAW**|**Binary**|**Raw**||  
|**REF CURSOR**||**資料指標**|如需詳細資訊，請參閱 < [Oracle REF Cursor](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)。|  
|**ROWID**|**AnsiString**|**rowid**||  
|**TIMESTAMP**|**DateTime**|**時間戳記**|只有當您同時使用 Oracle 9i 用戶端及伺服器軟體時，才可以使用 <xref:System.Data.OracleClient.OracleType>。|  
|**使用本地時區的時間戳記**|**DateTime**|**TimestampLocal**|只有當您同時使用 Oracle 9i 用戶端及伺服器軟體時，才可以使用 <xref:System.Data.OracleClient.OracleType>。|  
|**時區的時間戳記**|**DateTime**|**TimestampWithTz**|只有當您同時使用 Oracle 9i 用戶端及伺服器軟體時，才可以使用 <xref:System.Data.OracleClient.OracleType>。|  
|**不帶正負號的整數**|**位元組、 UInt16、 UInt32、 UInt64、 Decimal**|**位元組、 UInt16、 Uint32、 數字**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> 決定**System.Data.DBType**和<xref:System.Data.OracleClient.OracleType>。|  
|**VARCHAR2**|**AnsiString**|**VarChar**||  
  
 **InputOutput**，**輸出**，並**ReturnValue** **ParameterDirection**所使用的值<xref:System.Data.OracleClient.OracleParameter.Value%2A>屬性<xref:System.Data.OracleClient.OracleParameter>物件就會是.NET Framework 資料型別，除非輸入的值是 Oracle 資料類型 (例如<xref:System.Data.OracleClient.OracleNumber>或<xref:System.Data.OracleClient.OracleString>)。 這不適用於**REF CURSOR**， **BFILE**，或**LOB**資料型別。  
  
## <a name="see-also"></a>另請參閱

- [Oracle 和 ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
