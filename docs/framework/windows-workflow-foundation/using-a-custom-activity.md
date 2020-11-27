---
title: 使用自訂活動
ms.date: 03/30/2017
ms.assetid: 8f356419-681a-4175-ae93-878eee970249
ms.openlocfilehash: 43addd4e69b7f7ac3ac5cd8e5bcd41397d8f0a67
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293321"
---
# <a name="using-a-custom-activity"></a>使用自訂活動

衍生自 <xref:System.Activities.Activity> 或其子類別的活動，可以編寫成較大的工作流程，或直接建立成程式碼。 本主題說明如何在以程式碼或設計工具建立的工作流程中，使用自訂活動。  
  
> [!NOTE]
> 自訂活動可以在其定義所在的相同專案中使用。只要自訂活動和使用它的活動都經過編譯 (也就是由組建程式所產生的具現化型別載入) 如果參考活動是以動態方式載入 (例如使用 ActivityXAMLServices) ，則參考的元件應該放在不同的專案中，否則就必須手動編輯設計工具所產生的 XAML 來啟用此功能。  
  
#### <a name="using-a-custom-activity-to-a-workflow-project"></a>將自訂活動用於工作流程專案  
  
1. 將主專案的參考加入至包含自訂活動的活動程式庫專案。  
  
2. 建置方案。  
  
3. 若要在設計工具中使用自訂活動，請在工具箱中找到自訂活動，然後將該活動拖放至設計工具介面上。  
  
4. 若要在程式碼中使用自訂活動，請加入參考自訂活動專案的 Using 陳述式，並將活動的新執行個體傳遞至 <xref:System.Activities.WorkflowInvoker.Invoke%2A>。
