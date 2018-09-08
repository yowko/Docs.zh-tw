---
title: 針對活動
ms.date: 03/30/2017
ms.assetid: 2ea751b4-36f0-48aa-a115-70a2ab89f6d8
ms.openlocfilehash: 7a7023abb9057ab4b25552fbf9a81cd2ae2b4e88
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44206259"
---
# <a name="for-activity"></a>針對活動
For 範例示範如何建置繼承自 <xref:System.Activities.NativeActivity> 的自訂活動，以及在工作流程中使用它來執行真實的範例。 本範例中包含的自訂活動作用就像 C# `for` 陳述式。 T  
  
 `For` 自訂活動擁有名為 `InitAction`、`IterationAction`、`Condition` 和 `Body` 的屬性，這些屬性分別對應至標準 C# `For` 陳述式中的初始化陳述式、反覆性陳述式、持續條件以及主體陳述式。  
  
 下表描述範例中的重要檔案。  
  
|檔案|描述|  
|----------|-----------------|  
|For.cs|`For` 自訂活動的類別定義，它會擴充 <xref:System.Activities.NativeActivity> 類別以提供 C# `For` 陳述式的功能。|  
|Program.cs|用戶端應用程式，它會使用自訂 `For` 活動執行集合上基本的反覆性工作。|  
  
> [!NOTE]
>  使用 `For` 自訂活動時，務必確定已設定 `Condition` 屬性，否則可能發生無限迴圈。  
  
## <a name="demonstrates"></a>示範  
 建立繼承自 <xref:System.Activities.NativeActivity> 的自訂活動。  
  
## <a name="discussion"></a>討論  
 下表說明本範例中所包含活動的屬性。  
  
 InitAction  
 初始化陳述式  
  
 IterationAction  
 反覆性陳述式  
  
 條件  
 持續陳述式  
  
 本文  
 主體陳述式  
  
 活動會繼承自 <xref:System.Activities.NativeActivity> 以便存取執行階段功能，例如排程執行其他活動、使用 `ScheduleActivity` 的其中一個 <xref:System.Activities.NativeActivityContext> 方法。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 [For.sln] 方案檔案。  
  
2.  按 CTRL+SHIFT+B 以建置此方案。  
  
3.  按 F5 鍵執行方案。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\For`