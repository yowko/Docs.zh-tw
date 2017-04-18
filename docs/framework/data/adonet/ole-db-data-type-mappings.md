---
title: "OLE DB 資料型別對應 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 04bcb259-59d3-4fd7-894d-4f0dd0c68069
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# OLE DB 資料型別對應
下表顯示來自 .NET Framework Data Provider for ADO 和 OLE DB \(<xref:System.Data.OleDb>\) 之資料型別的推斷 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型別。  同時也一併列出 <xref:System.Data.OleDb.OleDbDataReader> 具型別的存取子方法。  
  
|ADO 型別|OLE DB 型別|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 類型|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 具型別的存取子|  
|------------|---------------|--------------------------------------------------------------------|-------------------------------------------------------------------------|  
|adBigInt|DBTYPE\_I8|Int64|GetInt64\(\)|  
|adBinary|DBTYPE\_BYTES|Byte\[\]|GetBytes\(\)|  
|adBoolean|DBTYPE\_BOOL|Boolean|GetBoolean\(\)|  
|adBSTR|DBTYPE\_BSTR|String|GetString\(\)|  
|adChapter|DBTYPE\_HCHAPTER|透過 `DataReader` 支援。  請參閱 [使用 DataReader 擷取資料](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)。|GetValue\(\)|  
|adChar|DBTYPE\_STR|String|GetString\(\)|  
|adCurrency|DBTYPE\_CY|Decimal|GetDecimal\(\)|  
|adDate|DBTYPE\_DATE|DateTime|GetDateTime\(\)|  
|adDBDate|DBTYPE\_DBDATE|DateTime|GetDateTime\(\)|  
|adDBTime|DBTYPE\_DBTIME|DateTime|GetDateTime\(\)|  
|adDBTimeStamp|DBTYPE\_DBTIMESTAMP|DateTime|GetDateTime\(\)|  
|adDecimal|DBTYPE\_DECIMAL|Decimal|GetDecimal\(\)|  
|adDouble|DBTYPE\_R8|Double|GetDouble\(\)|  
|adError|DBTYPE\_ERROR|ExternalException|GetValue\(\)|  
|adFileTime|DBTYPE\_FILETIME|DateTime|GetDateTime\(\)|  
|adGUID|DBTYPE\_GUID|Guid|GetGuid\(\)|  
|adIDispatch|DBTYPE\_IDISPATCH \*|物件|GetValue\(\)|  
|adInteger|DBTYPE\_I4|Int32|GetInt32\(\)|  
|adIUnknown|DBTYPE\_IUNKNOWN \*|物件|GetValue\(\)|  
|adNumeric|DBTYPE\_NUMERIC|Decimal|GetDecimal\(\)|  
|adPropVariant|DBTYPE\_PROPVARIANT|物件|GetValue\(\)|  
|adSingle|DBTYPE\_R4|Single|GetFloat\(\)|  
|adSmallInt|DBTYPE\_I2|Int16|GetInt16\(\)|  
|adTinyInt|DBTYPE\_I1|Byte|GetByte\(\)|  
|adUnsignedBigInt|DBTYPE\_UI8|UInt64|GetValue\(\)|  
|adUnsignedInt|DBTYPE\_UI4|UInt32|GetValue\(\)|  
|adUnsignedSmallInt|DBTYPE\_UI2|UInt16|GetValue\(\)|  
|adUnsignedTinyInt|DBTYPE\_UI1|Byte|GetByte\(\)|  
|adVariant|DBTYPE\_VARIANT|物件|GetValue\(\)|  
|adWChar|DBTYPE\_WSTR|String|GetString\(\)|  
|adUserDefined|DBTYPE\_UDT|不支援||  
|adVarNumeric|DBTYPE\_VARNUMERIC|不支援||  
  
 \* OLE DB 型別 `DBTYPE_IUNKNOWN` 和 `DBTYPE_IDISPATCH` 的物件參考是已封送處理的指標表示。  
  
## 請參閱  
 [擷取和修改 ADO.NET 中的資料](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)