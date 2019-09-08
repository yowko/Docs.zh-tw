---
title: SQL Server 二進位和大量數值資料
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: 4d941ad6b7865112b45fd8c20ad89e9236e17b9d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791680"
---
# <a name="sql-server-binary-and-large-value-data"></a>SQL Server 二進位和大量數值資料
SQL Server 提供 `max` 規範，可擴充 `varchar`、`nvarchar` 和 `varbinary` 資料類型的儲存容量。 `varchar(max)`、 `nvarchar(max)`和`varbinary(max)`統稱為*大數值資料類型*。 您可以使用大數值資料型別來儲存最多可達 2^31-1 位元組的資料。  
  
 SQL Server 2008 導入了 FILESTREAM 屬性。這個屬性不是資料型別，而是可針對資料行定義的屬性，允許大數值資料儲存在檔案系統上，而非資料庫中。  
  
## <a name="in-this-section"></a>本節內容  
 [在 ADO.NET 中修改大量數值 (max) 資料](modifying-large-value-max-data.md)  
 說明如何使用大型值資料類型。  
  
 [FILESTREAM 資料](filestream-data.md)  
 說明如何使用儲存在 SQL Server 2008 中的大數值資料搭配 FILESTREAM 屬性。  
  
## <a name="see-also"></a>另請參閱

- [SQL Server 資料類型和 ADO.NET](sql-server-data-types.md)
- [ADO.NET 中的 SQL Server 資料作業](sql-server-data-operations.md)
- [在 ADO.NET 中擷取和修改資料](../retrieving-and-modifying-data.md)
- [ADO.NET 概觀](../ado-net-overview.md)
