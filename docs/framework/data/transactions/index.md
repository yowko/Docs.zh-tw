---
title: "交易處理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: effdc8e6-accf-41eb-98a5-431603ba218b
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6c66e982715d0f7f97e7a4faa92c2de57f3b1471
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="transaction-processing"></a>交易處理
當您從線上書店購買一本書時，您以金錢來交易書籍 (以信用方式來支付)。 如果您的信用良好，接下來的一系列作業流程會確保您收到這本書，同時確保書店收到您支付的錢。 但是，如果在一系列交易過程中有任何一個環節出錯，整個交易就會失敗。 您將拿不到書，而書店也無法收到您支付的錢。  
  
 用於平衡並預測這項交易所有結果的技術，我們稱為交易處理。 交易可確保資料導向的資源不會一直更新，除非交易單元中的所有作業都已全部完成。 您可以將一系列相關作業整合到可能全部完成或全部失敗的單元中，藉此簡化錯誤復原程序並讓應用程式變得更可靠。  
  
 交易處理系統包含了裝載交易導向應用程式的電腦硬體與軟體用來執行業務運作所需的例行性交易。 常見範例包括用來管理銷售訂單輸入、機票預訂、薪資單、員工記錄、製造與出貨等項目的系統。  
  
 本節將提供有關交易處理的一般資訊，以及如何使用 Microsoft .NET Framework 來撰寫交易式應用程式與資源管理員的特定資訊。  
  
## <a name="in-this-section"></a>本節內容  
 [交易基礎概念](../../../../docs/framework/data/transactions/transaction-fundamentals.md)  
 簡介基礎交易處理名詞與概念。  
  
 [System.Transactions 所提供的功能](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md)  
 討論如何使用 System.Transactions 中的各項功能來撰寫自己的交易式應用程式。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Transactions>  
 提供可讓您的程式碼參與交易的各種類別。 這些類別支援了與多位分散的參與者、多階段告知和永久性登記進行的交易。
