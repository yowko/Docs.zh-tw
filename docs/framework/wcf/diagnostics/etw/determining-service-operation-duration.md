---
title: "判斷服務作業持續時間"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2c96aa6752feca637f89ed309d1a5c87cea4a3a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="determining-service-operation-duration"></a>判斷服務作業持續時間
如果已啟用 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 應用程式中的分析追蹤，則透過檢查事件記錄檔就能輕鬆判斷出服務作業的執行持續時間。  本主題示範如何判斷服務作業完成所需的時間。  
  
### <a name="determining-service-operation-execution-duration"></a>判斷服務作業執行持續時間  
  
1.  開啟事件檢視器，依序按一下**啟動**，**執行**，並輸入`eventvwr.exe`。  
  
2.  如果您尚未啟用分析追蹤，展開**Applications and Services Logs**， **Microsoft**， **Windows**，**應用程式伺服器-應用程式**. 選取**檢視**，**顯示分析與偵錯記錄檔**。 以滑鼠右鍵按一下**分析**選取**啟用記錄**。 讓 [事件檢視器] 保持開啟狀態，如此在服務作業執行之後就能檢視追蹤。  
  
3.  接著開啟 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 應用程式，其中包括與該服務互動的服務專案和用戶端專案。  您可以建立這類應用程式遵循[入門教學課程](../../../../../docs/framework/wcf/getting-started-tutorial.md)。  如果您有[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]範例的安裝，您可以開啟[入門](../../../../../docs/framework/wcf/samples/getting-started-sample.md)，其中包含已完成本教學課程中建立的專案。  
  
4.  執行伺服器應用程式按**F5**。 執行用戶端應用程式，以滑鼠右鍵按一下**用戶端**專案，並選取**偵錯**，**開始新執行個體**。  
  
5.  在 [事件檢視器] 中，重新整理分析記錄檔並依照 [事件 ID] 排序事件。  尋找事件識別碼[214-operationcompleted，接續](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md)。  這些事件將顯示已完成的作業，以及作業的持續時間。  下列事件會顯示 Add 作業的持續時間。  
  
    ```Output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
