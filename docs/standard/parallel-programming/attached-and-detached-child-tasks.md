---
title: "附加與中斷連結的子工作"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: tasks, child tasks
ms.assetid: c95788bf-90a6-4e96-b7bc-58e36a228cc5
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c1a0c664dffc2986d4d6985fd2b71cd8055bf2c9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="attached-and-detached-child-tasks"></a>附加與中斷連結的子工作
A*子工作*(或*巢狀的工作*) 是<xref:System.Threading.Tasks.Task?displayProperty=nameWithType>另一項工作，也就是使用者委派中建立的執行個體*父工作*。 子工作可以中斷連結或附加。 A*中斷連結的子工作*是其父代之外單獨執行的工作。 *附加子工作*是用來建立巢狀的工作<xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType>其父代並不明確或預設禁止它附加的選項。 工作可能會建立任意數目的附加和中斷連結的子工作，只受限於系統資源。  
  
 下表列出這兩種子工作之間的基本差異。  
  
|分類|中斷連結的子工作|附加的子工作|  
|--------------|--------------------------|--------------------------|  
|等候子工作完成的父系。|否|是|  
|父系會傳播子工作擲回的例外狀況。|否|是|  
|父系的狀態取決於子系的狀態。|否|是|  
  
 在大部分情況下，我們建議您使用中斷連結的子工作，因為它們與其他工作的關聯性較不複雜。 這也就是為什麼在父工作中建立的工作會依預設中斷連結，且您必須明確指定 <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> 選項才能建立附加的子工作。  
  
