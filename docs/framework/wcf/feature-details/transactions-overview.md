---
title: Windows Communication Foundation 異動概觀
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF]
- WCF, transactions
- Windows Communication Foundation, transactions
ms.assetid: c7757854-1207-4019-8b31-552578b7d570
ms.openlocfilehash: 42276a9b450b6f0664901747239195ab13f7c44d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223104"
---
# <a name="windows-communication-foundation-transactions-overview"></a>Windows Communication Foundation 異動概觀
異動提供了將一組動作或作業分組為單一個不可分割的執行單位。 交易就是具有下列屬性的作業集合：  
  
-   單元性 (Atomicity)。 這可確保在特定異動下完成的所有更新會被認可並變成永久性的，或確保所有更新會被取消並還原至先前的狀態。  
  
-   一致性 (Consistency)。 這可保證在異動下完成的變更會呈現從某個一致狀態轉換至另一個狀態。 例如，從支票帳戶轉帳到存款帳戶的異動並不會變更整個銀行帳戶內的總金額。  
  
-   隔離性。 這可避免異動觀察屬於其他並行異動的未經認可變更。 隔離性可提供抽象的並行，同時確保單一異動不會對其他異動的執行造成非預期的影響。  
  
-   持續性 (Durability)。 這個屬性表示在經過認可之後，對於 Managed 資源 (例如資料庫記錄) 的更新在遇到失敗時仍會持續。  
  
 Windows Communication Foundation (WCF) 提供一組豐富的功能，可讓您在 Web 服務應用程式中建立分散式的交易。  
  
 WCF 實作 WS-AtomicTransaction (WS-AT) 通訊協定，可讓 WCF 應用程式，將交易傳送至可互通的應用程式，例如使用協力廠商技術建置互通的 Web 服務的支援。 此外，WCF 也會實作 OLE Transactions 通訊協定，可用在案例中，您不需要 interop 功能來啟用交易流程的支援。  
  
 您可以使用應用程式組態檔，將繫結程序設定成啟用或停用異動流程，以及設定繫結程序上所需要的異動通訊協定。 此外，您也可以使用組態檔設定服務層級的異動逾時。 如需詳細資訊，請參閱 <<c0> [ 啟用交易流程](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)。  
  
 <xref:System.ServiceModel> 命名空間 (Namespace) 中的異動屬性可讓您完成下列工作：  
  
-   使用 <xref:System.ServiceModel.ServiceBehaviorAttribute> 屬性，以設定異動逾時和隔離等級的過濾。  
  
-   使用 <xref:System.ServiceModel.OperationBehaviorAttribute> 屬性，即可啟用交易功能並設定交易完成行為。  
  
-   使用合約方法上的 <xref:System.ServiceModel.ServiceContractAttribute> 和 <xref:System.ServiceModel.OperationContractAttribute> 屬性，即可要求、允許或拒絕交易流程。  
  
 如需詳細資訊，請參閱 < [ServiceModel 異動屬性](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md)。  
  
## <a name="see-also"></a>另請參閱

- [ServiceModel 交易屬性](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md)
- [啟用交易流程](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
