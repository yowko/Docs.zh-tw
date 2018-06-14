---
title: Windows 工作流程架構
ms.date: 03/30/2017
ms.assetid: 1d4c6495-d64a-46d0-896a-3a01fac90aa9
ms.openlocfilehash: c0e21e514e807196f3a09ae2a6eed6a9e7c55a18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513093"
---
# <a name="windows-workflow-architecture"></a>Windows 工作流程架構
Windows Workflow Foundation (WF) 會引發開發互動式長期執行應用程式的抽象層級。 工作的單元會封裝為活動。 活動會在環境中執行，該環境會為流程控制、例外狀況處理、錯誤傳播、狀態資料保存、從記憶體載入及卸載處理中的工作流程、追蹤，以及交易流程提供機能。  
  
## <a name="activity-architecture"></a>活動架構  
 活動會開發成衍生自 <xref:System.Activities.Activity>、<xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity> 或 <xref:System.Activities.NativeActivity> 的 CLR 型別，或者其傳回 <xref:System.Activities.Activity%601>、<xref:System.Activities.CodeActivity%601>、<xref:System.Activities.AsyncCodeActivity%601> 或 <xref:System.Activities.NativeActivity%601> 等值的變數。 開發衍生自 <xref:System.Activities.Activity> 的活動，可讓使用者組合預先存在的活動，以快速建立在工作流程環境中執行的工作單位。 另一方面，<xref:System.Activities.CodeActivity> 則可讓使用者能夠使用主要用於存取活動引數的 <xref:System.Activities.CodeActivityContext>，在 Managed 程式碼中撰寫執行邏輯。 <xref:System.Activities.AsyncCodeActivity> 類似 <xref:System.Activities.CodeActivity>，但可用來實作非同步工作。 開發衍生自 <xref:System.Activities.NativeActivity> 的活動，可讓使用者透過 <xref:System.Activities.NativeActivityContext> 來存取執行階段，以進行排定子系、建立書籤、叫用非同步工作、註冊交易等功能。  
  
 撰寫衍生自 <xref:System.Activities.Activity> 的活動是宣告式的，而且可在 XAML 中撰寫這些活動。 在下列範例中，會使用其他活動做為執行主體來建立稱為 `Prompt` 的活動。  
  
```xml  
<Activity x:Class='Prompt'  
  xmlns:x='http://schemas.microsoft.com/winfx/2006/xaml'  
    xmlns:z='http://schemas.microsoft.com/netfx/2008/xaml/schema'  
xmlns:my='clr-namespace:XAMLActivityDefinition;assembly=XAMLActivityDefinition'  
xmlns:s="clr-namespace:System;assembly=mscorlib"  
xmlns="http://schemas.microsoft.com/2009/workflow">  
<z:SchemaType.Members>  
    <z:SchemaType.SchemaProperty Name='Text' Type=' InArgument(s:String)' />  
  <z:SchemaType.SchemaProperty Name='Response' Type='OutArgument(s:String)' />  
</z:SchemaType.Members>  
  <Sequence>  
    <my:WriteLine Text='[Text]' />  
    <my:ReadLine BookmarkName='r1' Result='[Response]' />  
  </Sequence>  
</Activity>  
```  
  
## <a name="activity-context"></a>活動內容  
 <xref:System.Activities.ActivityContext> 是活動作者的工作流程執行階段介面，可提供存取執行階段各種豐富的功能。 下列範例會定義使用執行內容建立書籤的活動 (這種機制可讓活動在其執行中註冊持續點，以供傳遞資料至活動的主機繼續)。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
## <a name="activity-life-cycle"></a>活動開發週期  
 活動的執行個體會在 <xref:System.Activities.ActivityInstanceState.Executing> 狀態中啟動。 除非發生例外狀況，否則活動的執行個體會維持在這個狀態中，直到所有子活動皆執行完畢，而且其他所有暫止中的工作 (例如 <xref:System.Activities.Bookmark> 物件) 皆已完成，此時，該執行個體就會轉換成 <xref:System.Activities.ActivityInstanceState.Closed> 狀態。 活動執行個體的父系可以要求子系取消，如果子系可以取消，則會在 <xref:System.Activities.ActivityInstanceState.Canceled> 狀態下完成。 如果在執行期間擲回例外狀況，執行階段會將活動設為 <xref:System.Activities.ActivityInstanceState.Faulted> 狀態，並將例外狀況向上傳播至活動的父鏈結。 以下是活動的三種完成狀態：  
  
-   **關閉：** 活動已完成其工作並結束。  
  
-   **已取消：** 活動已正常放棄其工作並結束。 進入此狀態時，不會明確地復原工作。  
  
-   **發生錯誤：** 活動而發生錯誤，並已結束而不會完成其工作。  
  
 當活動被保存或卸載時，會繼續處於 <xref:System.Activities.ActivityInstanceState.Executing> 狀態。
