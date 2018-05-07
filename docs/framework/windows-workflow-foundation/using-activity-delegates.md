---
title: 使用活動委派
ms.date: 03/30/2017
ms.assetid: e33cf876-8979-440b-9b23-4a12d1139960
ms.openlocfilehash: 96a412a066342fb9c459e1388c5b58847ebac390
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="using-activity-delegates"></a>使用活動委派
活動委派可讓活動作者使用特定的簽章以公開回呼，活動使用者可以此為依據來提供活動處理常式。 活動委派有兩種型別可用：<xref:System.Activities.ActivityAction%601>，用來定義沒有傳回值的活動委派，以及 <xref:System.Activities.ActivityFunc%601>，用來定義有傳回值的活動委派。  
  
 在限制子活動必須擁有簽章的案例中，活動委派非常實用。 例如，<xref:System.Activities.Statements.While> 活動可包含任何沒有條件約束的子活動型別，但 <xref:System.Activities.Statements.ForEach%601> 活動的主體是 <xref:System.Activities.ActivityAction%601>，且最終由 <xref:System.Activities.Statements.ForEach%601> 執行的子活動，必須具有與 <xref:System.Activities.InArgument%601> 列舉之集合成員相同型別的 <xref:System.Activities.Statements.ForEach%601>。  
  
## <a name="using-activityaction"></a>使用 ActivityAction  
 幾個 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 活動會使用活動的動作，例如 <xref:System.Activities.Statements.Catch> 活動和 <xref:System.Activities.Statements.ForEach%601> 活動。 在每一個情況下，活動的動作都代表一個位置，工作流程作者會在這裡指定活動，以便在使用其中一個活動撰寫工作流程時提供所要的行為。 在下列範例中，<xref:System.Activities.Statements.ForEach%601> 活動是用來將文字顯示到主控台視窗。 <xref:System.Activities.Statements.ForEach%601> 的主體是使用符合字串 <xref:System.Activities.ActivityAction%601> 之型別的 <xref:System.Activities.Statements.ForEach%601> 所指定。 <xref:System.Activities.Statements.WriteLine> 中指定的 <xref:System.Activities.ActivityDelegate.Handler%2A> 活動擁有繫結至字串值的 <xref:System.Activities.Statements.WriteLine.Text%2A> 引數，該字串值位於 <xref:System.Activities.Statements.ForEach%601> 活動所反覆查看的集合中。  
  
 [!code-csharp[CFX_ActivityExample#6](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#6)]  
  
 actionArgument 是用來將集合中的個別項目流動到 WriteLine。 當叫用此工作流程時，主控台就會顯示下列輸出。  
 ``` 
 HelloWorld.
 ```  
本主題的範例會使用物件初始化語法。 物件初始化語法在使用程式碼建立工作流程定義時會很有用，因為它會在工作流程中提供活動的階層式檢視，並顯示活動之間的關係。 當您以程式設計方式來建立工作流程時，不一定非得使用物件初始化語法。 下列範例在功能上等同於先前的範例。  
  
 [!code-csharp[CFX_ActivityExample#7](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#7)]  
  
 如需物件初始設定式的詳細資訊，請參閱[如何： 初始化的物件，而不呼叫建構函式 （C# 程式設計手冊）](http://go.microsoft.com/fwlink/?LinkId=161015)和[How to： 使用物件初始設定式宣告物件](http://go.microsoft.com/fwlink/?LinkId=161016)。  
  
 在下列範例中，<xref:System.Activities.Statements.TryCatch> 活動會用於工作流程中。 <xref:System.ApplicationException> 是由工作流程所擲回而且是由 <xref:System.Activities.Statements.Catch%601> 活動所處理。 處理常式<xref:System.Activities.Statements.Catch%601>活動的活動動作是<xref:System.Activities.Statements.WriteLine>活動和例外狀況詳細資料會流向它使用`ex` <xref:System.Activities.DelegateInArgument%601>。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#33](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#33)]  
  
 建立定義 <xref:System.Activities.ActivityAction%601> 的自訂活動時，請使用 <xref:System.Activities.Statements.InvokeAction%601> 來建立該 <xref:System.Activities.ActivityAction%601> 的引動過程模型。 在這個範例中，會定義自訂 `WriteLineWithNotification` 活動。 此活動是由包含 <xref:System.Activities.Statements.Sequence> 活動的 <xref:System.Activities.Statements.WriteLine> 所構成，此活動之後是採用一個字串引數來叫用 <xref:System.Activities.Statements.InvokeAction%601> 的 <xref:System.Activities.ActivityAction%601>。  
  
 [!code-csharp[CFX_ActivityExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#1)]  
  
 使用 `WriteLineWithNotification` 活動建立工作流程時，工作流程作者會在活動動作的 <xref:System.Activities.ActivityDelegate.Handler%2A> 中指定想要的自訂邏輯。 在此範例中，會使用 `WriteLineWithNotification` 活動建立工作流程，且 <xref:System.Activities.Statements.WriteLine> 活動會用來當做 <xref:System.Activities.ActivityDelegate.Handler%2A>。  
  
 [!code-csharp[CFX_ActivityExample#2](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#2)]  
  
 提供多個泛型版本的 <xref:System.Activities.Statements.InvokeAction%601> 和 <xref:System.Activities.ActivityAction%601>，以傳遞一個或多個引數。  
  
## <a name="using-activityfunc"></a>使用 ActivityFunc  
 當活動沒有結果值時，<xref:System.Activities.ActivityAction%601> 會非常實用。當傳回結果值時，將會使用 <xref:System.Activities.ActivityFunc%601>。 建立定義 <xref:System.Activities.ActivityFunc%601> 的自訂活動時，請使用 <xref:System.Activities.Expressions.InvokeFunc%601> 來建立該 <xref:System.Activities.ActivityFunc%601> 的引動過程模型。 在下列範例中，會定義 `WriteFillerText` 活動。 若要提供填入文字，應指定 <xref:System.Activities.Expressions.InvokeFunc%601> 採用整數引數，並具有字串結果。 一旦擷取了填入文字之後，就會使用 <xref:System.Activities.Statements.WriteLine> 活動將它顯示到主控台。  
  
 [!code-csharp[CFX_ActivityExample#3](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#3)]  
  
 若要提供文字，必須使用活動以採用一個 `int` 引數，並具有字串結果。 此範例顯示符合要求的 `TextGenerator` 活動。  
  
 [!code-csharp[CFX_ActivityExample#4](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#4)]  
  
 若要與 `TextGenerator` 活動共同使用 `WriteFillerText` 活動，請將它指定為 <xref:System.Activities.ActivityDelegate.Handler%2A>。  
  
 [!code-csharp[CFX_ActivityExample#5](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#5)]  
  
## <a name="see-also"></a>另請參閱  
 [公開和叫用 ActivityActions](../../../docs/framework/windows-workflow-foundation/samples/exposing-and-invoking-activityactions.md)
