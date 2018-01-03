---
title: "撰寫異動式應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4d891f2-6fc8-4395-93c6-6819492406e0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9fab355da61ea7445e429cfc4e336a14b588e30c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="writing-a-transactional-application"></a>撰寫異動式應用程式
身為交易式應用程式設計人員，您可以利用 <xref:System.Transactions> 命名空間所提供的兩個程式撰寫模型 (Programming Model) 來建立交易。 您可以利用明確的程式設計模型使用<xref:System.Transactions.Transaction>類別或隱含的程式設計模型，交易自動管理基礎結構，使用<xref:System.Transactions.TransactionScope>類別。 我們建議您開發使用隱含交易模式。 您可以找到有關如何使用交易範圍中的詳細資訊[實作隱含交易使用交易範圍](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)主題。  
  
 兩種模型都支援在程式到達一致的狀態時認可交易。 一旦成功認可，就會永久地認可交易。 如果認可失敗，就會中止交易。 如果應用程式無法成功完成交易，就會嘗試中止並復原交易影響。  
  
## <a name="in-this-section"></a>本節內容  
  
### <a name="creating-a-transaction"></a>建立交易  
 <xref:System.Transactions> 命名空間會提供兩種用來建立交易的模型。 下列主題涵蓋這些模式。  
  
 [使用異動範圍實作隱含異動](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)  
  
 說明 <xref:System.Transactions> 命名空間如何透過 <xref:System.Transactions.TransactionScope> 類別來支援建立隱含的交易。  
  
 [使用 CommittableTransaction 實作明確異動](../../../../docs/framework/data/transactions/implementing-an-explicit-transaction-using-committabletransaction.md)  
  
 說明 <xref:System.Transactions> 命名空間如何透過 <xref:System.Transactions.CommittableTransaction> 類別來支援建立明確的交易。  
  
### <a name="escalating-transaction-management"></a>擴大交易管理  
 當交易需要存取位於另一個應用程式定義域的資源時，或是當您想要登記到另一個永久性的資源管理員時，交易會自動擴大為受到 MSDTC 管理。 交易擴大在講述[交易管理擴大](../../../../docs/framework/data/transactions/transaction-management-escalation.md)主題。  
  
### <a name="concurrency"></a>並行  
 本主題[DependentTransaction 管理並行存取](../../../../docs/framework/data/transactions/managing-concurrency-with-dependenttransaction.md)示範如何達成並行，使用非同步工作之間<xref:System.Transactions.DependentTransaction>類別。  
  
### <a name="com-interop"></a>COM+ Interop  
 本主題[互通性與 Enterprise Services 和 COM + 交易](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md)說明可以讓您與 COM + 交易進行互動的分散式的交易的方式。  
  
### <a name="diagnostics"></a>診斷  
 [診斷追蹤](../../../../docs/framework/data/transactions/diagnostic-traces.md)描述如何使用所產生的追蹤程式碼<xref:System.Transactions>基礎結構，以針對您的應用程式錯誤進行疑難排解。  
  
### <a name="working-within-aspnet"></a>使用 ASP.NET  
 [ASP.NET 中的使用 System.Transactions](../../../../docs/framework/data/transactions/using-system-transactions-in-aspnet.md)主題描述如何成功使用<xref:System.Transactions>ASP.NET 應用程式內。
