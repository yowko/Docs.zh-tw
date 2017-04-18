---
title: "監控服務作業失敗 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59472ba3-8ebf-4479-bd7b-f440d5e636cb
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 監控服務作業失敗
如果您為應用程式啟用分析追蹤，可以在事件檢視器中輕鬆監視服務失敗。本主題示範如何判斷服務作業失敗的時間，以及如何判斷造成失敗的原因。  
  
### 判斷服務作業失敗資訊  
  
1.  依序按一下 \[**開始**\]、\[**執行**\]，並輸入 `eventvwr.exe`，開啟 \[事件檢視器\]。  
  
2.  如果您尚未啟用分析追蹤，請依序展開 \[**應用程式與服務記錄檔**\]、\[**Microsoft**\]、\[**Windows**\]、\[**應用程式伺服器\-應用程式**\]。依序選取 \[**檢視**\]、\[**顯示分析與偵錯記錄檔**\]。以滑鼠右鍵按一下 \[**分析**\]，並選取 \[**啟用記錄**\]。讓 \[事件檢視器\] 保持開啟狀態，如此在服務作業失敗之後就能檢視追蹤。  
  
3.  接下來，開啟 [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] 之[快速入門教學課程](../../../../../docs/framework/wcf/getting-started-tutorial.md) 中建立的範例。請注意，您必須以系統管理員身分執行 [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)]，如此便可以建立服務。如果您已安裝 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 範例，則可以開啟[使用者入門](../../../../../docs/framework/wcf/samples/getting-started-sample.md)，其中包含教學課程中建立的已完成專案。  
  
4.  在伺服器專案的 Program.cs 檔案中，將下列程式碼行加入到 `CalculatorService` 類別中，`Divide` 方法的開頭：  
  
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
  
6.  按 **Ctrl\+F5** 鍵執行伺服器應用程式，而不偵錯。  
  
7.  開啟 Visual Studio 命令提示字元。巡覽至用戶端目錄，然後從命令列執行用戶端。  
  
8.  在 \[事件檢視器\] 中，停用並重新整理分析記錄檔並依照 \[事件識別碼\] 排序事件。尋找事件識別碼為 [219 \- ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md) 的事件，其中描述服務失敗。  
  
    ```Output  
    訊息處理期間發生了未處理的例外狀況 (型別為 'System.DivideByZeroException')。完整例外狀況 ToString：System.DivideByZeroException：嘗試以零除。  
    ```  
  
    > [!NOTE]
    >  事件傳送到事件檢視器時，會進行緩衝處理；失敗事件可能不會立即出現。