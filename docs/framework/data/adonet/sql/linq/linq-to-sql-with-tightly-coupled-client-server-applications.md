---
title: LINQ to SQL 搭配緊密結合的用戶端-伺服器應用程式
ms.date: 03/30/2017
ms.assetid: e083d805-dcf6-459d-b9af-9ef0563f2dd7
ms.openlocfilehash: f094bb319a4ca5241e60993770c9c49c3151635c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359916"
---
# <a name="linq-to-sql-with-tightly-coupled-client-server-applications"></a>LINQ to SQL 搭配緊密結合的用戶端-伺服器應用程式
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 可以使用中介層上利用緊密結合的展示層上的智慧型用戶端。 在唯讀資料存取的案例中，不需要開放式並行存取 (Optimistic Concurrency) 檢查或使用時間戳記的開放式並行存取，處理起來並不複雜，與簡單的非遠端案例相去不遠。 不過，當資料庫需要使用原始值的開放式並行存取檢查時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 無法提供與資料集中反覆存取資料相同的支援能力。 不過，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中介層可與任何平台上的用戶端交換資料。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 在[!INCLUDE[vs_orcas_long](../../../../../../includes/vs-orcas-long-md.md)]提供基礎結構之後已序列化到用戶端追蹤實體狀態。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 可讓資料和展示層之間的互動的小型和相對不可部分完成的服務導向的架構，但不會執行任何往返的原始值。 因此，如果您要使用緊密結合的智慧型用戶端搭配 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]，而資料庫使用以原始值為基礎的開放式並行存取，就必須實作自己的機制，讓展示層與中介層得以溝通變更。 系統設計人員可自行決定是否要在此額外工作與 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 在中介層所提供的功能之間做取捨。 另一方面，如果資料庫有時間戳記，那麼就不需要自訂變更追蹤邏輯。  
  
## <a name="see-also"></a>另請參閱  
 [使用 LINQ to SQL 的多層式架構和遠端應用程式](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)  
 [使用 Web 服務的 LINQ to SQL 多層式架構](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
 [使用多層式架構 (N-Tier) 應用程式中的資料集](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20)
