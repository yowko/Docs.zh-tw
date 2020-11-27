---
title: 使用 WS-AtomicTransaction
ms.date: 03/30/2017
helpviewer_keywords:
- WS-AT protocol [WCF]
ms.assetid: 04a4c200-0af0-4c5d-a3d9-87cb7339e054
ms.openlocfilehash: 22b84dc49ab723953ce36402ac14221f410dda11
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281595"
---
# <a name="using-ws-atomictransaction"></a>使用 WS-AtomicTransaction

WS-AtomicTransaction (WS-AT) 是一種互通的異動通訊協定， 可讓您使用 Web 服務訊息來流動分散式交易，並且以互通的方式在異質性交易基礎結構之間進行協調。 WS-AT 使用兩階段的認可通訊協定，能夠在分散型應用程式、異動管理員和資源管理員之間促成不可部分完成的結果。  
  
 Windows Communication Foundation (WCF) 提供的「WS-AT 執行」（MSDTC）可提供內建于 Microsoft Distributed Transaction Coordinator (MSDTC) 交易管理員的通訊協定服務。 WCF 應用程式可以使用 WS-AT 將交易流動到其他應用程式，包括使用協力廠商技術建立的互通 Web 服務。  
  
 當在用戶端應用程式和伺服器應用程式之間流動異動時，伺服器在用戶端所選取之端點上公開的繫結程序會判斷要使用的異動通訊協定。 某些 WCF 系統提供的系結預設會將 `OleTransactions` 通訊協定指定為交易傳播格式，而其他系結則預設為指定 ws-at。 您也可以使用程式設計的方式來修改在特定繫結程序中選擇的異動通訊協定。  
  
 選擇的通訊協定會影響：  
  
- 用來將交易從用戶端流動至伺服器的訊息標頭格式。  
  
- 用來在用戶端異動管理員和伺服器異動之間執行兩階段認可通訊協定的網路通訊協定，能夠解析異動的結果。  
  
 如果伺服器和用戶端是使用 WCF 撰寫的，您就不需要使用 WS-AT。 您可以改為使用已啟用 `NetTcpBinding` 屬性的 `TransactionFlow` 預設值，這樣就會使用 `OleTransactions` 通訊協定來替代。 如需詳細資訊，請參閱 [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) \(英文\)。 否則，如果您要流動異動至使用協力廠商技術建置的 Web 服務，就必須使用 WS-AT。  
  
## <a name="see-also"></a>另請參閱

- [設定 WS-Atomic 交易支援](configuring-ws-atomic-transaction-support.md)
