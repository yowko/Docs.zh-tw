---
title: "等候輸入活動"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d58c344e-9ee8-4ce2-b199-75b3fe45237f
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 145a71ff7d1ca07112ab91aa46ec4efb10429713
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="wait-for-input-activity"></a>等候輸入活動
此範例示範如何在工作流程中建立具名書籤。 [!INCLUDE[wf](../../../../includes/wf-md.md)] 不提供用於以宣告式建立書籤的活動。 因此，當您想要在工作流程中建立書籤時，您必須撰寫可建立書籤的自訂活動。 此範例中定義的 `WaitForInput` 活動會提供這個功能，所以使用者可在工作流程中以宣告方式建立書籤。  
  
## <a name="projects-in-this-sample"></a>這個範例中的專案  
  
|**專案名稱**|**說明**|**主要檔案**|  
|-|-|-|  
|WaitForInput|包含 `WaitForInput` 活動和其設計工具|WaitForInput.cs<br /><br /> `WaitForInput` 活動定義。|  
|||WaitForInputDesigner.xaml<br /><br /> `WaitForInput` 活動的自訂設計工具。|  
|||TypeToFirstGenericArgumentConverter.cs<br /><br /> WPF 型別轉換子，用來在設計工具內更新活動的泛型型別。|  
|WaitForInputTestClient|範例用戶端應用程式，可透過工作流程設計工具來設定及執行使用幾個 WaitForInput 活動的工作流程。|Sequence1.xaml<br /><br /> 使用 `WaitForInput` 活動的循序工作流程。|  
|||Program.cs<br /><br /> 執行 Sequence1.xaml 中定義的工作流程執行個體。|  
  
## <a name="waitforinput-activity"></a>WaitForInput 活動  
 `WaitForInput` 活動會在工作流程中建立具名的書籤。 此書籤會等候信號，並接收其設定之型別的資料。 當書籤繼續之後，傳入工作流程的資料可透過 `Result` 屬性來使用。  
  
 `WaitForInput` 活動衍生自 <xref:System.Activities.NativeActivity> 類別，因為它必須建立只能透過 <xref:System.Activities.NativeActivityContext> 類別存取的書籤。  
  
 此活動有三個套用的屬性，可繫結設計工具、加入可以更新的泛型引數功能，以及將預設泛型型別設定為字串。 此活動也有列於下表的引數。  
  
|**Name**|**Type**|**說明**|  
|-|-|-|  
|TResult|泛型引數 (TResult)|書籤的型別。 這是當書籤繼續時要傳遞給書籤的資料型別。|  
|BookmarkName|InArgument\<字串 >|書籤的名稱。|  
|結果|InArgument\<TResult >|當書籤繼續時傳遞給活動的資料。|  
  
## <a name="waitforinput-activity-designer"></a>WaitForInput 活動設計工具  
 `WaitForInput` 活動設計工具會在 WaitForInputDesigner.xaml 檔案中實作。 `WaitForInput` 活動和它的設計工具會包含在相同的組件中。 下圖顯示工具箱中某個分類的 `WaitForInput` 活動，該分類的名稱與組件相同。  
  
 ![WaitForInput 工具箱螢幕擷取畫面](../../../../docs/framework/windows-workflow-foundation/samples/media/waitforinputtoolbox.jpg "WaitForInputToolbox")  
  
 下圖顯示 `WaitForInput` 設計工具。 因為 `WaitForInput` 活動非常基本，所以設計工具允許直接在設計工具介面中設定它的所有引數。  
  
 ![WaitForInput 活動設計工具](../../../../docs/framework/windows-workflow-foundation/samples/media/waitforinputdesigner.jpg "WaitForInputDesigner")  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 WaitForInput.sln 檔。  
  
2.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
3.  若要啟動範例而不執行偵錯，請按 CTRL+F5。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\WaitForInput`