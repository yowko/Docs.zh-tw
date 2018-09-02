---
title: LINQ to SQL 搭配緊密結合的用戶端-伺服器應用程式
ms.date: 03/30/2017
ms.assetid: e083d805-dcf6-459d-b9af-9ef0563f2dd7
ms.openlocfilehash: 9c36fc1f402d3791611af47a3a6d997db4f31167
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43408956"
---
# <a name="linq-to-sql-with-tightly-coupled-client-server-applications"></a>LINQ to SQL 搭配緊密結合的用戶端-伺服器應用程式
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 可以使用中介層上與緊密結合的展示層上的智慧型用戶端。 在唯讀資料存取的案例中，不需要開放式並行存取 (Optimistic Concurrency) 檢查或使用時間戳記的開放式並行存取，處理起來並不複雜，與簡單的非遠端案例相去不遠。 不過，當資料庫需要使用原始值的開放式並行存取檢查時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 無法提供與資料集中反覆存取資料相同的支援能力。 不過，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中介層可與任何平台上的用戶端交換資料。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 在 [!INCLUDE[vs_orcas_long](../../../../../../includes/vs-orcas-long-md.md)]提供任何基礎結構序列化到用戶端之後，追蹤實體狀態。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 可讓服務導向的架構，其中資料和展示層之間的互動是小型且相對較不可部分完成，但不會執行任何反覆存取原始值。 因此，如果您要使用緊密結合的智慧型用戶端搭配 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]，而資料庫使用以原始值為基礎的開放式並行存取，就必須實作自己的機制，讓展示層與中介層得以溝通變更。 系統設計人員可自行決定是否要在此額外工作與 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 在中介層所提供的功能之間做取捨。 另一方面，如果資料庫有時間戳記，那麼就不需要自訂變更追蹤邏輯。  
  
## <a name="see-also"></a>另請參閱  
 [使用 LINQ to SQL 的多層式架構和遠端應用程式](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)  
 [使用 Web 服務的 LINQ to SQL 多層式架構](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
 [使用多層式架構 (N-Tier) 應用程式中的資料集](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications)
