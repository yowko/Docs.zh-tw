---
title: "撰寫交易式應用程式  | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a4d891f2-6fc8-4395-93c6-6819492406e0
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 撰寫交易式應用程式 
身為交易式應用程式設計人員，您可以利用 <xref:System.Transactions> 命名空間所提供的兩個程式撰寫模型 \(Programming Model\) 來建立交易。您可以藉由 <xref:System.Transactions.Transaction> 類別來使用明確的程式撰寫模型，或是藉由 <xref:System.Transactions.TransactionScope> 類別來使用隱含的程式撰寫模型，以便透過基礎結構自動管理交易。建議您使用隱含交易模型進行開發。您可以在[使用交易範圍實作隱含交易 ](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)主題中找到有關如何使用交易範圍的詳細資訊。  
  
 兩種模型都支援在程式到達一致的狀態時認可交易。一旦成功認可，就會永久地認可交易。如果認可失敗，就會中止交易。如果應用程式無法成功完成交易，就會嘗試中止並復原交易影響。  
  
## 本章節內容  
  
### 建立交易  
 <xref:System.Transactions> 命名空間會提供兩種用來建立交易的模型。下列主題涵蓋這些模式。  
  
 [使用交易範圍實作隱含交易 ](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)  
  
 說明 <xref:System.Transactions> 命名空間如何透過 <xref:System.Transactions.TransactionScope> 類別來支援建立隱含的交易。  
  
 [使用 CommittableTransaction 實作明確交易 ](../../../../docs/framework/data/transactions/implementing-an-explicit-transaction-using-committabletransaction.md)  
  
 說明 <xref:System.Transactions> 命名空間如何透過 <xref:System.Transactions.CommittableTransaction> 類別來支援建立明確的交易。  
  
### 擴大交易管理  
 當交易需要存取位於另一個應用程式定義域的資源時，或是當您想要登記到另一個永久性的資源管理員時，交易會自動擴大為受到 MSDTC 管理。[交易管理擴大規模案例 ](../../../../docs/framework/data/transactions/transaction-management-escalation.md) 主題涵蓋交易範圍擴大。  
  
### 並行  
 [使用 DependentTransaction 管理並行存取 ](../../../../docs/framework/data/transactions/managing-concurrency-with-dependenttransaction.md) 主題示範如何使用 <xref:System.Transactions.DependentTransaction> 類別來達到非同步工作之間的並行狀態。  
  
### COM\+ Interop  
 [與 Enterprise Services 和 COM\+ 交易的互通性 ](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md)主題說明如何讓分散式交易與 COM\+ 交易互動。  
  
### 診斷  
 [診斷追蹤 ](../../../../docs/framework/data/transactions/diagnostic-traces.md)說明如何使用 <xref:System.Transactions> 基礎結構所產生的追蹤程式碼來疑難排解應用程式中的錯誤。  
  
### 使用 ASP.NET  
 [在 ASP.NET 中使用 System.Transactions](../../../../docs/framework/data/transactions/using-system-transactions-in-aspnet.md) 主題說明如何成功運用 ASP.NET 應用程式中的 <xref:System.Transactions>。