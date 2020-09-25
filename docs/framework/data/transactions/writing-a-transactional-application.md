---
title: 撰寫異動式應用程式
description: 在 .NET 中撰寫交易式應用程式。 將明確或隱含的程式設計模型分別搭配 Transaction 類別或 TransactionScope 類別使用。
ms.date: 03/30/2017
ms.assetid: a4d891f2-6fc8-4395-93c6-6819492406e0
ms.openlocfilehash: b4cc33939128e61a69db319491a7d2d60ab9a819
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186662"
---
# <a name="writing-a-transactional-application"></a>撰寫異動式應用程式

身為交易式應用程式設計人員，您可以利用 <xref:System.Transactions> 命名空間所提供的兩個程式撰寫模型 (Programming Model) 來建立交易。 您可以使用類別 <xref:System.Transactions.Transaction> ，或使用類別在基礎結構自動管理交易的隱含程式設計模型中，利用明確的程式設計模型 <xref:System.Transactions.TransactionScope> 。 我們建議您使用隱含交易模型來進行開發。 您可以在「 [使用交易範圍執行隱含交易](implementing-an-implicit-transaction-using-transaction-scope.md) 」主題中，找到有關如何使用交易範圍的詳細資訊。  
  
 兩種模型都支援在程式到達一致的狀態時認可交易。 一旦成功認可，就會永久地認可交易。 如果認可失敗，就會中止交易。 如果應用程式無法成功完成交易，就會嘗試中止並復原交易影響。  
  
## <a name="in-this-section"></a>本節內容  
  
### <a name="creating-a-transaction"></a>建立交易  

 <xref:System.Transactions> 命名空間會提供兩種用來建立交易的模型。 下列主題涵蓋這些模式。  
  
 [使用交易範圍實作隱含交易](implementing-an-implicit-transaction-using-transaction-scope.md)  
  
 說明 <xref:System.Transactions> 命名空間如何透過 <xref:System.Transactions.TransactionScope> 類別來支援建立隱含的交易。  
  
 [使用 CommittableTransaction 實作明確交易](implementing-an-explicit-transaction-using-committabletransaction.md)  
  
 說明 <xref:System.Transactions> 命名空間如何透過 <xref:System.Transactions.CommittableTransaction> 類別來支援建立明確的交易。  
  
### <a name="escalating-transaction-management"></a>擴大交易管理  

 當交易需要存取位於另一個應用程式定義域的資源時，或是當您想要登記到另一個永久性的資源管理員時，交易會自動擴大為受到 MSDTC 管理。 交易 [管理擴大](transaction-management-escalation.md) 主題涵蓋交易擴大。  
  
### <a name="concurrency"></a>並行  

 使用 [DependentTransaction 來管理並行](managing-concurrency-with-dependenttransaction.md) 存取的主題示範如何使用類別在非同步工作之間達成並行 <xref:System.Transactions.DependentTransaction> 。  
  
### <a name="com-interop"></a>COM+ Interop  

 [與 Enterprise Services 和 COM + 交易的互通性](interoperability-with-enterprise-services-and-com-transactions.md)主題會說明如何讓分散式交易與 com + 交易互動。  
  
### <a name="diagnostics"></a>診斷  

 [診斷追蹤](diagnostic-traces.md) 會說明如何使用基礎結構所產生的追蹤程式碼， <xref:System.Transactions> 對應用程式中的錯誤進行疑難排解。  
  
### <a name="working-within-aspnet"></a>使用 ASP.NET  

 [ASP.NET 主題中的 Using system.object](using-system-transactions-in-aspnet.md)說明如何在 <xref:System.Transactions> ASP.NET 應用程式中成功使用。
