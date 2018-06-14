---
title: 範例提供者中的 SQL 產生
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: 7275a67927d7692dc943e2555d65d1f7d6e4ba5a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762149"
---
# <a name="sql-generation-in-the-sample-provider"></a>範例提供者中的 SQL 產生
[Entity Framework 範例提供者](http://go.microsoft.com/fwlink/?LinkId=180616)示範之 ADO.NET 資料提供者支援的新元件[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。  它會使用 SQL Server 2005 資料庫並且實作成 System.Data.SqlClient ADO.NET 2.0 資料提供者的包裝函式。  
  
 此範例提供者的 SQL 產生模組 (位於 SQL Generation 資料夾底下，但 DmlSqlGenerator.cs 檔案除外) 會接受輸入 DbQueryCommandTree 並且產生單一 SQL SELECT 陳述式。  
  
## <a name="in-this-section"></a>本章節內容  
 本節包括下列主題：  
  
 [架構和設計](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [逐步解說：SQL 產生](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a>另請參閱  
 [SQL 產生](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
