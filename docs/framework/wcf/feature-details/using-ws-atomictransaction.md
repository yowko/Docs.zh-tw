---
title: "使用 WS-AtomicTransaction"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS-AT protocol [WCF]
ms.assetid: 04a4c200-0af0-4c5d-a3d9-87cb7339e054
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7046add86f1255b222640912be02c08b98cb9cae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="using-ws-atomictransaction"></a>使用 WS-AtomicTransaction
WS-AtomicTransaction (WS-AT) 是一種互通的異動通訊協定， 可讓您使用 Web 服務訊息來流動分散式交易，並且以互通的方式在異質性交易基礎結構之間進行協調。 WS-AT 使用兩階段的認可通訊協定，能夠在分散型應用程式、交易管理員和資源管理員之間促成不可部分完成的結果。  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 提供的 WS-AT 實作包括內建於 Microsoft Distributed Transaction Coordinator (MSDTC) 交易管理員的通訊協定服務。 使用 WS-AT，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式就可以將交易流動到其他應用程式，包括使用協力廠商技術建置的可互通 Web 服務。  
  
 當在用戶端應用程式和伺服器應用程式之間流動交易時，伺服器在用戶端所選取之端點上公開的繫結會判斷要使用的交易通訊協定。 某些 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 系統提供的繫結是預設為將 `OleTransactions` 通訊協定指定為交易傳播格式，而其他的繫結則是預設為指定 WS-AT。 您也可以使用程式設計的方式來修改在特定繫結中選擇的交易通訊協定。  
  
 選擇的通訊協定會影響：  
  
-   用來將交易從用戶端流動至伺服器的訊息標頭格式。  
  
-   用來在用戶端交易管理員和伺服器交易之間執行兩階段認可通訊協定的網路通訊協定，能夠解析交易的結果。  
  
 如果伺服器和用戶端使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 寫入，您就不需要使用 WS-AT。 您可以改為使用已啟用 `NetTcpBinding` 屬性的 `TransactionFlow` 預設值，這樣就會使用 `OleTransactions` 通訊協定來替代。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)。 否則，如果您要流動異動至使用協力廠商技術建置的 Web 服務，就必須使用 WS-AT。  
  
## <a name="see-also"></a>另請參閱  
 [設定 Ws-atomic 交易支援](../../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
