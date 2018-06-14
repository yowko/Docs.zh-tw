---
title: 動態引數
ms.date: 03/30/2017
ms.assetid: 122ad479-d306-4602-a943-5aefe711329d
ms.openlocfilehash: 5c00b9678191e4e88e9e41380d6b10be39684b3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517974"
---
# <a name="dynamic-arguments"></a>動態引數
這個範例示範如何實作活動，由活動消費者 (而不是活動作者) 定義其引數。 其執行方式為覆寫執行階段建構活動中繼資料的方式。  
  
## <a name="sample-details"></a>範例詳細資料  
 在執行之前，執行階段會檢查活動型別的公用成員，以及自動將引數、變數、子活動和活動委派宣告為活動中繼資料的一部分，藉此建置活動的描述。 這樣做的目的在於確保工作流程的正確結構以及管理執行階段關聯性和存留期規則。 通常活動作者會透過在活動型別 (衍生自 <xref:System.Activities.Argument>) 上指定公用成員的方式定義活動的引數。 針對每一個衍生自 <xref:System.Activities.Argument> 的公用成員，執行階段會建立 <xref:System.Activities.RuntimeArgument>，並且將它繫結至該成員上使用者提供的引數集。 不過，在某些情況下，活動消費者會提供某種判斷引數集的組態。 活動作者會覆寫 <xref:System.Activities.Activity.CacheMetadata%2A> 以自訂建置活動中繼資料的方式，包括與活動相關聯的引數集。  
  
 這個範例示範如何為叫用方法的活動動態建置引數清單。 活動消費者會指定想要叫用的型別和方法名稱，以及要傳遞至該方法的引數集合。  
  
> [!NOTE]
>  這個範例的目的在於示範如何覆寫 <xref:System.Activities.CodeActivity.CacheMetadata%2A> 以及如何使用 <xref:System.Activities.RuntimeArgument>。 以下提供有關這個活動可以叫用之方法類型的一些注意事項。 例如，它無法搭配泛型或參數陣列運作。 .NET Framework 中隨附的 <xref:System.Activities.Statements.InvokeMethod> 活動會處理這些案例及其他情況。  
  
 `MethodInvoke` 活動會覆寫 <xref:System.Activities.CodeActivity.CacheMetadata%2A>，並且以建立 <xref:System.Activities.RuntimeArgument> 的方式開始處理方法叫用所產生的任何結果。 它會將這個 <xref:System.Activities.RuntimeArgument> 繫結至可公開設定的 <xref:System.Activities.OutArgument> (名為 `Result`)。 如果 `MethodInvoke.Result` 為 `null`，則執行階段會自動在其中填入 <xref:System.Activities.OutArgument>，該引數是以其型別的預設運算式設定。 這個行為表示活動作者永遠不必檢查引數屬性是否為 `null`。  
  
 接著，<xref:System.Activities.CodeActivity.CacheMetadata%2A> 覆寫會從使用者提供的 `MethodInfo` 和 `MethodName` 判斷用於引動的 `TargetType`。 `DetermineMethodInfo` 方法會採用傳遞至 <xref:System.Activities.CodeActivityMetadata> 覆寫的 <xref:System.Activities.CodeActivity.CacheMetadata%2A> 參數，如此任何組態錯誤都可以做為驗證錯誤回報。 藉由呼叫 `metadata.AddValidationError` 即可達到此目的。  
  
 一旦設定了 `MethodInfo`，範例就會逐一查看 `MethodInfo` 參數。 它會針對每一個參數建立 <xref:System.Activities.RuntimeArgument>，並且將它繫結至使用者提供的 `Parameters` 屬性集合中對應的引數。 最後，<xref:System.Activities.RuntimeArgument> 的集合會透過呼叫 `metadata.SetArgumentsCollection` 的方式與活動產生關聯。  
  
 請注意，引數可以使用 <xref:System.Activities.RuntimeArgument> (如同 `resultArgument` 的案例) 或是使用者提供的引數 (如同 `Parameters` 集合的案例) 進行解析。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 [DynamicArguments.sln] 檔案。  
  
2.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
3.  若要執行此方案，請按下 CTRL+F5。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\DynamicArguments`