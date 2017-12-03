---
title: "監控服務作業失敗"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59472ba3-8ebf-4479-bd7b-f440d5e636cb
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c6030b1ad1dc3953137d3b068be1bceb99975a5f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="monitoring-service-operation-failures"></a>監控服務作業失敗
如果您為應用程式啟用分析追蹤，可以在事件檢視器中輕鬆監視服務失敗。  本主題示範如何判斷服務作業失敗的時間，以及如何判斷造成失敗的原因。  
  
### <a name="determining-service-operation-failure-information"></a>判斷服務作業失敗資訊  
  
1.  開啟事件檢視器，依序按一下**啟動**，**執行**，並輸入`eventvwr.exe`。  
  
2.  如果您尚未啟用分析追蹤，展開**Applications and Services Logs**， **Microsoft**， **Windows**，**應用程式伺服器-應用程式**. 選取**檢視**，**顯示分析與偵錯記錄檔**。 以滑鼠右鍵按一下**分析**選取**啟用記錄**。 讓 [事件檢視器] 保持開啟狀態，如此在服務作業失敗之後就能檢視追蹤。  
  
3.  接下來，開啟 建立範例[入門教學課程](../../../../../docs/framework/wcf/getting-started-tutorial.md)中[!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)]請注意，您必須執行[!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)]身為系統管理員，以便可以建立服務。 如果您有[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]範例的安裝，您可以開啟[入門](../../../../../docs/framework/wcf/samples/getting-started-sample.md)，其中包含已完成本教學課程中建立的專案。  
  
4.  在伺服器專案的 Program.cs 檔案中，將下列程式碼行加入到 `Divide` 類別中，`CalculatorService` 方法的開頭：  
  
    ```  
    if (n2 == 0) throw new DivideByZeroException();  
    ```  
  
5.  在用戶端專案的 Program.cs 檔案中，將指派給 value2 的值變更為零：  
  
    ```  
    //Call the Divide service operation  
    value1 = 22.00D;  
    value2 = 0.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0}, {1}) = {2}", value1, value2, result);  
    ```  
  
6.  執行伺服器應用程式，但不偵錯按**Ctrl + F5**。  
  
7.  開啟 Visual Studio 命令提示字元。  巡覽至用戶端目錄，然後從命令列執行用戶端。  
  
8.  在 [事件檢視器] 中，停用並重新整理分析記錄檔並依照 [事件識別碼] 排序事件。  尋找事件識別碼的事件[219-ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md)，用來描述服務失敗。  
  
    ```Output  
    There was an unhandled exception of type 'System.DivideByZeroException' during message processing.  Full Exception ToString: System.DivideByZeroException: Attempted to divide by zero.  
    ```  
  
    > [!NOTE]
    >  事件傳送到事件檢視器時，會進行緩衝處理；失敗事件可能不會立即出現。
