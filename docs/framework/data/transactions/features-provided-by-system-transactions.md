---
title: System.Transactions 所提供的功能
ms.date: 03/30/2017
ms.assetid: e458cef9-63b5-4401-b448-1536dcd9d9e5
ms.openlocfilehash: c3ef924edf34ae19be9eace85aaee5340025de7d
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205969"
---
# <a name="features-provided-by-systemtransactions"></a>System.Transactions 所提供的功能
本節說明如何使用 <xref:System.Transactions> 命名空間所提供的各項功能，來撰寫自己的交易式應用程式與資源管理員。 具體來說，本節涵蓋了如何與一或多位參與者一同建立並參與交易 (本機或分散式)。  
  
## <a name="overview-of-systemtransactions"></a>System.Transactions 概觀  
 由 <xref:System.Transactions> 命名空間的各項類別所提供的基礎結構，藉由支援 SQL Server、ADO.NET、訊息佇列 (MSMQ)，以及 Microsoft 分散式交易協調器 (MSDTC) 所啟始的交易，讓交易程式設計變得簡單又有效率。 <xref:System.Transactions> 命名空間會提供根據 <xref:System.Transactions.Transaction> 類別的明確程式撰寫模型 (Programming Model)，以及使用 <xref:System.Transactions.TransactionScope> 類別的隱含程式撰寫模型，而其中異動會由基礎結構自動管理。 如需有關如何使用這兩種模型來建立交易式應用程式的詳細資訊, 請參閱[撰寫交易式應用程式](writing-a-transactional-application.md)。  
  
 <xref:System.Transactions> 命名空間也提供讓您實作資源管理員的型別。 資源管理員會管理交易中所使用的永久性資料或變動性資料，並和交易管理員一起合作以提供應用程式單元性 (Atomicity) 和隔離性 (Isolation) 的保證。 <xref:System.Transactions> 基礎結構所提供的交易管理員可支援多個變動性資源或單一永久性資源的相關交易。 如需有關如何執行資源管理員的詳細資訊, 請參閱 <<c0>執行 Resource Manager。  
  
 當其他永久性資源管理員向交易自行登記時，透過磁碟架構交易管理員 (如 DTC) 的協調，交易管理員在不需其他動作之下，也可以將本機交易擴大至分散式交易。 <xref:System.Transactions> 基礎結構提供兩個提高效能的重要方法。  
  
- 動態擴大規模，可確保在橫跨多個分散式資源進行交易時，<xref:System.Transactions> 基礎結構只使用 MSDTC。 如需動態擴大規模的詳細資訊。 請參閱[交易管理擴大](transaction-management-escalation.md)主題。  
  
- 可提升登記，可讓資源 (例如資料庫) 取得異動的擁有權 (如果該資源是參與異動之唯一實體 (Entity) 的話)。 如果有需要，<xref:System.Transactions> 基礎結構仍可在稍後將交易管理擴大至 MSDTC。 這會進一步減少 MSDTC 的使用。 在[使用單一階段認可和可提升單一階段通知的優化](optimization-spc-and-promotable-spn.md)主題中, 會深入討論可提升的登記。  
  
 <xref:System.Transactions> 命名空間定義了三種信任層級 - AllowPartiallyTrustedCallers (APTCA)、DistributedTransactionPermission (DTP)，以及完全信任，用以限制所公開的資源型別存取權限。 如需各種信任層級的詳細資訊, 請參閱[存取資源中的安全性信任層級](security-trust-levels-in-accessing-resources.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
### <a name="writing-a-transactional-application"></a>撰寫交易式應用程式  
 <xref:System.Transactions> 命名空間會提供兩種用來建立交易式應用程式的模型。 [使用交易範圍來執行隱含交易](implementing-an-implicit-transaction-using-transaction-scope.md)描述<xref:System.Transactions>命名空間如何支援使用<xref:System.Transactions.TransactionScope>類別來建立隱含交易。  
  
 [使用 CommittableTransaction 來執行明確交易](implementing-an-explicit-transaction-using-committabletransaction.md)說明<xref:System.Transactions>命名空間如何支援使用<xref:System.Transactions.CommittableTransaction>類別來建立明確的交易。  
  
 如需有關撰寫交易式應用程式的其他主題, 請參閱[撰寫交易式應用程式](writing-a-transactional-application.md)。  
  
### <a name="implementing-a-resource-manager"></a>實作資源管理員  
 若要執行可參與交易的資源管理員, 請參閱[執行 Resource Manager](implementing-a-resource-manager.md)。 本節涵蓋了資源登記、交易認可、故障復原，以及最佳化的最佳做法。
