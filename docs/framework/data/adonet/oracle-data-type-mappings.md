---
title: Oracle 資料類型對應
ms.date: 03/30/2017
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
ms.openlocfilehash: 71a85f82ea3535cf7aec8dd92fbda6726a36fb81
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166569"
---
# <a name="oracle-data-type-mappings"></a>Oracle 資料類型對應

下表列出 Oracle 資料型別及其與 <xref:System.Data.OracleClient.OracleDataReader> 的對應。  
  
|Oracle 資料類型|OracleDataReader.GetValue 傳回的 .NET Framework 資料型別|OracleDataReader.GetOracleValue 傳回的 OracleClient 資料型別|備註|  
|----------------------|--------------------------------------------------------------------|------------------------------------------------------------------------|-------------|  
|**BFILE**|**Byte []**|<xref:System.Data.OracleClient.OracleBFile>||  
|**BLOB**|**Byte []**|<xref:System.Data.OracleClient.OracleLob>||  
|**CHAR**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**CLOB**|**String**|<xref:System.Data.OracleClient.OracleLob>||  
|**DATE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**FLOAT**|**十進位**|<xref:System.Data.OracleClient.OracleNumber>|這種資料型別是 **NUMBER** 資料類型的別名，而且是設計成讓傳回 <xref:System.Data.OracleClient.OracleDataReader> 的是 **Decimal** 或 <xref:System.Data.OracleClient.OracleNumber> 而非浮點值。 使用 .NET Framework 資料型別會造成溢位。|  
|**INTEGER**|**十進位**|<xref:System.Data.OracleClient.OracleNumber>|此資料類型是** (38) **資料類型之數位的別名，而且是設計來讓傳回 system.string <xref:System.Data.OracleClient.OracleDataReader> 或不**System.Decimal**是 <xref:System.Data.OracleClient.OracleNumber> 整數值。 使用 .NET Framework 資料型別會造成溢位。|  
|**INTERVAL YEAR TO MONTH**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**INTERVAL DAY TO SECOND**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**LONG**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**LONG RAW**|**Byte []**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**String**|<xref:System.Data.OracleClient.OracleLob>||  
|**數量**|**十進位**|<xref:System.Data.OracleClient.OracleNumber>|使用 .NET Framework 資料型別會造成溢位。|  
|**NVARCHAR2**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**RAW**|**Byte []**|<xref:System.Data.OracleClient.OracleBinary>||  
|**REF CURSOR**|||物件不支援 Oracle **REF CURSOR** 資料類型 <xref:System.Data.OracleClient.OracleDataReader> 。|  
|**ROWID**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**TIMESTAMP**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**TIMESTAMP WITH LOCAL TIME ZONE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**具有時區的時間戳記**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**不帶正負號的整數**|**Number**|<xref:System.Data.OracleClient.OracleNumber>|此資料類型是** (38) **資料類型之數位的別名，其設計目的是要傳回 system.string <xref:System.Data.OracleClient.OracleDataReader> 或不**System.Decimal**帶正負號的 <xref:System.Data.OracleClient.OracleNumber> 整數值。 使用 .NET Framework 資料型別會造成溢位。|  
|**VARCHAR2**|**String**|<xref:System.Data.OracleClient.OracleString>||  
  
 下表列出 Oracle 資料類型，以及在將它們系結為參數時所要使用的 .NET Framework 資料類型 (**system.object** 和 <xref:System.Data.OracleClient.OracleType>) 。  
  