## <a name="detached-child-tasks"></a>中斷連結的子工作  
 雖然子工作由父工作建立，依預設它與父工作無關。 在下列範例中，父工作會建立一個簡單的子工作。 如果多次執行範例程式碼，您可能會注意到範例的輸出會不同於所顯示內容，且每次執行程式碼時輸出也可能變更。 這是因為父工作和子工作執行時彼此無關。子系是中斷連結的工作。 此範例只會等候父工作完成，子工作可能無法在主控台應用程式終止之前執行或完成。  
  
 [!code-csharp[TPL_ChildTasks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/nested1.cs#1)]
 [!code-vb[TPL_ChildTasks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/nested1.vb#1)]  
  
 如果子工作由 <xref:System.Threading.Tasks.Task%601> 物件代表，而非 <xref:System.Threading.Tasks.Task> 物件，則您可以藉由存取子系的 <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> 屬性確保父工作會等待子系完成，即使它是中斷連結的子工作。 <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性會封鎖，直到完成其工作，如下列範例所示。  
  
 [!code-csharp[TPL_ChildTasks#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/childtasks.cs#4)]
 [!code-vb[TPL_ChildTasks#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/tpl_childtasks.vb#4)]  
  
## <a name="attached-child-tasks"></a>附加的子工作  
 不同於中斷連結的子工作，附加的子工作與父代密切同步。 您可以將前一個範例中的中斷連結子工作，變更為附加的子工作，只要在工作建立陳述式中使用 <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> 選項，如下列範例所示。 在此程式碼中，附加的子工作會在其父系之前完成。 如此一來，此範例的輸出在您每次執行程式碼時都會相同。  
  
 [!code-csharp[TPL_ChildTasks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1.cs#2)]
 [!code-vb[TPL_ChildTasks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1.vb#2)]  
  
 您可以使用附加的子工作，建立非同步作業的緊密同步處理圖形。  
  
 不過，子工作只能在其父代未禁止附加子工作時附加至其父代。 父工作可以明確地防止子工作附加至其上，方法是在父工作的類別建構函式中指定 <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> 選項或 <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> 方法。 如果父工作是藉由呼叫 <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> 方法而建立，則父工作會隱含地防止子工作附加至它們。 下列範例將說明這點。 它與先前的範例相同，只除了父工作是藉由呼叫 <xref:System.Threading.Tasks.Task.Run%28System.Action%29?displayProperty=nameWithType> 方法建立，而非 <xref:System.Threading.Tasks.TaskFactory.StartNew%28System.Action%29?displayProperty=nameWithType> 方法。 因為子工作不能附加至其父代，所以無法預期此範例的輸出。 因為 <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> 多載的預設工作建立選項包含 <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>，此範例在功能上等於＜中斷連結的子工作＞一節中的第一個範例。  
  
 [!code-csharp[TPL_ChildTasks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1a.cs#3)]
 [!code-vb[TPL_ChildTasks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1a.vb#3)]  
  
## <a name="exceptions-in-child-tasks"></a>子工作中的例外狀況  
 如果中斷連結的子工作擲回例外狀況，則必須直接在父工作中觀察或處理該例外狀況，就像對任何非巢狀工作一樣。 如果附加的子工作擲回例外狀況，例外狀況會自動傳播至父工作，以及回到等待或嘗試存取工作之 <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> 屬性的緒行緒。 因此，藉由使用附加的子工作，您可以在呼叫執行緒上，對 <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> 的呼叫中，一次處理所有例外狀況。 如需詳細資訊，請參閱[例外狀況處理](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md)。  
  
## <a name="cancellation-and-child-tasks"></a>取消和子工作  
 工作取消需要合作。 也就是說，若要能取消，每個附加或中斷連結的子工作必須監視取消語彙基元的狀態。 如果您想要使用一個取消要求來取消父系及其所有子系，您會將相同的語彙基元當做引數傳遞至所有工作，並在每個工作中提供邏輯以回應每個工作中的要求。 如需詳細資訊，請參閱[工作取消](../../../docs/standard/parallel-programming/task-cancellation.md)和[如何：取消工作及其子系](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)。  
  
### <a name="when-the-parent-cancels"></a>當父系取消時  
 如果父系在其子工作啟動之前自行取消，則永遠不會啟動子系。 如果父系在子工作已經開始之後自行取消，則子系會執行到完成為止，除非它有自己的取消邏輯。 如需詳細資訊，請參閱 [Task Cancellation](../../../docs/standard/parallel-programming/task-cancellation.md)。  
  
### <a name="when-a-detached-child-task-cancels"></a>當取消中斷連結的子工作時  
 如果中斷連結的子工作使用傳遞給父系的相同語彙基元來自行取消，且父系不等候子工作，則不會傳播任何例外狀況，因為例外狀況被視為良性合作取消。 此行為與任何最上層工作相同。  
  
### <a name="when-an-attached-child-task-cancels"></a>當取消附加的子工作時  
 當附加的子工作使用傳遞給父工作的相同語彙基元來自行取消時，<xref:System.Threading.Tasks.TaskCanceledException> 會傳播到 <xref:System.AggregateException> 內部的聯結執行緒。 您必須等候父工作，以便處理所有良性的例外狀況，以及所有在附加的子工作的圖形間向上傳播的錯誤例外狀況。  
  
 如需詳細資訊，請參閱[例外狀況處理](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md)。  
  
## <a name="preventing-a-child-task-from-attaching-to-its-parent"></a>防止子工作附加到其父系  
 子工作所擲回的未處理例外狀況會傳播到父工作。 您可以使用此行為來從一個根工作觀察所有子工作例外狀況，而不必周遊工作樹狀結構。 不過，當父工作不預期會有來自其他程式碼的附加時，例外狀況傳播可能會造成問題。 例如，假設應用程式從 <xref:System.Threading.Tasks.Task> 物件呼叫協力廠商程式庫元件。 如果協力廠商程式庫元件也會建立 <xref:System.Threading.Tasks.Task> 物件，並指定 <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> 將它附加至父工作，則在子工作中發生任何未處理例外狀況都會傳播到父系。 這可能會導致在主應用程式中非預期的行為。  
  
 若要防止子工作附加至其父工作，，當您建立父 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 物件時，請指定 <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> 選項。 當工作嘗試附加至其父系，而父系指定 <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> 選項，則子工作將無法附加至父系，並且執行時就如同未指定 <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> 選項。  
  
 當子工作未及時完成時，您也可能想要防止子工作附加到其父系。 由於父工作會在所有子工作完成後才完成，因此長時間執行的子工作可能造成整個應用程式效能不佳。 如需示範如何藉由防止工作附加至其父工作，改善應用程式效能的範例，請參閱[如何： 防止子工作附加至其父代](../../../docs/standard/parallel-programming/how-to-prevent-a-child-task-from-attaching-to-its-parent.md)。  
  
## <a name="see-also"></a>另請參閱  
 [平行程式設計](../../../docs/standard/parallel-programming/index.md)  
 [資料平行處理原則](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
