---
title: 使用 Native 活動的自訂複合
ms.date: 03/30/2017
ms.assetid: ef9e739c-8a8a-4d11-9e25-cb42c62e3c76
ms.openlocfilehash: 57c724ad55c3aa2960e9a2d11fcd8419a94a0c72
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715179"
---
# <a name="custom-composite-using-native-activity"></a>使用 Native 活動的自訂複合
這個範例示範如何撰寫 <xref:System.Activities.NativeActivity>，它會排程其他 <xref:System.Activities.Activity> 物件來控制工作流程的執行流程。 此範例使用兩個常用的控制流程 (Sequence 和 While)，以示範如何進行這項處理。

## <a name="sample-details"></a>範例詳細資料
 從 `MySequence` 開始，要注意的第一件事就是它會衍生自 <xref:System.Activities.NativeActivity>。 <xref:System.Activities.NativeActivity> 是 <xref:System.Activities.Activity> 物件，可透過傳遞給 <xref:System.Activities.NativeActivityContext> 方法的 `Execute` 來公開工作流程執行階段的完整範圍。

 `MySequence` 會公開 <xref:System.Activities.Activity> 物件的公用集合，這些物件是由工作流程作者所填入。 在執行工作流程之前，工作流程執行階段會在工作流程中的每一個活動上呼叫 <xref:System.Activities.Activity.CacheMetadata%2A> 方法。 在這個程序期間，執行階段會建立父-子關係來設定資料範圍及進行存留期管理。 <xref:System.Activities.Activity.CacheMetadata%2A> 方法的預設執行會使用 `MySequence` 活動的 <xref:System.ComponentModel.TypeDescriptor> 實例類別，將類型 <xref:System.Activities.Activity> 或 <xref:System.Collections.IEnumerable>\<<xref:System.Activities.Activity>> `MySequence` 的任何公用屬性加入活動的子系。

 每當活動公開子活動的公開集合時，這些子活動很可能會共用狀態。 最佳作法是讓父活動 (此案例中的 `MySequence`) 也公開變數集合，子活動就可以透過這些變數完成這項作業。 就像子活動一樣，<xref:System.Activities.Activity.CacheMetadata%2A> 方法會將類型 <xref:System.Activities.Variable> 或 <xref:System.Collections.IEnumerable>\<<xref:System.Activities.Variable>> 的公用屬性加入與 `MySequence` 活動相關聯的變數。

 除了公用變數 (由 `MySequence` 的子系所操作) 以外，`MySequence` 在執行其子系的過程中也必須追蹤其所在位置。 它會使用私用變數 `currentIndex` 完成這項處理。 這個變數會登錄為 `MySequence` 環境的一部分，其方式是在 <xref:System.Activities.NativeActivityMetadata.AddImplementationVariable%2A> 活動的 `MySequence` 方法內加入 <xref:System.Activities.Activity.CacheMetadata%2A> 方法的呼叫。 加入至 <xref:System.Activities.Activity> `MySequence` 集合的 `Activities` 物件不能存取以這個方式加入的變數。

 當執行階段執行 `MySequence` 時，執行階段會呼叫它的 <xref:System.Activities.NativeActivity.Execute%2A> 方法，傳入 <xref:System.Activities.NativeActivityContext>。 <xref:System.Activities.NativeActivityContext> 是回到執行階段的活動 Proxy，可針對引數和變數來取值，以及排程其他 <xref:System.Activities.Activity> 物件或 `ActivityDelegates`。 `MySequence` 會使用 `InternalExecute` 方法，將排程第一個子系和所有後續子系的邏輯封裝在單一方法中。 它一開始會先針對 `currentIndex` 來取值。 如果它等於 `Activities` 集合中的計數，則會完成序列、活動會傳回而不排程任何工作，然後執行階段會將它移到 <xref:System.Activities.ActivityInstanceState.Closed> 狀態。 如果 `currentIndex` 小於活動計數，則下一個子系會從 `Activities` 集合取得，而 `MySequence` 會呼叫 <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>，傳入要排程的子系，以及指向 <xref:System.Activities.CompletionCallback> 方法的 `InternalExecute`。 最後，`currentIndex` 會遞增，而控制權會回到執行階段。 只要 `MySequence` 執行個體已排程子物件 <xref:System.Activities.Activity>，執行階段就會將它視為「正在執行」狀態。

 當子活動完成時，就會執行 <xref:System.Activities.CompletionCallback>。 迴圈會從最上層繼續執行。 就像 `Execute` 一樣，<xref:System.Activities.CompletionCallback> 會採用 <xref:System.Activities.NativeActivityContext>，讓實作者可存取執行階段。

 `MyWhile` 與 `MySequence` 不同之處在于，它會重複排程單一 <xref:System.Activities.Activity> 物件，而且它會使用名為 < 的 <xref:System.Activities.Activity%601>\> bool `Condition` 來判斷是否應該進行此排程。 就像 `MySequence` 一樣，`MyWhile` 會使用 `InternalExecute` 方法來集中處理它的排程邏輯。 它會使用名為 <xref:System.Activities.CompletionCallback%601>的 \<> bool `OnEvaluationCompleted`，排定 `Condition`<xref:System.Activities.Activity>< bool\>。 當完成 `Condition` 的執行時，可在名為 <xref:System.Activities.CompletionCallback> 的強型別參數中透過這個 `result` 來使用其結果。 如果為 `true`，則 `MyWhile` 會呼叫 <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>，傳入 `Body`<xref:System.Activities.Activity> 物件和 `InternalExecute` 當做 <xref:System.Activities.CompletionCallback>。 當完成 `Body` 的執行時，`Condition` 會再次於 `InternalExecute` 中排程，重新開始迴圈。 當 `Condition` 傳回 `false` 時，`MyWhile` 的執行個體會將控制權送回執行階段而不排程 `Body`，而執行階段會將它移到 <xref:System.Activities.ActivityInstanceState.Closed> 狀態。

#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例

1. 開啟 Visual Studio 2010 中的複合 .sln 範例解決方案。

2. 建置並執行方案。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> 如果此目錄不存在，請移至[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）範例](https://www.microsoft.com/download/details.aspx?id=21459)，以下載所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\CustomCompositeNativeActivity`
