---
title: "使用自訂活動 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8f356419-681a-4175-ae93-878eee970249
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 使用自訂活動
衍生自 <xref:System.Activities.Activity> 或其子類別的活動，可以編寫成較大的工作流程，或直接建立成程式碼。本主題說明如何在以程式碼或設計工具建立的工作流程中，使用自訂活動。  
  
> [!NOTE]
>  自訂活動可以用在定義這些自訂活動的相同專案中，只要自訂活動和使用它的活動都經過編譯 \(也就是說，由建置程序產生的具現化類型載入\)。如果參考的活動是以動態方式載入 \(例如使用 ActivityXAMLServices\)，則參考的組件應放在不同的專案中，否則設計工具產生的 XAML 需要透過手動編輯來啟用此功能。  
  
#### 將自訂活動用於工作流程專案  
  
1.  將主專案的參考加入至包含自訂活動的活動程式庫專案。  
  
2.  建置方案。  
  
3.  若要在設計工具中使用自訂活動，請在工具箱中找到自訂活動，然後將該活動拖放至設計工具介面上。  
  
4.  若要在程式碼中使用自訂活動，請加入參考自訂活動專案的 Using 陳述式，並將活動的新執行個體傳遞至 <xref:System.Activities.WorkflowInvoker.Invoke%2A>。