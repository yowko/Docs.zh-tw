---
title: 使用自訂活動
ms.date: 03/30/2017
ms.assetid: 8f356419-681a-4175-ae93-878eee970249
ms.openlocfilehash: 6ca67ef7a8c4330d0182e960fc3fdcce656976a4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962228"
---
# <a name="using-a-custom-activity"></a>使用自訂活動
衍生自 <xref:System.Activities.Activity> 或其子類別的活動，可以編寫成較大的工作流程，或直接建立成程式碼。 本主題說明如何在以程式碼或設計工具建立的工作流程中，使用自訂活動。  
  
> [!NOTE]
> 自訂活動可以在其定義所在的相同專案中使用, 只要自訂活動和使用它的活動經過編譯 (也就是由組建進程所產生的具現化型別載入) (如果已載入參考活動的話)動態 (例如使用 ActivityXAMLServices), 則會將參考的元件放在不同的專案中, 或設計工具產生的 XAML 必須手動編輯才能啟用此功能。  
  
#### <a name="using-a-custom-activity-to-a-workflow-project"></a>將自訂活動用於工作流程專案  
  
1. 將主專案的參考加入至包含自訂活動的活動程式庫專案。  
  
2. 建置方案。  
  
3. 若要在設計工具中使用自訂活動，請在工具箱中找到自訂活動，然後將該活動拖放至設計工具介面上。  
  
4. 若要在程式碼中使用自訂活動，請加入參考自訂活動專案的 Using 陳述式，並將活動的新執行個體傳遞至 <xref:System.Activities.WorkflowInvoker.Invoke%2A>。
