---
title: 異動模型
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: 8731b72d0657aa420dbb020e216c3af059916ce9
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517779"
---
# <a name="transaction-models"></a>異動模型
本主題描述異動程式設計模型與 Microsoft 提供的基礎結構元件之間的關係。  
  
 當使用交易的 Windows Communication Foundation (WCF) 中，務必了解您不是選取不同的交易式模型之間，但而不在不同層整合與一致模型的運作。  
  
 下列幾節詳細描述三個主要的異動元件。  
  
## <a name="windows-communication-foundation-transactions"></a>Windows Communication Foundation 異動  
 在 WCF 中的交易支援可讓您撰寫交易式服務。 此外，它對 WS-AtomicTransaction (WS-AT) 通訊協定的支援，與應用程式可以使異動流向使用 WCF 或協力廠商技術建置的 Web 服務。  
  
 在 WCF 服務或應用程式中，WCF 交易功能會提供屬性和組態以宣告方式指定基礎結構如何及何時應該建立、 流動，並同步處理交易。  
  
## <a name="systemtransactions-transactions"></a>System.Transactions 異動  
 <xref:System.Transactions> 命名空間會提供根據 <xref:System.Transactions.Transaction> 類別的明確程式設計模型，以及使用 <xref:System.Transactions.TransactionScope> 類別的隱含程式設計模型，而其中交易會由基礎結構自動管理。  
  
 如需如何建立交易式應用程式使用這兩種模型的詳細資訊，請參閱[撰寫交易式應用程式](https://go.microsoft.com/fwlink/?LinkId=94947)。  
  
 WCF 服務或應用程式，<xref:System.Transactions>提供程式設計模型，建立用戶端應用程式內的交易和明確交易，與互動時所需，在服務中。  
  
## <a name="msdtc-transactions"></a>MSDTC 異動  
 Microsoft Distributed Transaction Coordinator (MSDTC) 是對分散式異動提供支援的異動管理員。  
  
 如需詳細資訊，請參閱 < [DTC 程式設計人員參考](https://go.microsoft.com/fwlink/?LinkId=94948)。  
  
 在 WCF 服務或應用程式中，MSDTC 會提供用戶端或服務中建立的異動協調基礎結構。