|Oracle 資料類型|要以參數來繫結的 DbType 列舉型別|要以參數來繫結的 OracleType 列舉型別|備註|  
|----------------------|-----------------------------------------------|---------------------------------------------------|-------------|  
|**BFILE**||**BFile**|Oracle 只允許將 **bfile** 系結為 **bfile** 參數。 如果您嘗試系結非**BFILE** 值（例如 **byte []** 或），則 Oracle 的 .net Data Provider 不會自動為您建立一個 <xref:System.Data.OracleClient.OracleBinary> 。|  
|**BLOB**||**Blob**|Oracle 只允許將 **blob** 系結為 **blob** 參數。 如果您嘗試系結非**BLOB** 值（例如 **byte []** 或），則 Oracle 的 .net Data Provider 不會自動為您建立一個 <xref:System.Data.OracleClient.OracleBinary> 。|  
|**CHAR**|**AnsiStringFixedLength**|**字元**||  
|**CLOB**||**Clob**|Oracle 只允許將 **CLOB** 系結為 **CLOB** 參數。 如果您嘗試系結非**CLOB** 的值（例如 **system.string** 或），則 Oracle 的 .net Data Provider 不會自動為您建立一個 <xref:System.Data.OracleClient.OracleString> 。|  
|**DATE**|**DateTime**|**DateTime**||  
|**FLOAT**|**Single、Double、Decimal**|**Float、Double、Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> 決定 **system.object** 和 <xref:System.Data.OracleClient.OracleType> 。|  
|**INTEGER**|**SByte、Int16、Int32、Int64、Decimal**|**SByte、Int16、Int32、Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> 決定 **system.object** 和 <xref:System.Data.OracleClient.OracleType> 。|  
|**INTERVAL YEAR TO MONTH**|**Int32**|**IntervalYearToMonth**|只有當您同時使用 Oracle 9i 用戶端及伺服器軟體時，才可以使用 <xref:System.Data.OracleClient.OracleType>。|  
|**INTERVAL DAY TO SECOND**|**Object**|**IntervalDayToSecond**|只有當您同時使用 Oracle 9i 用戶端及伺服器軟體時，才可以使用 <xref:System.Data.OracleClient.OracleType>。|  
|**LONG**|**AnsiString**|**LongVarChar**||  
|**LONG RAW**|**二進位**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**NChar**||  
|**NCLOB**||**NClob**|Oracle 只允許將 **NCLOB** 系結為 **NCLOB** 參數。 如果您嘗試系結非**NCLOB** 的值（例如 **system.string** 或），則 Oracle 的 .net Data Provider 不會自動為您建立一個 <xref:System.Data.OracleClient.OracleString> 。|  
|**數量**|**VarNumeric**|**Number**||  
|**NVARCHAR2**|**String**|**NVarChar**||  
|**RAW**|**二進位**|**原始**||  
|**REF CURSOR**||**資料指標**|如需詳細資訊，請參閱 [ORACLE REF 資料指標](oracle-ref-cursors.md)。|  
|**ROWID**|**AnsiString**|**Rowid**||  
|**TIMESTAMP**|**DateTime**|**Timestamp**|只有當您同時使用 Oracle 9i 用戶端及伺服器軟體時，才可以使用 <xref:System.Data.OracleClient.OracleType>。|  
|**TIMESTAMP WITH LOCAL TIME ZONE**|**DateTime**|**TimestampLocal**|只有當您同時使用 Oracle 9i 用戶端及伺服器軟體時，才可以使用 <xref:System.Data.OracleClient.OracleType>。|  
|**具有時區的時間戳記**|**DateTime**|**TimestampWithTz**|只有當您同時使用 Oracle 9i 用戶端及伺服器軟體時，才可以使用 <xref:System.Data.OracleClient.OracleType>。|  
|**不帶正負號的整數**|**Byte、UInt16、UInt32、UInt64、Decimal**|**Byte、UInt16、Uint32、Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> 決定 **system.object** 和 <xref:System.Data.OracleClient.OracleType> 。|  
|**VARCHAR2**|**AnsiString**|**VarChar**||  
  
 **ReturnValue** **ParameterDirection** **InputOutput** **Output** <xref:System.Data.OracleClient.OracleParameter.Value%2A> <xref:System.Data.OracleClient.OracleParameter> 除非輸入值為 Oracle 資料類型 (例如，或) ，否則物件屬性所使用的 InputOutput、Output 和 ReturnValue ParameterDirection 值都是 .NET Framework 資料類型 <xref:System.Data.OracleClient.OracleNumber> <xref:System.Data.OracleClient.OracleString> 。 這不適用於 **REF CURSOR**、 **BFILE**或 **LOB** 資料類型。  
  
## <a name="see-also"></a>另請參閱

- [Oracle 和 ADO.NET](oracle-and-adonet.md)
- [ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)
