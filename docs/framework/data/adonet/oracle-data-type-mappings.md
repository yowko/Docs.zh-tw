---
title: Oracle 資料類型對應
ms.date: 03/30/2017
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
ms.openlocfilehash: be478741069e9edd406d73c0b75d5960b9909896
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783417"
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
|**FLOAT**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|此資料類型是**NUMBER**資料類型的別名，而且是設計成<xref:System.Data.OracleClient.OracleDataReader>會傳回 system.string 或<xref:System.Data.OracleClient.OracleNumber>而非浮點**值。** 使用 .NET Framework 資料型別會造成溢位。|  
|**介於**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|此資料型別是**NUMBER （38）** 資料型別的別名，其<xref:System.Data.OracleClient.OracleDataReader>設計目的是要讓傳回**Decimal**或<xref:System.Data.OracleClient.OracleNumber>而不是整數值。 使用 .NET Framework 資料型別會造成溢位。|  
|**間隔年到月**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**間隔日到秒**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**LONG**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**長原始**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**String**|<xref:System.Data.OracleClient.OracleLob>||  
|**項數**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|使用 .NET Framework 資料型別會造成溢位。|  
|**NVARCHAR2**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**原始**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**REF CURSOR**|||<xref:System.Data.OracleClient.OracleDataReader>物件不支援 Oracle **REF CURSOR**資料類型。|  
|**ROWID**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**TIMESTAMP**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**具有當地時區的時間戳記**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**含時區的時間戳記**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**不帶正負號的整數**|**數字**|<xref:System.Data.OracleClient.OracleNumber>|此資料型別是**NUMBER （38）** 資料型別的別名，其設計目的是要讓<xref:System.Data.OracleClient.OracleDataReader>傳回**Decimal**或<xref:System.Data.OracleClient.OracleNumber>而不是不帶正負號的整數值。 使用 .NET Framework 資料型別會造成溢位。|  
|**VARCHAR2**|**String**|<xref:System.Data.OracleClient.OracleString>||  
  
 下表列出 Oracle 資料類型，以及將它們系結為參數時所要使用的<xref:System.Data.OracleClient.OracleType>.NET Framework 資料類型（system.object 和）。  
  
|Oracle 資料型別|要以參數來繫結的 DbType 列舉型別|要以參數來繫結的 OracleType 列舉型別|備註|  
|----------------------|-----------------------------------------------|---------------------------------------------------|-------------|  
|**BFILE**||**BFile**|Oracle 僅允許以**bfile**參數來系結**bfile** 。 如果您嘗試系結非**BFILE**值（例如**byte []** 或<xref:System.Data.OracleClient.OracleBinary>），則 Oracle 的 .net Data Provider 不會自動為您建立一個。|  
|**BLOB**||**Blob**|Oracle 只允許將**blob**系結為**blob**參數。 如果您嘗試系結非**BLOB**值（例如**byte []** 或<xref:System.Data.OracleClient.OracleBinary>），.net Data Provider for Oracle 不會自動為您建立一個。|  
|**CHAR**|**AnsiStringFixedLength**|**Char**||  
|**CLOB**||**Clob**|Oracle 只允許將**CLOB**系結為**CLOB**參數。 如果您嘗試系結非**CLOB**值（例如**system.string**或<xref:System.Data.OracleClient.OracleString>），則 Oracle 的 .net Data Provider 不會自動為您建立一個。|  
|**DATE**|**DateTime**|**DateTime**||  
|**FLOAT**|**Single、Double、Decimal**|**Float、Double、Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>決定**system.object**和<xref:System.Data.OracleClient.OracleType>。|  
|**介於**|**SByte、Int16、Int32、Int64、Decimal**|**SByte、Int16、Int32、Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>決定**system.object**和<xref:System.Data.OracleClient.OracleType>。|  
|**間隔年到月**|**Int32**|**IntervalYearToMonth**|只有當您同時使用 Oracle 9i 用戶端及伺服器軟體時，才可以使用 <xref:System.Data.OracleClient.OracleType>。|  
|**間隔日到秒**|**物件**|**IntervalDayToSecond**|只有當您同時使用 Oracle 9i 用戶端及伺服器軟體時，才可以使用 <xref:System.Data.OracleClient.OracleType>。|  
|**LONG**|**AnsiString**|**LongVarChar**||  
|**長原始**|**Binary**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**NChar**||  
|**NCLOB**||**NClob**|Oracle 只允許將**NCLOB**系結為**NCLOB**參數。 如果您嘗試系結非**NCLOB**值（例如**system.string**或<xref:System.Data.OracleClient.OracleString>），則 Oracle 的 .net Data Provider 不會自動為您建立一個。|  
|**項數**|**VarNumeric**|**數字**||  
|**NVARCHAR2**|**String**|**NVarChar**||  
|**原始**|**Binary**|**原始**||  
|**REF CURSOR**||**滑鼠**|如需詳細資訊，請參閱[ORACLE REF](oracle-ref-cursors.md)cursor。|  
|**ROWID**|**AnsiString**|**Rowid**||  
|**TIMESTAMP**|**DateTime**|**時間戳記**|只有當您同時使用 Oracle 9i 用戶端及伺服器軟體時，才可以使用 <xref:System.Data.OracleClient.OracleType>。|  
|**具有當地時區的時間戳記**|**DateTime**|**TimestampLocal**|只有當您同時使用 Oracle 9i 用戶端及伺服器軟體時，才可以使用 <xref:System.Data.OracleClient.OracleType>。|  
|**含時區的時間戳記**|**DateTime**|**TimestampWithTz**|只有當您同時使用 Oracle 9i 用戶端及伺服器軟體時，才可以使用 <xref:System.Data.OracleClient.OracleType>。|  
|**不帶正負號的整數**|**Byte、UInt16、UInt32、UInt64、Decimal**|**Byte、UInt16、Uint32、Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>決定**system.object**和<xref:System.Data.OracleClient.OracleType>。|  
|**VARCHAR2**|**AnsiString**|**VarChar**||  
  
 <xref:System.Data.OracleClient.OracleParameter>物件的屬性所使用的InputOutput、Output和ReturnValueParameterDirection值是.NETFramework資料類型，除非輸入值是Oracle資料類型（適用于<xref:System.Data.OracleClient.OracleParameter.Value%2A>範例， <xref:System.Data.OracleClient.OracleNumber>或<xref:System.Data.OracleClient.OracleString>）。 這並不適用于**REF CURSOR**、 **BFILE**或**LOB**資料類型。  
  
## <a name="see-also"></a>另請參閱

- [Oracle 和 ADO.NET](oracle-and-adonet.md)
- [ADO.NET 概觀](ado-net-overview.md)
