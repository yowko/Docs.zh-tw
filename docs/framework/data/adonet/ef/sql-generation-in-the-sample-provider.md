---
title: 範例提供者中的 SQL 產生
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: a59f1fecf85d63208c3388204c962b5838902ba7
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854312"
---
# <a name="sql-generation-in-the-sample-provider"></a>範例提供者中的 SQL 產生
[Entity Framework 範例提供者](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0)會示範支援 Entity Framework 的 ADO.NET 資料提供者的新元件。  它會使用 SQL Server 2005 資料庫並且實作成 System.Data.SqlClient ADO.NET 2.0 資料提供者的包裝函式。  
  
 此範例提供者的 SQL 產生模組 (位於 SQL Generation 資料夾底下，但 DmlSqlGenerator.cs 檔案除外) 會接受輸入 DbQueryCommandTree 並且產生單一 SQL SELECT 陳述式。  
  
## <a name="in-this-section"></a>本節內容  
 本節包括下列主題：  
  
 [架構和設計](architecture-and-design.md)  
  
 [逐步解說：SQL 產生](walkthrough-sql-generation.md)  
  
## <a name="see-also"></a>另請參閱

- [SQL 產生](sql-generation.md)
