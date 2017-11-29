---
title: "異動模型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 182a394b7698c7a1a59a4db50ee81caed4d2e75f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="transaction-models"></a>異動模型
本主題描述異動程式設計模型與 Microsoft 提供的基礎結構元件之間的關係。  
  
 在 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中使用交易時，了解您並非在不同的交易式模型之間做選擇，而是在整合與一致的模型之不同層中作業相當重要。  
  
 下列幾節詳細描述三個主要的交易元件。  
  
## <a name="windows-communication-foundation-transactions"></a>Windows Communication Foundation 交易  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的交易支援可讓您撰選交易式服務。 此外，透過它對 WS-AtomicTransaction (WS-AT) 通訊協定的支援，應用程式可以使交易流向使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 或協力廠商技術建立的 Web 服務。  
  
 在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務或應用程式中，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 交易功能提供屬性與組態，用於以宣告方式指定應建立、流動和同步化交易的方法與時間。  
  
## <a name="systemtransactions-transactions"></a>System.Transactions 交易  
 <xref:System.Transactions> 命名空間會提供根據 <xref:System.Transactions.Transaction> 類別的明確程式設計模型，以及使用 <xref:System.Transactions.TransactionScope> 類別的隱含程式設計模型，而其中交易會由基礎結構自動管理。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]如何建立交易式應用程式使用這兩個模型，請參閱[撰寫異動應用程式](http://go.microsoft.com/fwlink/?LinkId=94947)。  
  
 在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務或應用程式中，<xref:System.Transactions> 提供用於在用戶端應用程式中建立交易，以及在服務中需要時與交易明確互動的程式設計模型。  
  
## <a name="msdtc-transactions"></a>MSDTC 交易  
 Microsoft Distributed Transaction Coordinator (MSDTC) 是對分散式異動提供支援的異動管理員。  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][DTC 程式設計人員參考](http://go.microsoft.com/fwlink/?LinkId=94948)。  
  
 在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務或應用程式中，MSDTC 為在用戶端或服務中建立的交易協調提供基礎結構。
