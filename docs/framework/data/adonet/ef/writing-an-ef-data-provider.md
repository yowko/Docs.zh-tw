---
title: 撰寫 Entity Framework 資料提供者
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 578de94aa191d7302b762f1cdc87d4a6810037e3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="writing-an-entity-framework-data-provider"></a>撰寫 Entity Framework 資料提供者
本章節將討論如何撰寫[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]提供者來支援非 SQL Server 資料來源。 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]包含支援 SQL Server 提供者。  
  
## <a name="introducing-the-entity-framework-provider-model"></a>Entity Framework 提供者模型簡介  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 與資料庫無關，而且您可以使用 ADO.NET 提供者模型來撰寫提供者，以便連接到各種不同的資料來源。  
  
 Entity Framework 資料提供者 (使用 ADO.NET 資料提供者模型所建置) 會執行下列功能：  
  
-   將實體資料模型 (EDM) 基本型別對應到提供者類型。  
  
-   公開提供者特有的函式。  
  
-   為給定的 DbQueryCommandTree 產生提供者特有的命令來支援 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 查詢。  
  
-   為給定的 DbModificationCommandTree 產生提供者特有的更新命令，以支援透過 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 的更新。  
  
-   公開存放結構定義的對應檔案，以便支援根據資料庫產生模型。  
  
-   透過概念模型公開中繼資料 (如資料表和檢視表)。  
  
 ![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")  
  
## <a name="sample"></a>範例  
 請參閱[Entity Framework 範例提供者](http://go.microsoft.com/fwlink/?LinkId=180616)某個[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]支援非 SQL Server 資料來源的提供者。  
  
## <a name="in-this-section"></a>本節內容  
 [SQL 產生](../../../../../docs/framework/data/adonet/ef/sql-generation.md)  
  
 [修改 SQL 產生](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md)  
  
 [提供者資訊清單規格](../../../../../docs/framework/data/adonet/ef/provider-manifest-specification.md)  
  
## <a name="see-also"></a>另請參閱  
 [處理資料提供者](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)
