---
title: 適用於 Entity Framework 之 SqlClient 的類型
ms.date: 03/30/2017
ms.assetid: f2a95ead-c845-4e97-9fb3-04b444f7ed81
ms.openlocfilehash: af3a4eea08dd3f4e1a134fcb66d92bc4a3b077c7
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248372"
---
# <a name="sqlclient-for-entity-frameworktypes"></a>適用於 Entity Framework 之 SqlClient 的類型
.NET Framework Data Provider for SQL Server (SqlClient) 提供者資訊清單檔案包含下列的清單：提供者基本型別 (Primitive Type)、每個型別的 Facet、概念和儲存體模型基本型別之間的對應，以及概念和儲存體模型基本型別之間的提升及轉換規則。  
  
 下表描述 SQL Server 2008、SQL Server 2005 和 SQL Server 2000 資料庫的類型，以及這些類型如何對應至概念模型類型。 較新的 SQL Server 版本中引進了一些新的型別，但是舊版的 SQL Server 並不支援這些型別。 下表會說明這些類型。  
  
|提供者類型<br /><br /> NAME|提供者類型<br /><br /> 屬性|`EDMSimpleType`<br /><br /> NAME|Facet|  
|----------------------------|----------------------------------|------------------------------|------------|  
|`bit`|N/A|`Edm.Boolean`|N/A|  
|`tinyint`|N/A|`Edm.Byte`|N/A|  
|`smallint`|N/A|`Edm.Int16`|N/A|  
|`int`|N/A|`Edm.Int32`|N/A|  
|`bigint`|N/A|`Edm.Int64`|N/A|  
|`float`|N/A|`Edm.Double`|N/A|  
|`real`|N/A|`Edm.Double`|N/A|  
|`decimal`|N/A|`Edm.Decimal`|精密<br /><br /> 至少1<br /><br /> 高38<br /><br /> 預設18<br /><br /> 常數偽<br /><br /> 尺度<br /><br /> 至少0<br /><br /> 高38<br /><br /> 預設0<br /><br /> 常數偽|  
|`numeric`|N/A|`Edm.Decimal`|精密<br /><br /> 至少1<br /><br /> 高38<br /><br /> 預設18<br /><br /> 常數偽<br /><br /> 尺度<br /><br /> 至少0<br /><br /> 高38<br /><br /> 預設0<br /><br /> 常數偽|  
|`smallmoney`|N/A|`Edm.Decimal`|精密<br /><br /> 預設10<br /><br /> 常數True<br /><br /> 尺度<br /><br /> 預設4<br /><br /> 常數True|  
|`money`|N/A|`Edm.Decimal`|精密<br /><br /> 預設19<br /><br /> 常數True<br /><br /> 尺度<br /><br /> 預設4<br /><br /> 常數True|  
|`binary`|N/A|`Edm.Binary`|長度<br /><br /> 至少1<br /><br /> 高8000<br /><br /> 預設8000<br /><br /> 常數偽<br /><br /> FixedLength<br /><br /> 預設True<br /><br /> 常數True|  
|`varbinary`|N/A|`Edm.Binary`|長度<br /><br /> 至少1<br /><br /> 高8000<br /><br /> 預設8000<br /><br /> 常數偽<br /><br /> FixedLength<br /><br /> 預設偽<br /><br /> 常數True|  
|`varbinary(max)`<br /><br /> 注意:SQL Server 2000 中不支援此類型。|N/A|`Edm.Binary`|長度<br /><br /> 預設214748364780<br /><br /> 常數True<br /><br /> FixedLength<br /><br /> 預設偽<br /><br /> 常數True|  
|`image`|N/A|`Edm.Binary`|長度<br /><br /> 預設2147483647<br /><br /> 常數True<br /><br /> FixedLength<br /><br /> 預設偽<br /><br /> 常數True|  
|`timestamp`|N/A|`Edm.Binary`|長度<br /><br /> 預設8<br /><br /> 常數True<br /><br /> FixedLength<br /><br /> 預設True<br /><br /> 常數True|  
|`rowversion`|N/A|`Edm.Binary`|長度<br /><br /> 預設8<br /><br /> 常數True<br /><br /> FixedLength<br /><br /> 預設True<br /><br /> 常數True|  
|`smalldatetime`|N/A|`Edm.DateTime`|精密<br /><br /> 預設0<br /><br /> 常數True|  
|`datetime`|N/A|`Edm.DateTime`|精密<br /><br /> 預設3<br /><br /> 常數True|  
|`date`<br /><br /> 注意:SQL Server 2005 和 SQL Server 2000 中不支援此類型。|N/A|`Edm.DateTime`|精密<br /><br /> 預設0<br /><br /> 常數偽|  
|`time`<br /><br /> 注意:SQL Server 2005 和 SQL Server 2000 中不支援此類型。|N/A|`Edm.Time`|精密<br /><br /> 預設7<br /><br /> 常數偽|  
|`datetime2`<br /><br /> 注意:SQL Server 2005 和 SQL Server 2000 中不支援此類型。|N/A|`Edm.DateTime`|精密<br /><br /> 預設7<br /><br /> 常數偽|  
|`datetimeoffset`<br /><br /> 注意:SQL Server 2005 和 SQL Server 2000 中不支援此類型。|N/A|`Edm.DateTimeOffset`|精密<br /><br /> 預設7<br /><br /> 常數偽|  
|`nvarchar`<br /><br /> 注意:SQL Server 2000 中不支援此類型。|N/A|`Edm.String`|長度<br /><br /> 至少1<br /><br /> 高4000<br /><br /> 預設4000<br /><br /> 常數偽<br /><br /> Unicode：<br /><br /> 預設True<br /><br /> 常數True<br /><br /> FixedLength<br /><br /> 預設偽<br /><br /> 常數True|  
|`varchar`<br /><br /> 注意:SQL Server 2000 中不支援此類型。|N/A|`Edm.String`|長度<br /><br /> 至少1<br /><br /> 高8000<br /><br /> 預設8000<br /><br /> 常數偽<br /><br /> Unicode：<br /><br /> 預設偽<br /><br /> 常數True<br /><br /> FixedLength<br /><br /> 預設偽<br /><br /> 常數True|  
|`char`|N/A|`Edm.String`|長度<br /><br /> 至少1<br /><br /> 高8000<br /><br /> 預設8000<br /><br /> 常數偽<br /><br /> Unicode：<br /><br /> 預設偽<br /><br /> 常數True<br /><br /> FixedLength<br /><br /> 預設True<br /><br /> 常數True|  
|`nchar`|N/A|`Edm.String`|長度<br /><br /> 至少1<br /><br /> 高4000<br /><br /> 預設4000<br /><br /> 常數偽<br /><br /> Unicode：<br /><br /> 預設True<br /><br /> 常數True<br /><br /> FixedLength<br /><br /> 預設True<br /><br /> 常數True|  
|`varchar`(`max`)|N/A|`Edm.String`|長度<br /><br /> 預設2147483647<br /><br /> 常數True<br /><br /> Unicode：<br /><br /> 預設偽<br /><br /> 常數True<br /><br /> FixedLength<br /><br /> 預設偽<br /><br /> 常數True|  
|`nvarchar`(`max`)|N/A|`Edm.String`|長度<br /><br /> 預設1073741823<br /><br /> 常數True<br /><br /> Unicode：<br /><br /> 預設True<br /><br /> 常數True<br /><br /> FixedLength<br /><br /> 預設偽<br /><br /> 常數True|  
|`ntext`|相等比較：偽<br /><br /> 可比較的順序：偽|`Edm.String`|長度<br /><br /> 預設1073741823<br /><br /> 常數True<br /><br /> Unicode：<br /><br /> 預設偽<br /><br /> 常數True<br /><br /> FixedLength<br /><br /> 預設偽<br /><br /> 常數True|  
|`text`|相等比較：偽<br /><br /> 可比較的順序：偽|`Edm.String`|長度<br /><br /> 預設2147483647<br /><br /> 常數True<br /><br /> Unicode：<br /><br /> 預設偽<br /><br /> 常數True<br /><br /> FixedLength<br /><br /> 預設偽<br /><br /> 常數True|  
|`Unique`<br /><br /> `identifier`|相等比較：True<br /><br /> 可比較的順序：True|`Edm.Guid`|N/A|  
|`xml`|相等比較：偽<br /><br /> 可比較的順序：偽|`Edm.String`|長度<br /><br /> 預設1073741823<br /><br /> 常數True<br /><br /> Unicode：<br /><br /> 預設True<br /><br /> 常數True<br /><br /> FixedLength<br /><br /> 預設偽<br /><br /> 常數True|  
  
## <a name="see-also"></a>另請參閱

- [CSDL、SSDL 和 MSL 規格](./language-reference/csdl-ssdl-and-msl-specifications.md)
