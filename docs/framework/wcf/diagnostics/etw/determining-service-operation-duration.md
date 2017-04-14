---
title: "判斷服務作業持續時間 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 判斷服務作業持續時間
如果已啟用 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 應用程式中的分析追蹤，則透過檢查事件記錄檔就能輕鬆判斷出服務作業的執行持續時間。  本主題示範如何判斷服務作業完成所需的時間。  
  
### 判斷服務作業執行持續時間  
  
1.  依序按一下 \[**開始**\]、\[**執行**\]，並輸入 `eventvwr.exe`，開啟 \[事件檢視器\]。  
  
2.  如果您尚未啟用分析追蹤，請依序展開 \[**應用程式與服務記錄檔**\]、\[**Microsoft**\]、\[**Windows**\]、\[**應用程式伺服器\-應用程式**\]。  依序選取 \[**檢視**\]、\[**顯示分析與偵錯記錄檔**\]。  以滑鼠右鍵按一下 \[**分析**\]，然後選取 \[**啟用記錄**\]。  讓 \[事件檢視器\] 保持開啟狀態，如此在服務作業執行之後就能檢視追蹤。  
  
3.  接著開啟 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 應用程式，其中包括與該服務互動的服務專案和用戶端專案。  您可以依照[快速入門教學課程](../../../../../docs/framework/wcf/getting-started-tutorial.md)建立這類應用程式。  如果您已安裝 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 範例，則可以開啟[使用者入門](../../../../../docs/framework/wcf/samples/getting-started-sample.md)，其中包含教學課程中建立的已完成專案。  
  
4.  按 **F5** 鍵執行伺服器應用程式。  以滑鼠右鍵按一下 \[**用戶端**\] 專案，然後依序選取 \[**偵錯**\] 和 \[**開始新執行個體**\]，藉此執行用戶端應用程式。  
  
5.  在 \[事件檢視器\] 中，重新整理分析記錄檔並依照 \[事件 ID\] 排序事件。  尋找 \[事件 ID\] 為 [214 \- OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md) 的事件。  這些事件將顯示已完成的作業，以及作業的持續時間。  下列事件會顯示 Add 作業的持續時間。  
  
    ```Output  
  
    OperationInvoker 已完成對 'Add' 方法的呼叫。  方法呼叫持續時間為 '3' 毫秒。    
    ```