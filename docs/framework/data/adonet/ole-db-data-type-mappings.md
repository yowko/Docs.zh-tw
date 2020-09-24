---
title: OLE DB 資料類型對應
ms.date: 03/30/2017
ms.assetid: 04bcb259-59d3-4fd7-894d-4f0dd0c68069
ms.openlocfilehash: 7f3b498e39feac4a6fe98e739793d20e0268b8f4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150696"
---
# <a name="ole-db-data-type-mappings"></a>OLE DB 資料類型對應

下表顯示 ADO 和 OLE DB () 之 .NET Framework Data Provider 中的資料類型推斷 .NET Framework 類型 <xref:System.Data.OleDb> 。 同時也一併列出 <xref:System.Data.OleDb.OleDbDataReader> 具型別的存取子方法。  
  
|ADO 型別|OLE DB 類型|.NET Framework 類型|.NET Framework 具類型存取子|  
|--------------|-----------------|----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|adBigInt|DBTYPE_I8|Int64|GetInt64()|  
|adBinary|DBTYPE_BYTES|Byte[]|GetBytes()|  
|adBoolean|DBTYPE_BOOL|Boolean|GetBoolean()|  
|adBSTR|DBTYPE_BSTR|String|GetString()|  
|adChapter|DBTYPE_HCHAPTER|透過 `DataReader` 支援。 請參閱 [使用 DataReader 來取出資料](retrieving-data-using-a-datareader.md)。|GetValue()|  
|adChar|DBTYPE_STR|String|GetString()|  
|adCurrency|DBTYPE_CY|Decimal|GetDecimal()|  
|adDate|DBTYPE_DATE|Datetime|GetDateTime()|  
|adDBDate|DBTYPE_DBDATE|Datetime|GetDateTime()|  
|adDBTime|DBTYPE_DBTIME|Datetime|GetDateTime()|  
|adDBTimeStamp|DBTYPE_DBTIMESTAMP|Datetime|GetDateTime()|  
|adDecimal|DBTYPE_DECIMAL|Decimal|GetDecimal()|  
|adDouble|DBTYPE_R8|Double|GetDouble()|  
|adError|DBTYPE_ERROR|ExternalException|GetValue()|  
|adFileTime|DBTYPE_FILETIME|Datetime|GetDateTime()|  
|adGUID|DBTYPE_GUID|Guid|GetGuid()|  
|adIDispatch|DBTYPE_IDISPATCH *|Object|GetValue()|  
|adInteger|DBTYPE_I4|Int32|GetInt32()|  
|adIUnknown|DBTYPE_IUNKNOWN *|Object|GetValue()|  
|adNumeric|DBTYPE_NUMERIC|Decimal|GetDecimal()|  
|adPropVariant|DBTYPE_PROPVARIANT|Object|GetValue()|  
|adSingle|DBTYPE_R4|Single|GetFloat()|  
|adSmallInt|DBTYPE_I2|Int16|GetInt16()|  
|adTinyInt|DBTYPE_I1|Byte|GetByte()|  
|adUnsignedBigInt|DBTYPE_UI8|UInt64|GetValue()|  
|adUnsignedInt|DBTYPE_UI4|UInt32|GetValue()|  
|adUnsignedSmallInt|DBTYPE_UI2|UInt16|GetValue()|  
|adUnsignedTinyInt|DBTYPE_UI1|Byte|GetByte()|  
|adVariant|DBTYPE_VARIANT|Object|GetValue()|  
|adWChar|DBTYPE_WSTR|String|GetString()|  
|adUserDefined|DBTYPE_UDT|不支援||  
|adVarNumeric|DBTYPE_VARNUMERIC|不支援||  
  
 \* 如果是 OLE DB 類型 `DBTYPE_IUNKNOWN` 和 `DBTYPE_IDISPATCH` ，則物件參考是已封送處理的指標標記法。  
  
## <a name="see-also"></a>另請參閱

- [在 ADO.NET 中傳送和修改資料](retrieving-and-modifying-data.md)
- [ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)
