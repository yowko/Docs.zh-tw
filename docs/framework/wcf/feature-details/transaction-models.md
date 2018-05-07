---
title: 異動模型
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: 9efe8c6994cc80957b707bbae0885a3c5896f70a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="transaction-models"></a>異動模型
本主題描述異動程式設計模型與 Microsoft 提供的基礎結構元件之間的關係。  
  
 當使用 Windows Communication Foundation (WCF) 的交易，務必了解，您不選取不同的交易式模型之間而不在不同層整合與一致的模型上運作。  
  
 下列幾節詳細描述三個主要的異動元件。  
  
## <a name="windows-communication-foundation-transactions"></a>Windows Communication Foundation 異動  
 在 WCF 中的交易支援可讓您撰寫交易式服務。 此外，透過它對 Ws-atomictransaction (WS-AT) 通訊協定的支援，應用程式可以使異動流向使用 WCF 或協力廠商技術建置的 Web 服務。  
  
 在 WCF 服務或應用程式中，WCF 交易功能提供屬性和組態，用於以宣告方式指定基礎結構如何及何時應該建立、 流動和同步化交易。  
  
## <a name="systemtransactions-transactions"></a>System.Transactions 異動  
 <xref:System.Transactions> 命名空間會提供根據 <xref:System.Transactions.Transaction> 類別的明確程式設計模型，以及使用 <xref:System.Transactions.TransactionScope> 類別的隱含程式設計模型，而其中交易會由基礎結構自動管理。  
  
 如需如何建立交易式應用程式使用這兩個模型的詳細資訊，請參閱[撰寫異動應用程式](http://go.microsoft.com/fwlink/?LinkId=94947)。  
  
 中的 WCF 服務或應用程式，<xref:System.Transactions>提供程式設計模型，以用戶端應用程式中建立交易並明確交易，需要時與互動，在服務中。  
  
## <a name="msdtc-transactions"></a>MSDTC 異動  
 Microsoft Distributed Transaction Coordinator (MSDTC) 是對分散式異動提供支援的異動管理員。  
  
 如需詳細資訊，請參閱[DTC 程式設計人員參考](http://go.microsoft.com/fwlink/?LinkId=94948)。  
  
 在 WCF 服務或應用程式中，MSDTC 會提供基礎結構以便建立用戶端或服務中的交易協調。
