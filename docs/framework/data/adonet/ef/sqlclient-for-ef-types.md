---
title: "適用於 Entity Framework 之 SqlClient 的類型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2a95ead-c845-4e97-9fb3-04b444f7ed81
caps.latest.revision: "9"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: b04a7199fefc5df93d5e3472163d16c66e9279c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="sqlclient-for-entity-frameworktypes"></a>適用於 Entity Framework 之 SqlClient 的類型
.NET Framework Data Provider for SQL Server (SqlClient) 提供者資訊清單檔案包含下列的清單：提供者基本型別 (Primitive Type)、每個型別的 Facet、概念和儲存體模型基本型別之間的對應，以及概念和儲存體模型基本型別之間的提升及轉換規則。  
  
 下表描述 SQL Server 2008，型別[!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)]，和[!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)]資料庫和這些類型如何對應至概念模型型別。 較新的 SQL Server 版本中引進了一些新的型別，但是舊版的 SQL Server 並不支援這些型別。 下表會說明這些類型。  
  
|提供者類型<br /><br /> name|提供者類型<br /><br /> 屬性|`EDMSimpleType`<br /><br /> name|Facet|  
|----------------------------|----------------------------------|------------------------------|------------|  
|`bit`|N/A|`Edm.Boolean`|N/A|  
|`tinyint`|N/A|`Edm.Byte`|N/A|  
|`smallint`|N/A|`Edm.Int16`|N/A|  
|`int`|N/A|`Edm.Int32`|N/A|  
|`bigint`|N/A|`Edm.Int64`|N/A|  
|`float`|N/A|`Edm.Double`|N/A|  
|`real`|N/A|`Edm.Double`|N/A|  
|`decimal`|N/A|`Edm.Decimal`|有效位數：<br /><br /> -最小值： 1<br /><br /> -最大： 38<br /><br /> -預設值： 18<br /><br /> -常數： False<br /><br /> 小數位數：<br /><br /> -最小值： 0<br /><br /> -最大： 38<br /><br /> -預設值： 0<br /><br /> -常數： False|  
|`numeric`|N/A|`Edm.Decimal`|有效位數：<br /><br /> -最小值： 1<br /><br /> -最大： 38<br /><br /> -預設值： 18<br /><br /> -常數： False<br /><br /> 小數位數：<br /><br /> -最小值： 0<br /><br /> -最大： 38<br /><br /> -預設值： 0<br /><br /> -常數： False|  
|`smallmoney`|N/A|`Edm.Decimal`|有效位數：<br /><br /> -預設值： 10<br /><br /> -常數： True<br /><br /> 小數位數：<br /><br /> -預設值： 4<br /><br /> -常數： True|  
|`money`|N/A|`Edm.Decimal`|有效位數：<br /><br /> -預設值： 19<br /><br /> -常數： True<br /><br /> 小數位數：<br /><br /> -預設值： 4<br /><br /> -常數： True|  
|`binary`|N/A|`Edm.Binary`|MaxLength:<br /><br /> -最小值： 1<br /><br /> -最大： 8000<br /><br /> -預設值： 8000<br /><br /> -常數： False<br /><br /> FixedLength:<br /><br /> -預設值： True<br /><br /> -常數： True|  
|`varbinary`|N/A|`Edm.Binary`|MaxLength:<br /><br /> -最小值： 1<br /><br /> -最大： 8000<br /><br /> -預設值： 8000<br /><br /> -常數： False<br /><br /> FixedLength:<br /><br /> -預設： False<br /><br /> -常數： True|  
|`varbinary(max)`<br /><br /> 注意： 此類型不支援[!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)]。|N/A|`Edm.Binary`|MaxLength:<br /><br /> -預設值： 214748364780<br /><br /> -常數： True<br /><br /> FixedLength:<br /><br /> -預設： False<br /><br /> -常數： True|  
|`image`|N/A|`Edm.Binary`|MaxLength:<br /><br /> -預設值： 2147483647<br /><br /> -常數： True<br /><br /> FixedLength:<br /><br /> -預設： False<br /><br /> -常數： True|  
|`timestamp`|N/A|`Edm.Binary`|MaxLength:<br /><br /> -預設值： 8<br /><br /> -常數： True<br /><br /> FixedLength:<br /><br /> -預設值： True<br /><br /> -常數： True|  
|`rowversion`|N/A|`Edm.Binary`|MaxLength:<br /><br /> -預設值： 8<br /><br /> -常數： True<br /><br /> FixedLength:<br /><br /> -預設值： True<br /><br /> -常數： True|  
|`smalldatetime`|N/A|`Edm.DateTime`|有效位數：<br /><br /> -預設值： 0<br /><br /> -常數： True|  
|`datetime`|N/A|`Edm.DateTime`|有效位數：<br /><br /> -預設： 3<br /><br /> -常數： True|  
|`date`<br /><br /> 注意： 在 SQL Server 2005 和 SQL Server 2000 中不支援此類型。|N/A|`Edm.DateTime`|有效位數：<br /><br /> -預設值： 0<br /><br /> -常數： False|  
|`time`<br /><br /> 注意： 在 SQL Server 2005 和 SQL Server 2000 中不支援此類型。|N/A|`Edm.Time`|有效位數：<br /><br /> -預設值： 7<br /><br /> -常數： False|  
|`datetime2`<br /><br /> 注意： 在 SQL Server 2005 和 SQL Server 2000 中不支援此類型。|N/A|`Edm.DateTime`|有效位數：<br /><br /> -預設值： 7<br /><br /> -常數： False|  
|`datetimeoffset`<br /><br /> 注意： 在 SQL Server 2005 和 SQL Server 2000 中不支援此類型。|N/A|`Edm.DateTimeOffset`|有效位數：<br /><br /> -預設值： 7<br /><br /> -常數： False|  
|`nvarchar`<br /><br /> 注意： 此類型不支援[!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)]。|N/A|`Edm.String`|MaxLength:<br /><br /> -最小值： 1<br /><br /> -最大： 4000<br /><br /> -預設值： 4000<br /><br /> -常數： False<br /><br /> Unicode:<br /><br /> -預設值： True<br /><br /> -常數： True<br /><br /> FixedLength:<br /><br /> -預設： False<br /><br /> -常數： True|  
|`varchar`<br /><br /> 注意： 此類型不支援[!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)]。|N/A|`Edm.String`|MaxLength:<br /><br /> -最小值： 1<br /><br /> -最大： 8000<br /><br /> -預設值： 8000<br /><br /> -常數： False<br /><br /> Unicode:<br /><br /> -預設： False<br /><br /> -常數： True<br /><br /> FixedLength:<br /><br /> -預設： False<br /><br /> -常數： True|  
|`char`|N/A|`Edm.String`|MaxLength:<br /><br /> -最小值： 1<br /><br /> -最大： 8000<br /><br /> -預設值： 8000<br /><br /> -常數： False<br /><br /> Unicode:<br /><br /> -預設： False<br /><br /> -常數： True<br /><br /> FixedLength:<br /><br /> -預設值： True<br /><br /> -常數： True|  
|`nchar`|N/A|`Edm.String`|MaxLength:<br /><br /> -最小值： 1<br /><br /> -最大： 4000<br /><br /> -預設值： 4000<br /><br /> -常數： False<br /><br /> Unicode:<br /><br /> -預設值： True<br /><br /> -常數： True<br /><br /> FixedLength:<br /><br /> -預設值： True<br /><br /> -常數： True|  
|`varchar`(`max`)|N/A|`Edm.String`|MaxLength:<br /><br /> -預設值： 2147483647<br /><br /> -常數： True<br /><br /> Unicode:<br /><br /> -預設： False<br /><br /> -常數： True<br /><br /> FixedLength:<br /><br /> -預設： False<br /><br /> -常數： True|  
|`nvarchar`(`max`)|N/A|`Edm.String`|MaxLength:<br /><br /> -預設值： 1073741823<br /><br /> -常數： True<br /><br /> Unicode:<br /><br /> -預設值： True<br /><br /> -常數： True<br /><br /> FixedLength:<br /><br /> -預設： False<br /><br /> -常數： True|  
|`ntext`|相等比較： False<br /><br /> 可比較順序： False|`Edm.String`|MaxLength:<br /><br /> -預設值： 1073741823<br /><br /> -常數： True<br /><br /> Unicode:<br /><br /> -預設： False<br /><br /> -常數： True<br /><br /> FixedLength:<br /><br /> -預設： False<br /><br /> -常數： True|  
|`text`|相等比較： False<br /><br /> 可比較順序： False|`Edm.String`|MaxLength:<br /><br /> -預設值： 2147483647<br /><br /> -常數： True<br /><br /> Unicode:<br /><br /> -預設： False<br /><br /> -常數： True<br /><br /> FixedLength:<br /><br /> -預設： False<br /><br /> -常數： True|  
|`Unique`<br /><br /> `identifier`|相等比較： True<br /><br /> 可比較順序： True|`Edm.Guid`|N/A|  
|`xml`|相等比較： False<br /><br /> 可比較順序： False|`Edm.String`|MaxLength:<br /><br /> -預設值： 1073741823<br /><br /> -常數： True<br /><br /> Unicode:<br /><br /> -預設值： True<br /><br /> -常數： True<br /><br /> FixedLength:<br /><br /> -預設： False<br /><br /> -常數： True|  
  
## <a name="see-also"></a>請參閱  
 [CSDL、SSDL 和 MSL 規格](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
