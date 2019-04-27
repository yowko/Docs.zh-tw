---
title: 適用於 Entity Framework 之 SqlClient 的類型
ms.date: 03/30/2017
ms.assetid: f2a95ead-c845-4e97-9fb3-04b444f7ed81
ms.openlocfilehash: eb12bde1e319fde5adf20ad6cd54f8776aeda31d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879160"
---
# <a name="sqlclient-for-entity-frameworktypes"></a>適用於 Entity Framework 之 SqlClient 的類型
.NET Framework Data Provider for SQL Server (SqlClient) 提供者資訊清單檔案包含下列的清單：提供者基本型別 (Primitive Type)、每個型別的 Facet、概念和儲存體模型基本型別之間的對應，以及概念和儲存體模型基本型別之間的提升及轉換規則。  
  
 下表描述類型的 SQL Server 2008 [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)]，和[!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)]資料庫和這些類型如何對應至概念模型型別。 較新的 SQL Server 版本中引進了一些新的型別，但是舊版的 SQL Server 並不支援這些型別。 下表會說明這些類型。  
  
|提供者類型<br /><br /> 名稱|提供者類型<br /><br /> 屬性|`EDMSimpleType`<br /><br /> 名稱|Facet|  
|----------------------------|----------------------------------|------------------------------|------------|  
|`bit`|N/A|`Edm.Boolean`|N/A|  
|`tinyint`|N/A|`Edm.Byte`|N/A|  
|`smallint`|N/A|`Edm.Int16`|N/A|  
|`int`|N/A|`Edm.Int32`|N/A|  
|`bigint`|N/A|`Edm.Int64`|N/A|  
|`float`|N/A|`Edm.Double`|N/A|  
|`real`|N/A|`Edm.Double`|N/A|  
|`decimal`|N/A|`Edm.Decimal`|有效位數：<br /><br /> 最小值：1<br /><br /> 最大值：38<br /><br /> -預設值：18<br /><br /> -常數：False<br /><br /> 小數位數：<br /><br /> 最小值：0<br /><br /> 最大值：38<br /><br /> -預設值：0<br /><br /> -常數：False|  
|`numeric`|N/A|`Edm.Decimal`|有效位數：<br /><br /> 最小值：1<br /><br /> 最大值：38<br /><br /> -預設值：18<br /><br /> -常數：False<br /><br /> 小數位數：<br /><br /> 最小值：0<br /><br /> 最大值：38<br /><br /> -預設值：0<br /><br /> -常數：False|  
|`smallmoney`|N/A|`Edm.Decimal`|有效位數：<br /><br /> -預設值：10<br /><br /> -常數：True<br /><br /> 小數位數：<br /><br /> -預設值：4<br /><br /> -常數：True|  
|`money`|N/A|`Edm.Decimal`|有效位數：<br /><br /> -預設值：19<br /><br /> -常數：True<br /><br /> 小數位數：<br /><br /> -預設值：4<br /><br /> -常數：True|  
|`binary`|N/A|`Edm.Binary`|MaxLength:<br /><br /> 最小值：1<br /><br /> 最大值：8000<br /><br /> -預設值：8000<br /><br /> -常數：False<br /><br /> FixedLength:<br /><br /> -預設值：True<br /><br /> -常數：True|  
|`varbinary`|N/A|`Edm.Binary`|MaxLength:<br /><br /> 最小值：1<br /><br /> 最大值：8000<br /><br /> -預設值：8000<br /><br /> -常數：False<br /><br /> FixedLength:<br /><br /> -預設值：False<br /><br /> -常數：True|  
|`varbinary(max)`<br /><br /> 注意:中不支援此類型[!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)]。|N/A|`Edm.Binary`|MaxLength:<br /><br /> -預設值：214748364780<br /><br /> -常數：True<br /><br /> FixedLength:<br /><br /> -預設值：False<br /><br /> -常數：True|  
|`image`|N/A|`Edm.Binary`|MaxLength:<br /><br /> -預設值：2147483647<br /><br /> -常數：True<br /><br /> FixedLength:<br /><br /> -預設值：False<br /><br /> -常數：True|  
|`timestamp`|N/A|`Edm.Binary`|MaxLength:<br /><br /> -預設值：8<br /><br /> -常數：True<br /><br /> FixedLength:<br /><br /> -預設值：True<br /><br /> -常數：True|  
|`rowversion`|N/A|`Edm.Binary`|MaxLength:<br /><br /> -預設值：8<br /><br /> -常數：True<br /><br /> FixedLength:<br /><br /> -預設值：True<br /><br /> -常數：True|  
|`smalldatetime`|N/A|`Edm.DateTime`|有效位數：<br /><br /> -預設值：0<br /><br /> -常數：True|  
|`datetime`|N/A|`Edm.DateTime`|有效位數：<br /><br /> -預設值：3<br /><br /> -常數：True|  
|`date`<br /><br /> 注意:在 SQL Server 2005 和 SQL Server 2000 中不支援此類型。|N/A|`Edm.DateTime`|有效位數：<br /><br /> -預設值：0<br /><br /> -常數：False|  
|`time`<br /><br /> 注意:在 SQL Server 2005 和 SQL Server 2000 中不支援此類型。|N/A|`Edm.Time`|有效位數：<br /><br /> -預設值：7<br /><br /> -常數：False|  
|`datetime2`<br /><br /> 注意:在 SQL Server 2005 和 SQL Server 2000 中不支援此類型。|N/A|`Edm.DateTime`|有效位數：<br /><br /> -預設值：7<br /><br /> -常數：False|  
|`datetimeoffset`<br /><br /> 注意:在 SQL Server 2005 和 SQL Server 2000 中不支援此類型。|N/A|`Edm.DateTimeOffset`|有效位數：<br /><br /> -預設值：7<br /><br /> -常數：False|  
|`nvarchar`<br /><br /> 注意:中不支援此類型[!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)]。|N/A|`Edm.String`|MaxLength:<br /><br /> 最小值：1<br /><br /> 最大值：4000<br /><br /> -預設值：4000<br /><br /> -常數：False<br /><br /> Unicode：<br /><br /> -預設值：True<br /><br /> -常數：True<br /><br /> FixedLength:<br /><br /> -預設值：False<br /><br /> -常數：True|  
|`varchar`<br /><br /> 注意:中不支援此類型[!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)]。|N/A|`Edm.String`|MaxLength:<br /><br /> 最小值：1<br /><br /> 最大值：8000<br /><br /> -預設值：8000<br /><br /> -常數：False<br /><br /> Unicode：<br /><br /> -預設值：False<br /><br /> -常數：True<br /><br /> FixedLength:<br /><br /> -預設值：False<br /><br /> -常數：True|  
|`char`|N/A|`Edm.String`|MaxLength:<br /><br /> 最小值：1<br /><br /> 最大值：8000<br /><br /> -預設值：8000<br /><br /> -常數：False<br /><br /> Unicode：<br /><br /> -預設值：False<br /><br /> -常數：True<br /><br /> FixedLength:<br /><br /> -預設值：True<br /><br /> -常數：True|  
|`nchar`|N/A|`Edm.String`|MaxLength:<br /><br /> 最小值：1<br /><br /> 最大值：4000<br /><br /> -預設值：4000<br /><br /> -常數：False<br /><br /> Unicode：<br /><br /> -預設值：True<br /><br /> -常數：True<br /><br /> FixedLength:<br /><br /> -預設值：True<br /><br /> -常數：True|  
|`varchar`(`max`)|N/A|`Edm.String`|MaxLength:<br /><br /> -預設值：2147483647<br /><br /> -常數：True<br /><br /> Unicode：<br /><br /> -預設值：False<br /><br /> -常數：True<br /><br /> FixedLength:<br /><br /> -預設值：False<br /><br /> -常數：True|  
|`nvarchar`(`max`)|N/A|`Edm.String`|MaxLength:<br /><br /> -預設值：1073741823<br /><br /> -常數：True<br /><br /> Unicode：<br /><br /> -預設值：True<br /><br /> -常數：True<br /><br /> FixedLength:<br /><br /> -預設值：False<br /><br /> -常數：True|  
|`ntext`|等號比較：False<br /><br /> 可比較順序：False|`Edm.String`|MaxLength:<br /><br /> -預設值：1073741823<br /><br /> -常數：True<br /><br /> Unicode：<br /><br /> -預設值：False<br /><br /> -常數：True<br /><br /> FixedLength:<br /><br /> -預設值：False<br /><br /> -常數：True|  
|`text`|等號比較：False<br /><br /> 可比較順序：False|`Edm.String`|MaxLength:<br /><br /> -預設值：2147483647<br /><br /> -常數：True<br /><br /> Unicode：<br /><br /> -預設值：False<br /><br /> -常數：True<br /><br /> FixedLength:<br /><br /> -預設值：False<br /><br /> -常數：True|  
|`Unique`<br /><br /> `identifier`|等號比較：True<br /><br /> 可比較順序：True|`Edm.Guid`|N/A|  
|`xml`|等號比較：False<br /><br /> 可比較順序：False|`Edm.String`|MaxLength:<br /><br /> -預設值：1073741823<br /><br /> -常數：True<br /><br /> Unicode：<br /><br /> -預設值：True<br /><br /> -常數：True<br /><br /> FixedLength:<br /><br /> -預設值：False<br /><br /> -常數：True|  
  
## <a name="see-also"></a>另請參閱

- [CSDL、SSDL 和 MSL 規格](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
