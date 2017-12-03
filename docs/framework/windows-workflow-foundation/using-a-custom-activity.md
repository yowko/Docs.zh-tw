---
title: "使用自訂活動"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f356419-681a-4175-ae93-878eee970249
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cea0e819c79550b27a71957f6d8c2c9badfef7c0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="using-a-custom-activity"></a>使用自訂活動
衍生自 <xref:System.Activities.Activity> 或其子類別的活動，可以編寫成較大的工作流程，或直接建立成程式碼。 本主題說明如何在以程式碼或設計工具建立的工作流程中，使用自訂活動。  
  
> [!NOTE]
>  可以在相同的專案中，它們會定義，使用自訂活動，只要自訂活動和活動，使用它所編譯的 （也就是由建置流程所產生具現化類型載入） 載入參考的活動以動態方式 （例如使用 ActivityXAMLServices），然後參考的組件應放在不同的專案，或設計工具產生的 XAML 需要透過手動編輯來啟用此功能。  
  
#### <a name="using-a-custom-activity-to-a-workflow-project"></a>將自訂活動用於工作流程專案  
  
1.  將主專案的參考加入至包含自訂活動的活動程式庫專案。  
  
2.  建置方案。  
  
3.  若要在設計工具中使用自訂活動，請在工具箱中找到自訂活動，然後將該活動拖放至設計工具介面上。  
  
4.  若要在程式碼中使用自訂活動，請加入參考自訂活動專案的 Using 陳述式，並將活動的新執行個體傳遞至 <xref:System.Activities.WorkflowInvoker.Invoke%2A>。
