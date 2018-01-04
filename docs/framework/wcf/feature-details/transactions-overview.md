---
title: "Windows Communication Foundation 交易概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transactions [WCF]
- WCF, transactions
- Windows Communication Foundation, transactions
ms.assetid: c7757854-1207-4019-8b31-552578b7d570
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6fb90d0f93e9bdf7dd9779ffd5d4b1288ba56e7a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="windows-communication-foundation-transactions-overview"></a>Windows Communication Foundation 異動概觀
異動提供了將一組動作或作業分組為單一個不可分割的執行單位。 交易就是具有下列屬性的作業集合：  
  
-   單元性 (Atomicity)。 這可確保在特定交易下完成的所有更新會被認可並變成永久性的，或確保所有更新會被取消並還原至先前的狀態。  
  
-   一致性 (Consistency)。 這可保證在交易下完成的變更會呈現從某個一致狀態轉換至另一個狀態。 例如，從支票帳戶轉帳到存款帳戶的交易並不會變更整個銀行帳戶內的總金額。  
  
-   隔離性。 這可避免交易觀察屬於其他並行交易的未經認可變更。 隔離性可提供抽象的並行，同時確保單一交易不會對其他交易的執行造成非預期的影響。  
  
-   持續性 (Durability)。 這個屬性表示在經過認可之後，對於 Managed 資源 (例如資料庫記錄) 的更新在遇到失敗時仍會持續。  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 提供了一組豐富的功能，可讓您在 Web 服務應用程式中建立分散式交易。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 實作 WS-AtomicTransaction (WS-AT) 通訊協定的支援，該通訊協定可讓 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式將交易流向可互通的應用程式，例如使用協力廠商技術建構的互通式 Web 服務。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 同時也實作 OLE Transactions 通訊協定的支援，該通訊協定可用在不需要 interop 功能來啟用交易流程的情節中。  
  
 您可以使用應用程式組態檔，將繫結設定成啟用或停用交易流程，以及設定繫結上所需要的交易通訊協定。 此外，您也可以使用組態檔設定服務層級的異動逾時。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][啟用交易流程](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)。  
  
 <xref:System.ServiceModel> 命名空間 (Namespace) 中的交易屬性可讓您完成下列工作：  
  
-   使用 <xref:System.ServiceModel.ServiceBehaviorAttribute> 屬性，以設定交易逾時和隔離等級的過濾。  
  
-   使用 <xref:System.ServiceModel.OperationBehaviorAttribute> 屬性，即可啟用交易功能並設定交易完成行為。  
  
-   使用合約方法上的 <xref:System.ServiceModel.ServiceContractAttribute> 和 <xref:System.ServiceModel.OperationContractAttribute> 屬性，即可要求、允許或拒絕交易流程。  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ServiceModel 交易屬性](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md)。  
  
## <a name="see-also"></a>請參閱  
 [ServiceModel 異動屬性](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md)  
 [啟用異動流程](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
