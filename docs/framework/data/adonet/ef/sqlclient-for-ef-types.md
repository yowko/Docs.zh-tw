---
title: 適用於 Entity Framework 之 SqlClient 的類型
ms.date: 03/30/2017
ms.assetid: f2a95ead-c845-4e97-9fb3-04b444f7ed81
ms.openlocfilehash: bca2cc0e0d9f43c51c66080f3bd38c245ce94381
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156585"
---
# <a name="sqlclient-for-entity-frameworktypes"></a>適用於 Entity Framework 之 SqlClient 的類型

.NET Framework Data Provider for SQL Server (SqlClient) 提供者資訊清單檔案包含下列的清單：提供者基本型別 (Primitive Type)、每個型別的 Facet、概念和儲存體模型基本型別之間的對應，以及概念和儲存體模型基本型別之間的提升及轉換規則。  
  
 下表描述 SQL Server 2008、SQL Server 2005 和 SQL Server 2000 資料庫的類型，以及這些類型如何對應至概念模型類型。 較新的 SQL Server 版本中引進了一些新的型別，但是舊版的 SQL Server 並不支援這些型別。 下表會說明這些類型。  
  
|提供者類型<br /><br /> NAME|提供者類型<br /><br /> 屬性|`EDMSimpleType`<br /><br /> NAME|Facet|  
|----------------------------|----------------------------------|------------------------------|------------|  
|`bit`|n/a|`Edm.Boolean`|n/a|  
|`tinyint`|n/a|`Edm.Byte`|n/a|  
|`smallint`|n/a|`Edm.Int16`|n/a|  
|`int`|n/a|`Edm.Int32`|n/a|  
|`bigint`|n/a|`Edm.Int64`|n/a|  
|`float`|n/a|`Edm.Double`|n/a|  
|`real`|n/a|`Edm.Double`|n/a|  
|`decimal`|n/a|`Edm.Decimal`|精度：<br /><br /> -最小值：1<br /><br /> -最大值：38<br /><br /> -預設值：18<br /><br /> -常數： False<br /><br /> 規模：<br /><br /> -最小值：0<br /><br /> -最大值：38<br /><br /> -預設值：0<br /><br /> -常數： False|  
|`numeric`|n/a|`Edm.Decimal`|精度：<br /><br /> -最小值：1<br /><br /> -最大值：38<br /><br /> -預設值：18<br /><br /> -常數： False<br /><br /> 規模：<br /><br /> -最小值：0<br /><br /> -最大值：38<br /><br /> -預設值：0<br /><br /> -常數： False|  
|`smallmoney`|n/a|`Edm.Decimal`|精度：<br /><br /> -預設值：10<br /><br /> -常數： True<br /><br /> 規模：<br /><br /> -預設值：4<br /><br /> -常數： True|  
|`money`|n/a|`Edm.Decimal`|精度：<br /><br /> -預設值：19<br /><br /> -常數： True<br /><br /> 規模：<br /><br /> -預設值：4<br /><br /> -常數： True|  
|`binary`|n/a|`Edm.Binary`|MaxLength<br /><br /> -最小值：1<br /><br /> -最大值：8000<br /><br /> -預設值：8000<br /><br /> -常數： False<br /><br /> FixedLength<br /><br /> -Default： True<br /><br /> -常數： True|  
|`varbinary`|n/a|`Edm.Binary`|MaxLength<br /><br /> -最小值：1<br /><br /> -最大值：8000<br /><br /> -預設值：8000<br /><br /> -常數： False<br /><br /> FixedLength<br /><br /> -預設值： False<br /><br /> -常數： True|  
|`varbinary(max)`<br /><br /> 注意： SQL Server 2000 中不支援此類型。|n/a|`Edm.Binary`|MaxLength<br /><br /> -預設值：214748364780<br /><br /> -常數： True<br /><br /> FixedLength<br /><br /> -預設值： False<br /><br /> -常數： True|  
|`image`|n/a|`Edm.Binary`|MaxLength<br /><br /> -預設值：2147483647<br /><br /> -常數： True<br /><br /> FixedLength<br /><br /> -預設值： False<br /><br /> -常數： True|  
|`timestamp`|n/a|`Edm.Binary`|MaxLength<br /><br /> -預設值：8<br /><br /> -常數： True<br /><br /> FixedLength<br /><br /> -Default： True<br /><br /> -常數： True|  
|`rowversion`|n/a|`Edm.Binary`|MaxLength<br /><br /> -預設值：8<br /><br /> -常數： True<br /><br /> FixedLength<br /><br /> -Default： True<br /><br /> -常數： True|  
|`smalldatetime`|n/a|`Edm.DateTime`|精度：<br /><br /> -預設值：0<br /><br /> -常數： True|  
|`datetime`|n/a|`Edm.DateTime`|精度：<br /><br /> -預設值：3<br /><br /> -常數： True|  
|`date`<br /><br /> 注意： SQL Server 2005 和 SQL Server 2000 不支援此類型。|n/a|`Edm.DateTime`|精度：<br /><br /> -預設值：0<br /><br /> -常數： False|  
|`time`<br /><br /> 注意： SQL Server 2005 和 SQL Server 2000 不支援此類型。|n/a|`Edm.Time`|精度：<br /><br /> -預設值：7<br /><br /> -常數： False|  
|`datetime2`<br /><br /> 注意： SQL Server 2005 和 SQL Server 2000 不支援此類型。|n/a|`Edm.DateTime`|精度：<br /><br /> -預設值：7<br /><br /> -常數： False|  
|`datetimeoffset`<br /><br /> 注意： SQL Server 2005 和 SQL Server 2000 不支援此類型。|n/a|`Edm.DateTimeOffset`|精度：<br /><br /> -預設值：7<br /><br /> -常數： False|  
|`nvarchar`<br /><br /> 注意： SQL Server 2000 中不支援此類型。|n/a|`Edm.String`|MaxLength<br /><br /> -最小值：1<br /><br /> -最大值：4000<br /><br /> -預設值：4000<br /><br /> -常數： False<br /><br /> Unicode：<br /><br /> -Default： True<br /><br /> -常數： True<br /><br /> FixedLength<br /><br /> -預設值： False<br /><br /> -常數： True|  
|`varchar`<br /><br /> 注意： SQL Server 2000 中不支援此類型。|n/a|`Edm.String`|MaxLength<br /><br /> -最小值：1<br /><br /> -最大值：8000<br /><br /> -預設值：8000<br /><br /> -常數： False<br /><br /> Unicode：<br /><br /> -預設值： False<br /><br /> -常數： True<br /><br /> FixedLength<br /><br /> -預設值： False<br /><br /> -常數： True|  
|`char`|n/a|`Edm.String`|MaxLength<br /><br /> -最小值：1<br /><br /> -最大值：8000<br /><br /> -預設值：8000<br /><br /> -常數： False<br /><br /> Unicode：<br /><br /> -預設值： False<br /><br /> -常數： True<br /><br /> FixedLength<br /><br /> -Default： True<br /><br /> -常數： True|  
|`nchar`|n/a|`Edm.String`|MaxLength<br /><br /> -最小值：1<br /><br /> -最大值：4000<br /><br /> -預設值：4000<br /><br /> -常數： False<br /><br /> Unicode：<br /><br /> -Default： True<br /><br /> -常數： True<br /><br /> FixedLength<br /><br /> -Default： True<br /><br /> -常數： True|  
|`varchar`(`max`)|n/a|`Edm.String`|MaxLength<br /><br /> -預設值：2147483647<br /><br /> -常數： True<br /><br /> Unicode：<br /><br /> -預設值： False<br /><br /> -常數： True<br /><br /> FixedLength<br /><br /> -預設值： False<br /><br /> -常數： True|  
|`nvarchar`(`max`)|n/a|`Edm.String`|MaxLength<br /><br /> -預設值：1073741823<br /><br /> -常數： True<br /><br /> Unicode：<br /><br /> -Default： True<br /><br /> -常數： True<br /><br /> FixedLength<br /><br /> -預設值： False<br /><br /> -常數： True|  
|`ntext`|相等的可比較： False<br /><br /> 順序可比較： False|`Edm.String`|MaxLength<br /><br /> -預設值：1073741823<br /><br /> -常數： True<br /><br /> Unicode：<br /><br /> -預設值： False<br /><br /> -常數： True<br /><br /> FixedLength<br /><br /> -預設值： False<br /><br /> -常數： True|  
|`text`|相等的可比較： False<br /><br /> 順序可比較： False|`Edm.String`|MaxLength<br /><br /> -預設值：2147483647<br /><br /> -常數： True<br /><br /> Unicode：<br /><br /> -預設值： False<br /><br /> -常數： True<br /><br /> FixedLength<br /><br /> -預設值： False<br /><br /> -常數： True|  
|`Unique`<br /><br /> `identifier`|相等的可比較： True<br /><br /> 順序可比較： True|`Edm.Guid`|n/a|  
|`xml`|相等的可比較： False<br /><br /> 順序可比較： False|`Edm.String`|MaxLength<br /><br /> -預設值：1073741823<br /><br /> -常數： True<br /><br /> Unicode：<br /><br /> -Default： True<br /><br /> -常數： True<br /><br /> FixedLength<br /><br /> -預設值： False<br /><br /> -常數： True|  
  
## <a name="see-also"></a>另請參閱

- [CSDL、SSDL 和 MSL 規格](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
