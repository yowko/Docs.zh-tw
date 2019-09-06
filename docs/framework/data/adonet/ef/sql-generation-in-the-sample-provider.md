---
title: 範例提供者中的 SQL 產生
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: d0e058cdc4dd3f7a1a04ab6eea5acf4d3deabb89
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248502"
---
# <a name="sql-generation-in-the-sample-provider"></a>範例提供者中的 SQL 產生
[Entity Framework 範例提供者](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0)會示範支援的[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]ADO.NET 資料提供者的新元件。  它會使用 SQL Server 2005 資料庫並且實作成 System.Data.SqlClient ADO.NET 2.0 資料提供者的包裝函式。  
  
 此範例提供者的 SQL 產生模組 (位於 SQL Generation 資料夾底下，但 DmlSqlGenerator.cs 檔案除外) 會接受輸入 DbQueryCommandTree 並且產生單一 SQL SELECT 陳述式。  
  
## <a name="in-this-section"></a>本節內容  
 本節包括下列主題：  
  
 [架構和設計](architecture-and-design.md)  
  
 [逐步解說：SQL 產生](walkthrough-sql-generation.md)  
  
## <a name="see-also"></a>另請參閱

- [SQL 產生](sql-generation.md)
