---
title: SQL Server 二進位和大量數值資料
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: a9296e83b0f4e4352423470433670bb2cbe5a248
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183035"
---
# <a name="sql-server-binary-and-large-value-data"></a>SQL Server 二進位和大量數值資料

SQL Server 提供 `max` 指定名稱，可擴充 `varchar`、`nvarchar` 和 `varbinary` 資料類型的儲存容量。 `varchar(max)`、`nvarchar(max)` 和 `varbinary(max)` 統稱為「大數值資料類型」**。 您可以使用大數值資料類型來儲存最多可達 2^31-1 位元組的資料。  
  
 SQL Server 2008 引進了 FILESTREAM 屬性，其不是資料類型，而是可定義於資料行上的屬性，能夠將大數值資料儲存於檔案系統，而不是資料庫中。  
  
## <a name="in-this-section"></a>本節內容  

 [修改 ADO.NET 中的大型值 (最大) 資料](modifying-large-value-max-data.md)  
 描述如何使用大數值資料類型。  
  
 [FILESTREAM 資料](filestream-data.md)  
 描述如何使用以 FILESTREAM 屬性儲存在 SQL Server 2008 中的大型值資料。  
  
## <a name="see-also"></a>另請參閱

- [SQL Server 資料類型和 ADO.NET](sql-server-data-types.md)
- [ADO.NET 中的 SQL Server 資料作業](sql-server-data-operations.md)
- [在 ADO.NET 中傳送和修改資料](../retrieving-and-modifying-data.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
