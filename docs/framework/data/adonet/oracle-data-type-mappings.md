---
title: "Oracle 資料型別對應 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Oracle 資料型別對應
下表列出 Oracle 資料型別及其與 <xref:System.Data.OracleClient.OracleDataReader> 的對應。  
  
|Oracle 資料型別|OracleDataReader.GetValue 傳回的 .NET Framework 資料型別|OracleDataReader.GetOracleValue 傳回的 OracleClient 資料型別|備註|  
|-----------------|-------------------------------------------------------|-----------------------------------------------------------|--------|  
|**BFILE**|**Byte\[\]**|<xref:System.Data.OracleClient.OracleBFile>||  
|**BLOB**|**Byte\[\]**|<xref:System.Data.OracleClient.OracleLob>||  
|**CHAR**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**CLOB**|**String**|<xref:System.Data.OracleClient.OracleLob>||  
|**DATE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**FLOAT**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|此資料型別是 **NUMBER** 資料型別的別名，並且已設計為能夠讓 <xref:System.Data.OracleClient.OracleDataReader> 傳回 **System.Decimal** 或 <xref:System.Data.OracleClient.OracleNumber>，而非浮點值。  使用 .NET Framework 資料型別會造成溢位。|  
|**INTEGER**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|此資料型別是 **NUMBER\(38\)** 資料型別的別名，並且已設計為能夠讓 <xref:System.Data.OracleClient.OracleDataReader> 傳回 **System.Decimal** 或 <xref:System.Data.OracleClient.OracleNumber>，而非整數值。  使用 .NET Framework 資料型別會造成溢位。|  
|**INTERVAL YEAR TO MONTH**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**INTERVAL DAY TO SECOND**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**LONG**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**LONG RAW**|**Byte\[\]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**String**|<xref:System.Data.OracleClient.OracleLob>||  
|**NUMBER**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|使用 .NET Framework 資料型別會造成溢位。|  
|**NVARCHAR2**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**RAW**|**Byte\[\]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**REF CURSOR**|||Oracle **REF CURSOR** 資料型別不受 <xref:System.Data.OracleClient.OracleDataReader> 物件支援。|  
|**ROWID**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**TIMESTAMP**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**TIMESTAMP WITH LOCAL TIME ZONE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**TIMESTAMP WITH TIME ZONE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**UNSIGNED INTEGER**|**數字**|<xref:System.Data.OracleClient.OracleNumber>|此資料型別是 **NUMBER\(38\)** 資料型別的別名，並且已設計為能夠讓 <xref:System.Data.OracleClient.OracleDataReader> 傳回 **System.Decimal** 或 <xref:System.Data.OracleClient.OracleNumber>，而非不帶正負號的整數 \(Unsigned Integer\) 值。  使用 .NET Framework 資料型別會造成溢位。|  
|**VARCHAR2**|**String**|<xref:System.Data.OracleClient.OracleString>||  
  
 下表列出當做參數進行繫結時，要使用的 Oracle 資料型別及 .NET Framework 資料型別 \(**System.Data.DbType** 及 <xref:System.Data.OracleClient.OracleType>\)。  
  
