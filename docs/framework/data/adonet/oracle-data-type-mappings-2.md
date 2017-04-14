---
title: "Oracle 資料類型對應 | Microsoft Docs"
ms.custom: ""
ms.date: "02/15/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d2521bcc-0051-4f35-8be3-e8723edeaf6f
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
---
# Oracle 資料類型對應
下表顯示 .NET Framework Data Provider for Oracle \([!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]\) 之資料型別的推斷 <xref:System.Data.OracleClient> 型別。 同時也一併列出 <xref:System.Data.OracleClient.OracleDataReader> 具型別的存取子方法。  
  
|Oracle 型別|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 類型|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 具型別的存取子|OracleType 具型別的存取子|  
|---------------|--------------------------------------------------------------------|-------------------------------------------------------------------------|------------------------|  
|BFILE|Byte\[\]|GetBytes\(\)|GetOracleBFile\(\)|  
|BLOB|Byte\[\]|GetBytes\(\)|GetOracleLob\(\)|  
|CHAR|String<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|GetOracleString\(\)|  
|CLOB|String<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|GetOracleLob\(\)|  
|DATE|DateTime|GetDateTime\(\)|GetOracleDateTime\(\)|  
|FLOAT|Decimal|GetDecimal\(\)|GetOracleNumber\(\) \*\*|  
|INTEGER|Decimal|GetDecimal\(\)|GetOracleNumber\(\) \*\*|  
|INTERVAL YEAR TO MONTH \*|Int32|GetInt32\(\)|GetOracleMonthSpan\(\)|  
|INTERVAL DAY TO SECOND \*|TimeSpan|GetTimeSpan\(\)|GetOracleTimeSpan\(\)|  
|LONG|String<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|GetOracleString\(\)|  
|LONG RAW|Byte\[\]|GetBytes\(\)|GetOracleBinary\(\)|  
|NCHAR|String<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|GetOracleString\(\)|  
|NCLOB|String<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|GetOracleLob\(\)|  
|NUMBER|Decimal|GetDecimal\(\)|GetOracleNumber\(\) \*\*|  
|NVARCHAR2|String<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|GetOracleString\(\)|  
|RAW|Byte\[\]|GetBytes\(\)|GetOracleBinary\(\)|  
|REF CURSOR||||  
|ROWID|String<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|GetOracleString\(\)|  
|TIMESTAMP \*|DateTime|GetDateTime\(\)|GetOracleDateTime\(\)|  
|TIMESTAMP WITH LOCAL TIME ZONE \*|DateTime|GetDateTime\(\)|GetOracleDateTime\(\)|  
|TIMESTAMP WITH TIME ZONE \*|DateTime|GetDateTime\(\)|GetOracleDateTime\(\)|  
|UNSIGNED INTEGER|Decimal|GetDecimal\(\)|GetOracleNumber\(\) \*\*|  
|VARCHAR2|String<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|GetOracleString\(\)|  
  
 \* 只有在您同時針對用戶端和伺服器使用 Oracle 9i 軟體時，才能使用指定的 Oracle 型別。  
  
 \*\* Oracle NUMBER 最大可有 38 個有效位數。[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] `decimal` 型別限制為 28 位數。 將 Oracle NUMBER 讀取到 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]`decimal` 型別會造成 `OverflowException` 並使 NUMBER 值超過 28 位數。 如果您從 `OracleDataReader` 讀取 Oracle NUMBER 值，建議您呼叫 `GetOracleNumber` 具型別存取子方法，將 Oracle NUMBER 值當做 `OracleNumber` 傳回。 如果填入 `DataSet`，可以使用 `FillError` 事件來判斷 `OverflowException` 是否已經發生，並採取適當的動作 \(如果發生此事件的話\)。 如需 `FillError` 事件的資訊，請參閱 [處理 DataAdapter 事件](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)。  
  
## 請參閱  
 [Oracle 和 ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)   
 [擷取和修改 ADO.NET 中的資料](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)