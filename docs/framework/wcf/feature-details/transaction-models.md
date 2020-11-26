---
title: 異動模型
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: ce7eb74a3e06df8db2e6d8261faca16650e4e4f1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242262"
---
# <a name="transaction-models"></a>異動模型

本主題描述異動程式設計模型與 Microsoft 提供的基礎結構元件之間的關係。  
  
 使用 Windows Communication Foundation (WCF) 中的交易時，請務必瞭解，您不會在不同的交易式模型之間進行選取，而是在整合式和一致模型的不同層級上操作。  
  
 下列幾節詳細描述三個主要的交易元件。  
  
## <a name="windows-communication-foundation-transactions"></a>Windows Communication Foundation 異動  

 WCF 中的交易支援可讓您撰寫交易式服務。 此外，WS-AtomicTransaction (WS-AT) 通訊協定的支援，應用程式可以將交易流動至使用 WCF 或協力廠商技術建立的 Web 服務。  
  
 在 WCF 服務或應用程式中，WCF 交易功能會提供屬性和設定，以宣告方式指定基礎結構應建立、流動和同步處理交易的方式和時間。  
  
## <a name="systemtransactions-transactions"></a>System.Transactions 異動  

 <xref:System.Transactions> 命名空間會提供根據 <xref:System.Transactions.Transaction> 類別的明確程式設計模型，以及使用 <xref:System.Transactions.TransactionScope> 類別的隱含程式設計模型，而其中異動會由基礎結構自動管理。  
  
 如需有關如何使用這兩個模型來建立交易式應用程式的詳細資訊，請參閱 [撰寫交易式應用程式](https://go.microsoft.com/fwlink/?LinkId=94947)。  
  
 在 WCF 服務或應用程式中， <xref:System.Transactions> 提供程式設計模型來建立用戶端應用程式中的交易，並在必要時，于服務內明確地與交易互動。  
  
## <a name="msdtc-transactions"></a>MSDTC 交易  

 Microsoft Distributed Transaction Coordinator (MSDTC) 是對分散式交易提供支援的交易管理員。  
  
 如需詳細資訊，請參閱 DTC 程式設計 [人員參考](/previous-versions/windows/desktop/ms686108(v=vs.85))。  
  
 在 WCF 服務或應用程式中，MSDTC 會提供基礎結構，以協調在用戶端或服務中建立的交易。