|Oracle 資料型別|要以參數來繫結的 DbType 列舉型別|要以參數來繫結的 OracleType 列舉型別|備註|  
|-----------------|--------------------------|------------------------------|--------|  
|**BFILE**||**BFile**|Oracle 僅允許以 **BFILE** 參數來繫結 **BFILE**。  如果您嘗試繫結非 **BFILE** 值 \(例如 **byte\[\]** 或 <xref:System.Data.OracleClient.OracleBinary>\)，.NET Data Provider for Oracle 將不會自動為您建構。|  
|**BLOB**||**Blob**|Oracle 僅允許以 **BLOB** 參數來繫結 **BLOB**。  如果您嘗試繫結非 **BLOB** 值 \(例如 **byte\[\]** 或 <xref:System.Data.OracleClient.OracleBinary>\)，.NET Data Provider for Oracle 將不會自動為您建構。|  
|**CHAR**|**AnsiStringFixedLength**|**Char**||  
|**CLOB**||**Clob**|Oracle 僅允許以 **CLOB** 參數來繫結 **CLOB**。  如果您嘗試繫結非 **CLOB** 值 \(例如 **System.String** 或 <xref:System.Data.OracleClient.OracleString>\)，.NET Data Provider for Oracle 將不會自動為您建構。|  
|**DATE**|**DateTime**|**DateTime**||  
|**FLOAT**|**Single、Double、Decimal**|**Float、Double、Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> 可決定 **System.Data.DBType** 和 <xref:System.Data.OracleClient.OracleType>。|  
|**INTEGER**|**SByte、Int16、Int32、Int64、Decimal**|**SByte、Int16、Int32、Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> 可決定 **System.Data.DBType** 和 <xref:System.Data.OracleClient.OracleType>。|  
|**INTERVAL YEAR TO MONTH**|**Int32**|**IntervalYearToMonth**|只有當您同時使用 Oracle 9i 用戶端及伺服器軟體時，才可以使用 <xref:System.Data.OracleClient.OracleType>。|  
|**INTERVAL DAY TO SECOND**|**物件**|**IntervalDayToSecond**|只有當您同時使用 Oracle 9i 用戶端及伺服器軟體時，才可以使用 <xref:System.Data.OracleClient.OracleType>。|  
|**LONG**|**AnsiString**|**LongVarChar**||  
|**LONG RAW**|**二元**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**NChar**||  
|**NCLOB**||**NClob**|Oracle 僅允許以 **NCLOB** 參數來繫結 **NCLOB**。  如果您嘗試繫結非 **NCLOB** 值 \(例如 **System.String** 或 <xref:System.Data.OracleClient.OracleString>\)，.NET Data Provider for Oracle 將不會自動為您建構。|  
|**NUMBER**|**VarNumeric**|**數字**||  
|**NVARCHAR2**|**String**|**NVarChar**||  
|**RAW**|**二元**|**Raw**||  
|**REF CURSOR**||**Cursor**|如需詳細資訊，請參閱[Oracle REF CURSOR](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)。|  
|**ROWID**|**AnsiString**|**Rowid**||  
|**TIMESTAMP**|**DateTime**|**Timestamp**|只有當您同時使用 Oracle 9i 用戶端及伺服器軟體時，才可以使用 <xref:System.Data.OracleClient.OracleType>。|  
|**TIMESTAMP WITH LOCAL TIME ZONE**|**DateTime**|**TimestampLocal**|只有當您同時使用 Oracle 9i 用戶端及伺服器軟體時，才可以使用 <xref:System.Data.OracleClient.OracleType>。|  
|**TIMESTAMP WITH TIME ZONE**|**DateTime**|**TimestampWithTz**|只有當您同時使用 Oracle 9i 用戶端及伺服器軟體時，才可以使用 <xref:System.Data.OracleClient.OracleType>。|  
|**UNSIGNED INTEGER**|**Byte、UInt16、UInt32、UInt64、Decimal**|**Byte、UInt16、Uint32、Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> 可決定 **System.Data.DBType** 和 <xref:System.Data.OracleClient.OracleType>。|  
|**VARCHAR2**|**AnsiString**|**VarChar**||  
  
 除非輸入值是 Oracle 資料型別 \(例如，<xref:System.Data.OracleClient.OracleNumber> 或 <xref:System.Data.OracleClient.OracleString>\)，否則 <xref:System.Data.OracleClient.OracleParameter> 物件之 <xref:System.Data.OracleClient.OracleParameter.Value%2A> 屬性所使用的 **InputOutput**、**Output** 和 **ReturnValue** **ParameterDirection** 值就是 .NET Framework 資料型別。  這並不適用於 **REF CURSOR**、**BFILE** 或 **LOB** 資料型別。  
  
## 請參閱  
 [Oracle 和 ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)