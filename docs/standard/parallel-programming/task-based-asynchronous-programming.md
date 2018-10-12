---
title: 以工作為基礎的非同步程式設計
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallelism, task
ms.assetid: 458b5e69-5210-45e5-bc44-3888f86abd6f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a879cce8eb429e2daeaa5db963b3d95d1e944da
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47171370"
---
# <a name="task-based-asynchronous-programming"></a>以工作為基礎的非同步程式設計
工作平行程式庫 (TPL) 是以「工作」(Task) 的概念為基礎，工作表示非同步作業。 在某些方面，工作類似執行緒或 <xref:System.Threading.ThreadPool> 工作項目，但是抽象等級較高。 「工作平行處理原則」(Task Parallelism) 是指同時執行一個或多個獨立工作。 工作主要提供兩項優點：  
  
-   更有效率且更靈活地使用系統資源。  
  
     在幕後，工作會排入已用演算法加強之 <xref:System.Threading.ThreadPool> 的佇列中，這些演算法會判斷和調整執行緒數目，並提供負載平衡以發揮最大輸送量。 這樣會使得工作變得相當輕便，而且您可以建立許多工作來啟用細部的平行處理原則。  
  
-   比使用執行緒或工作項目提供更多的程式設計控制能力。  
  
     工作和以工作為中心建置的架構提供了一組豐富的 API，可支援等候、取消、接續、穩固的例外狀況處理、詳細狀態和自訂排程等各式各樣的作業。  
  
 基於這兩個理由，在 .NET Framework 中，TPL 是撰寫多執行緒、非同步和平行程式碼時較好的應用程式開發介面。  
  
## <a name="creating-and-running-tasks-implicitly"></a>隱含建立和執行工作  
 <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> 方法有便利的方式可讓您同時執行任何數目的任意陳述式。 只要為每個工作項目傳入 <xref:System.Action> 委派即可。 若要建立這些委派，使用 Lambda 運算式是最簡單的方式。 Lambda 運算式可以呼叫具名方法，或提供程式碼內嵌。 下列範例說明如何使用基本 <xref:System.Threading.Tasks.Parallel.Invoke%2A> 呼叫，建立並啟動兩項同時執行的工作。 第一個工作是由呼叫名為 `DoSomeWork` 之方法的 Lambda 運算式表示，而第二個工作是由呼叫名為 `DoSomeOtherWork` 之方法的 Lambda 運算式表示。  
  
> [!NOTE]
>  本文件使用 Lambda 運算式來定義 TPL 中的委派。 如果您不熟悉 C# 或 Visual Basic 中的 Lambda 運算式，請參閱 [PLINQ 和 TPL 中的 Lambda 運算式](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)。  
  
 [!code-csharp[TPL#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#21)]
 [!code-vb[TPL#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#21)]  
  
> [!NOTE]
>  <xref:System.Threading.Tasks.Task> 在幕後建立的 <xref:System.Threading.Tasks.Parallel.Invoke%2A> 執行個體數目，不一定會等於所提供的委派數目。 TPL 可採用各種不同的最佳化方式，尤其是有大量委派時。  
  
 如需詳細資訊，請參閱[如何：使用 Parallel.Invoke 來執行平行作業](../../../docs/standard/parallel-programming/how-to-use-parallel-invoke-to-execute-parallel-operations.md)。  
  
 若要進一步控制工作執行，或是從工作傳回值，您必須更明確地使用 <xref:System.Threading.Tasks.Task> 物件。  
  
## <a name="creating-and-running-tasks-explicitly"></a>明確建立和執行工作  
 不會傳回值的工作是以 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 類別表示。 會傳回值的工作則是以繼承自 <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> 的 <xref:System.Threading.Tasks.Task> 類別表示。 工作物件會處理基礎結構細節，並提供可供呼叫端執行緒在整個工作存留期存取的方法和屬性。 例如，您可以隨時存取工作的 <xref:System.Threading.Tasks.Task.Status%2A> 屬性，看看工作是否已開始執行、已執行完畢、已取消或已擲回例外狀況。 狀態是以 <xref:System.Threading.Tasks.TaskStatus> 列舉表示。  
  
 當您建立工作時，您會指定使用者委派給工作，這個使用者委派會封裝此工作會執行的程式碼。 委派可以以具名委派、匿名方法或 Lambda 運算式的形式呈現。 Lambda 運算式可以包含具名方法的呼叫，如下列範例所示。 請注意，此範例會包含對 <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> 方法的呼叫，以確保工作會在主控台模式應用程式結束前完成執行。  
  
 [!code-csharp[TPL_TaskIntro#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/lambda1.cs#1)]
 [!code-vb[TPL_TaskIntro#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/lambda1.vb#1)]  
  
 您也可以使用 <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> 方法直接以一道作業建立並啟動工作。 不論與目前執行緒相關聯的是哪個工作排程器，<xref:System.Threading.Tasks.Task.Run%2A> 方法都會使用預設的工作排程器來管理工作。 若不需要對工作的建立和排程多加控制，則 <xref:System.Threading.Tasks.Task.Run%2A> 方法是建立和啟動工作的較好方式。  
  
 [!code-csharp[TPL_TaskIntro#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/run1.cs#2)]
 [!code-vb[TPL_TaskIntro#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/run1.vb#2)]  
  
 您也可以使用 <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> 方法直接以一道作業建立並啟動工作。 如果建立和排程不需要分開，且您需要其他工作建立選項或使用特定排程器，或是如果需要透過其 <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> 屬性將其他狀態傳遞至您可以擷取的工作 (如下面範例所示)，請使用這個方法。  
  
 [!code-csharp[TPL_TaskIntro#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/asyncstate.cs#23)]
 [!code-vb[TPL_TaskIntro#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/asyncstate.vb#23)]  
  
 <xref:System.Threading.Tasks.Task> 和 <xref:System.Threading.Tasks.Task%601> 都會公開靜態 <xref:System.Threading.Tasks.Task.Factory%2A> 屬性，這個屬性會傳回 <xref:System.Threading.Tasks.TaskFactory> 的預設執行個體，讓您以 `Task.Factory.StartNew()` 的形式呼叫這個方法。 另外，在下面範例中，每個工作都屬於 <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> 類型，因此它們都各自具有包含計算結果的公用 <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> 屬性。 這些工作會以非同步方式執行，且可能以任何順序完成。 如果在計算完成之前就存取 <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性，則這個屬性會封鎖呼叫端執行緒，直到有值為止。  
  
 [!code-csharp[TPL_TaskIntro#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/result1.cs#4)]
 [!code-vb[TPL_TaskIntro#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/result1.vb#4)]  
  
 如需詳細資訊，請參閱[如何：從工作傳回值](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md)。  
  
 當您使用 Lambda 運算式建立委派時，可以存取原始程式碼中該時間點可見的所有變數。 不過，在某些情況下 (特別是在迴圈內)，Lambda 擷取的變數不是預期的變數。 它只會擷取最後的值，而不是在每次反覆運算後變動的值。 下面範例會說明此問題。 它會將迴圈計數器傳遞給 Lambda 運算式，這個運算式會具現化 `CustomData` 物件並使用迴圈計數器做為物件的識別項。 如範例輸出所示，每個 `CustomData` 物件都具有相同的識別項。  
  
 [!code-csharp[TPL_TaskIntro#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1b.cs#22)]
 [!code-vb[TPL_TaskIntro#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1b.vb#22)]  
  
 您可以透過工作的建構函式提供狀態物件給工作，以存取每個反覆項目的值。 下面範例是修改自先前的範例，是在建立 `CustomData` 物件 (此物件接著傳遞至 Lambda 運算式) 時使用迴圈計數器。  如範例輸出所示，每個 `CustomData` 物件現在會在物件具現化時根據迴圈計數器的值而擁有唯一識別項。  
  
 [!code-csharp[TPL_TaskIntro#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1a.cs#21)]
 [!code-vb[TPL_TaskIntro#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1a.vb#21)]  
  
 這個狀態會做為引數傳遞給工作委派，且可使用 <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> 屬性從工作物件存取。  下面範例是改變自先前的範例。 此範例會使用 <xref:System.Threading.Tasks.Task.AsyncState%2A> 屬性來顯示有關傳遞至 Lambda 運算式之 `CustomData` 物件的資訊。  
  
 [!code-csharp[TPL_TaskIntro#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/asyncstate.cs#23)]
 [!code-vb[TPL_TaskIntro#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/asyncstate.vb#23)]  
  
## <a name="task-id"></a>工作 ID  
 每個工作都會得到一個整數 ID，這個 ID 負責在應用程式定義域中唯一識別該工作，且可以經由 <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=nameWithType> 屬性來存取。 當要在 Visual Studio Debugger 的 [平行堆疊] 和 [工作] 視窗中檢閱工作資訊時，這個 ID 很有用。 ID 是採延遲建立的方式，也就是說，要等到收到要求後才會建立 ID。因此，每次執行程式時，工作都可能會有不同的 ID。 如需如何在偵錯工具中檢閱工作識別碼的詳細資訊，請參閱[使用工作視窗](/visualstudio/debugger/using-the-tasks-window)和[使用平行堆疊視窗](/visualstudio/debugger/using-the-parallel-stacks-window)。  
  
## <a name="task-creation-options"></a>工作建立選項  
 大多數建立工作的 API 都會提供用來接受 <xref:System.Threading.Tasks.TaskCreationOptions> 參數的多載。 您可以指定其中一個選項，指示工作排程器要如何在執行緒集區上排定工作。 下表列出各種工作建立選項。  
  
|<xref:System.Threading.Tasks.TaskCreationOptions> 參數值|描述|  
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|  
|<xref:System.Threading.Tasks.TaskCreationOptions.None>|未指定選項時的預設值。 排程器會使用其預設的啟發式來排定工作。|  
|<xref:System.Threading.Tasks.TaskCreationOptions.PreferFairness>|指定排定工作時，應該讓較早建立的工作較早執行，並讓較晚建立的工作較晚執行。|  
|<xref:System.Threading.Tasks.TaskCreationOptions.LongRunning>|指定工作表示一項長時間執行的作業。|  
|<xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent>|指定應該將工作建立為目前工作 (如果有的話) 的子系。 如需詳細資訊，請參閱[附加與中斷連結的子工作](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)。|  
|<xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach>|指定如果內部工作指定了 `AttachedToParent` 選項，則該工作不會成為附加的子工作。|  
|<xref:System.Threading.Tasks.TaskCreationOptions.HideScheduler>|指定預設排程器是從特定工作內部呼叫如 <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> 或 <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> 等方法所建立之工作的工作排程器，而不是此工作執行所在的排程器。|  
  
 這些選項可以透過位元 **OR** 運算結合在一起。 下列範例顯示具有 <xref:System.Threading.Tasks.TaskCreationOptions.LongRunning> 和 <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness> 選項的工作。  
  
 [!code-csharp[TPL_TaskIntro#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#03)]
 [!code-vb[TPL_TaskIntro#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#03)]  
  
## <a name="tasks-threads-and-culture"></a>工作、執行緒和文化特性  
 每個執行緒都有相關聯的文化特性和 UI 文化特性，分別由 <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> 屬性定義。 執行緒的文化特性會用在格式化、剖析、排序及字串比較之類的作業。 執行緒的 UI 文化特性會用於資源查閱。 一般來說，除非您使用 <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> 和 <xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=nameWithType> 屬性，為應用程式定義域中的所有執行緒指定預設文化特性，否則執行緒的預設文化特性和 UI 文化特性是由系統文化特性所定義。 如果您明確設定執行緒的文化特性，並啟動新的執行緒，新的執行緒並不會繼承呼叫執行緒的文化特性；相反地，其文化特性為預設系統文化特性。 如果應用程式是以早於 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 的 .NET Framework 版本為目標，則其以工作為基礎的程式設計模型遵循此做法。  
  
> [!IMPORTANT]
>  請注意，做為工作內容一部分的呼叫執行緒文化特性適用於以 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 為「目標」的應用程式，不適用於在 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]「之下執行」的應用程式。 在 Visual Studio 中建立專案時，您可以從 [新增專案] 對話方塊頂端的下拉式清單中選取特定版本的 .NET Framework 設為目標，如果是在 Visual Studio 之外，您可以使用 <xref:System.Runtime.Versioning.TargetFrameworkAttribute> 屬性。 如果應用程式是以早於 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 的 .NET Framework 版本為目標，或是不以特定版本的 .NET Framework 版本為目標，工作的文化特性還是取決於所執行之執行緒的文化特性。  
  
 從以 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 為目標的應用程式開始，即使工作是在執行緒集區執行緒上非同步執行，每項工作都會繼承呼叫執行緒的文化特性。  
  
 下列範例提供一個簡單的範例。 它使用 <xref:System.Runtime.Versioning.TargetFrameworkAttribute> 屬性將 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 設為目標，並將應用程式目前的文化特性變更為「法文 (法國)」(如果「法文 (法國)」已經是目前的文化特性，則變更為「英文 (美國)」)。 然後它叫用名為 `formatDelegate` 的委派，並傳回在新的文化特性中格式化為貨幣值的一些數字。 請注意，無論委派是做為同步或非同步工作，都會傳回預期的結果，因為非同步工作會繼承呼叫執行緒的文化特性。  
  
 [!code-csharp[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/cs/asyncculture1.cs#5)]
 [!code-vb[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/vb/asyncculture1.vb#5)]  
  
 如果您使用 Visual Studio，您可以省略 <xref:System.Runtime.Versioning.TargetFrameworkAttribute> 屬性，然後在 [新增專案] 對話方塊中建立專案時，改為選取 .NET Framework 4.6 做為目標。  
  
 如果輸出所反映的應用程式行為是以早於 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 的 .NET framework 版本為目標，請移除原始程式碼中的 <xref:System.Runtime.Versioning.TargetFrameworkAttribute> 屬性。 輸出會反映預設系統文化特性的格式化慣例，而不是呼叫執行緒文化特性的格式化慣例。  
  
 如需有關非同步工作和文化特性的詳細資訊，請參閱 <xref:System.Globalization.CultureInfo> 主題中的＜文化特性和以工作為基礎的非同步作業＞一節。  
  
## <a name="creating-task-continuations"></a>建立工作接續  
 <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> 方法可讓您指定在「前項工作」(Antecedent Task) 完成時要啟動的工作。 前項工作的參考會傳遞給接續工作的委派，以便檢查前項工作的狀態，並可藉由擷取 <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> 屬性的值，使用前項的輸出做為接續的輸入。  
  
 在下面範例中，`getData` 工作是透過呼叫 <xref:System.Threading.Tasks.TaskFactory.StartNew%60%601%28System.Func%7B%60%600%7D%29?displayProperty=nameWithType> 方法來啟動。 當 `processData` 完成時，會自動啟動 `getData` 工作，而 `displayData` 完成時會啟動 `processData`。 `getData` 會產生整數陣列，`processData` 工作可透過 `getData` 工作的 <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> 屬性存取該陣列。 `processData` 工作會處理該陣列並傳回結果，這個結果的類型是從傳遞給 <xref:System.Threading.Tasks.Task%601.ContinueWith%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%600%7D%2C%60%600%7D%29?displayProperty=nameWithType> 方法之 Lambda 運算式的傳回類型推斷而來。 當 `displayData` 完成時，`processData` 工作會自動執行，而 <xref:System.Tuple%603> Lambda 運算式傳回的 `processData` 物件可供 `displayData` 工作透過 `processData` 工作的 <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> 屬性來存取。 `displayData` 工作會接受 `processData` 工作的結果並且產生結果，這個結果的類型也是以類似方式推斷而來，且這個結果會放在 <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性中讓程式取得。  
  
 [!code-csharp[TPL_TaskIntro#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations1.cs#5)]
 [!code-vb[TPL_TaskIntro#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations1.vb#5)]  
  
 由於 <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> 是執行個體方法，所以您可以將方法呼叫鏈結在一起 (而不是具現化每個前項工作的 <xref:System.Threading.Tasks.Task%601> 物件)。 下面範例在功能上與前一個範例相同，不同之處在於會將對 <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> 方法的呼叫鏈結在一起。 請注意，由方法呼叫鏈結所傳回的 <xref:System.Threading.Tasks.Task%601> 物件是最後的接續工作。  
  
 [!code-csharp[TPL_TaskIntro#24](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations2.cs#24)]
 [!code-vb[TPL_TaskIntro#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations2.vb#24)]  
  
 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> 和 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> 方法可讓您從多個工作繼續執行。  
  
 如需詳細資訊，請參閱[使用接續工作鏈結工作](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md)。  
  
## <a name="creating-detached-child-tasks"></a>建立中斷連結的子工作  
 當在工作內執行的使用者程式碼建立新工作，卻未指定 <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> 選項時，新的工作不會以任何特殊方式與父工作保持同步。 這種非同步處理的工作稱為「中斷連結的巢狀工作」(Detached Nested Task) 或「中斷連結的子工作」(Detached Child Task)。 下面範例會示範一個工作如何建立一個中斷連結的子工作。  
  
 [!code-csharp[TPL_TaskIntro#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#07)]
 [!code-vb[TPL_TaskIntro#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#07)]  
  
 請注意，父工作不會等候中斷連結的子工作完成。  
  
## <a name="creating-child-tasks"></a>建立子工作  
 當在工作內執行的使用者程式碼以 <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> 選項建立新工作時，新的工作即稱為父工作的「附加的子工作」(Attached Child Task)。 您可以使用 <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> 選項來呈現結構化工作平行處理原則，因為父工作會隱含等候所有附加的子工作都完成。 下面範例會示範一個父工作如何建立十個附加的子工作。 請注意，雖然此範例會呼叫 <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> 方法等候父工作完成，但不一定會明確等候附加的子工作完成。  
  
 [!code-csharp[TPL_TaskIntro#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/child1.cs#8)]
 [!code-vb[TPL_TaskIntro#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/child1.vb#8)]  
  
 父工作可以使用 <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> 選項防止其他工作附加至父工作。 如需詳細資訊，請參閱[附加與中斷連結的子工作](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)。  
  
## <a name="waiting-for-tasks-to-finish"></a>等候工作完成  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> 類型會提供 <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> 和        <!--zz <xref:System.Threading.Tasks.Task%601.Wait%2A?displayProperty=nameWithType>--> `System.Threading.Tasks.Task.Wait` 方法的數個多載，這些多載可讓您等候工作完成。 此外，靜態 <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> 方法的多載可讓您等候工作陣列中的任一工作或所有工作完成。  
  
 您通常會因為下列其中一個原因而等候工作完成：  
  
-   主執行緒需要有工作的最終計算結果才能完成。  
  
-   您必須處理可能會從工作擲回的例外狀況。  
  
-   應用程式可能會在所有工作都已經完成執行之前結束。 例如，只要 `Main` (應用程式進入點) 中的所有同步程式碼都已執行，主控台應用程式就會終止。  
  
 下列範例顯示不含例外狀況處理的基本模式。  
  
 [!code-csharp[TPL_TaskIntro#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#06)]
 [!code-vb[TPL_TaskIntro#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#06)]  
  
 如需示範例外狀況處理的範例，請參閱[例外狀況處理](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md)。  
  
 有些多載可讓您指定逾時，有些多載則額外接受一個 <xref:System.Threading.CancellationToken> 做為輸入參數，讓等候作業本身也可以取消 (不管是透過程式設計還是做為對使用者輸入的回應)。  
  
 等候工作時，也會隱含等候該工作之所有使用 <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> 選項建立的子系。 如果工作已完成，則 <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> 會立即傳回。 <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> 方法會擲回工作所引發的任何例外狀況，即使 <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> 方法是在工作完成之後才呼叫也一樣。  
  
## <a name="composing-tasks"></a>組成工作  
 <xref:System.Threading.Tasks.Task> 和 <xref:System.Threading.Tasks.Task%601> 類別提供數種方法，可協助您撰寫多個工作來實作一般模式，以及更有效地使用 C#、Visual Basic 和 F# 提供的非同步語言功能。 本節說明 <xref:System.Threading.Tasks.Task.WhenAll%2A>、<xref:System.Threading.Tasks.Task.WhenAny%2A>、<xref:System.Threading.Tasks.Task.Delay%2A> 和 <xref:System.Threading.Tasks.Task.FromResult%2A> 方法。  
  
### <a name="taskwhenall"></a>Task.WhenAll  
 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 方法會以非同步方式來等候多個 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 物件完成。 這會提供可讓您等候多組不一致工作的多載版本。 例如，您可以在單一方法呼叫中等候多個 <xref:System.Threading.Tasks.Task> 和 <xref:System.Threading.Tasks.Task%601> 物件完成。  
  
### <a name="taskwhenany"></a>Task.WhenAny  
 <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> 方法會以非同步方式來等候多個 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 物件的其中一個完成。 和 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 方法一樣，此方法也會提供可讓您等候多組不一致工作的多載版本。 <xref:System.Threading.Tasks.Task.WhenAny%2A> 方法在下列情況下特別有用。  
  
-   重複的作業。 請考慮能夠以多種方式執行的演算法或作業。 您可以使用 <xref:System.Threading.Tasks.Task.WhenAny%2A> 方法，選擇先完成的作業，然後取消其餘作業。  
  
-   交錯作業。 您可以啟動所有必須完成的多個作業，和使用 <xref:System.Threading.Tasks.Task.WhenAny%2A> 方法以在每個作業完成時處理結果。 完成作業後，您可以開始一個或多個其他工作。  
  
-   已節流的作業。 您可以使用 <xref:System.Threading.Tasks.Task.WhenAny%2A> 方法來限制並行作業的數目，以擴充前一個案例。  
  
-   過期的作業。 您可以使用 <xref:System.Threading.Tasks.Task.WhenAny%2A> 方法選取一個或多個工作，以及在指定時間之後完成的工作，例如由 <xref:System.Threading.Tasks.Task.Delay%2A> 方法傳回的工作。 下一節將說明 <xref:System.Threading.Tasks.Task.Delay%2A> 方法。  
  
### <a name="taskdelay"></a>Task.Delay  
 <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> 方法會產生 <xref:System.Threading.Tasks.Task> 物件，這個物件會在指定的時間之後完成。 您可以使用這個方法建立執行下列動作的迴圈：偶爾輪詢資料，引入逾時，延遲使用者輸入處理長達一段預先定義的時間等等。  
  
### <a name="tasktfromresult"></a>Task(T).FromResult  
 使用 <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> 方法，您可以建立裝載預先計算結果的 <xref:System.Threading.Tasks.Task%601> 物件。 當您執行會傳回 <xref:System.Threading.Tasks.Task%601> 物件的非同步作業，而且該 <xref:System.Threading.Tasks.Task%601> 物件的結果已計算時，這個方法很有用。 如需範例示範如何使用 <xref:System.Threading.Tasks.Task.FromResult%2A> 來擷取快取保留之非同步下載作業的結果，請參閱[如何：建立經過預先計算的工作](../../../docs/standard/parallel-programming/how-to-create-pre-computed-tasks.md)。  
  
## <a name="handling-exceptions-in-tasks"></a>處理工作中的例外狀況  
 當工作擲回一個或多個例外狀況時，這些例外狀況會包裝在 <xref:System.AggregateException> 例外狀況中。 接著該例外狀況就會回傳給與工作聯結的執行緒，這通常會是正在等候該工作完成的執行緒，或是存取 <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性的執行緒。 這個行為有助於落實這樣的 .NET Framework 原則：即所有未處理的例外狀況預設都應該要終止處理序。 呼叫的程式碼可以在 `try`/`catch` 區塊中使用下列任何一個來處理例外狀況：  
  
-   <xref:System.Threading.Tasks.Task.Wait%2A> 方法  
  
-   <xref:System.Threading.Tasks.Task.WaitAll%2A> 方法  
  
-   <xref:System.Threading.Tasks.Task.WaitAny%2A> 方法  
  
-   <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性  
  
 聯結的執行緒也可以藉由在工作被進行記憶體回收之前就存取 <xref:System.Threading.Tasks.Task.Exception%2A> 屬性，以處理例外狀況。 存取這個屬性，可防止未處理的例外狀況觸發當物件完成時，會終止處理序的例外狀況傳播行為。  
  
 如需例外狀況和工作的詳細資訊，請參閱[例外狀況處理](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md)。  
  
## <a name="canceling-tasks"></a>取消工作  
 `Task` 類別支援合作式取消，且與 .NET Framework 4 中引進的 <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> 和 <xref:System.Threading.CancellationToken?displayProperty=nameWithType> 類別完全整合。 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 類別中的許多建構函式都接受 <xref:System.Threading.CancellationToken> 物件做為輸入參數。 許多 <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> 和 <xref:System.Threading.Tasks.Task.Run%2A> 多載也包含 <xref:System.Threading.CancellationToken> 參數。  
  
 您可以先建立語彙基元，之後再使用 <xref:System.Threading.CancellationTokenSource> 類別來發出取消要求。 請將語彙基元當做引數傳遞給 <xref:System.Threading.Tasks.Task>，並同時在您的使用者委派 (負責完成回應取消要求的動作) 中參考同一個語彙基元。  
  
 如需詳細資訊，請參閱[工作取消](../../../docs/standard/parallel-programming/task-cancellation.md)和[如何：取消工作及其子系](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)。  
  
## <a name="the-taskfactory-class"></a>TaskFactory 類別  
 <xref:System.Threading.Tasks.TaskFactory> 類別提供靜態方法，這些方法會封裝在建立和啟動工作及接續工作時常用的一些模式。  
  
-   最常用的模式是 <xref:System.Threading.Tasks.TaskFactory.StartNew%2A>，這個模式會以一個陳述式建立並啟動工作。  
  
-   當您從多個前項工作建立接續工作時，請使用 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> 方法或 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> 方法或 <xref:System.Threading.Tasks.Task%601> 類別中的對應項。 如需詳細資訊，請參閱[使用接續工作鏈結工作](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md)。  
  
-   若要在 `BeginX` 或 `EndX` 執行個體中封裝非同步程式設計模型 <xref:System.Threading.Tasks.Task> 和 <xref:System.Threading.Tasks.Task%601> 方法，請使用 <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> 方法。 如需詳細資訊，請參閱 [TPL 和傳統 .NET Framework 非同步程式設計](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)。  
  
 <xref:System.Threading.Tasks.TaskFactory> 類別或 <xref:System.Threading.Tasks.Task> 類別上會以靜態屬性的形式提供預設的 <xref:System.Threading.Tasks.Task%601> 供人存取。 您也可以直接具現化 <xref:System.Threading.Tasks.TaskFactory> 並指定各種選項，包括 <xref:System.Threading.CancellationToken>、<xref:System.Threading.Tasks.TaskCreationOptions> 選項、<xref:System.Threading.Tasks.TaskContinuationOptions> 選項或 <xref:System.Threading.Tasks.TaskScheduler>。 您在建立工作 Factory 時指定的任何選項都會套用至此 Factory 建立的所有工作，除非 <xref:System.Threading.Tasks.Task> 是以 <xref:System.Threading.Tasks.TaskCreationOptions> 列舉建立，在此情況下，工作的選項會覆寫工作 Factory 的選項。  
  
## <a name="tasks-without-delegates"></a>不含委派的工作  
 在某些情況下，您可能需要使用 <xref:System.Threading.Tasks.Task> 來封裝由外部元件 (而非您自己的使用者委派) 所執行的一些非同步作業。 如果作業是根據非同步程式設計模型 Begin/End 模式，您可以使用 <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> 方法。 如果不是根據這個模式，您可以使用 <xref:System.Threading.Tasks.TaskCompletionSource%601> 物件將作業包裝在工作中，進而享有利用 <xref:System.Threading.Tasks.Task> 撰寫程式的一些優點，例如支援例外狀況傳播和接續。 如需詳細資訊，請參閱<xref:System.Threading.Tasks.TaskCompletionSource%601>。  
  
## <a name="custom-schedulers"></a>自訂排程器  
 大部分的應用程式或程式庫開發人員並不在意工作會在哪一個處理器上執行、工作會如何將自己的成品與其他工作同步，或是工作會如何排定在 <xref:System.Threading.ThreadPool?displayProperty=nameWithType> 上。 他們只要求工作能夠在主機電腦上盡可能有效率地執行。 如果您需要進一步控制排程細節，工作平行程式庫可讓您設定預設工作排程器上的某些設定，甚至可讓您提供自訂的排程器。 如需詳細資訊，請參閱<xref:System.Threading.Tasks.TaskScheduler>。  
  
## <a name="related-data-structures"></a>相關資料結構  
 TPL 提供數個新的公用類型，這些類型在平行處理和序列處理情節中會很有用。 這些類型包括 <xref:System.Collections.Concurrent?displayProperty=nameWithType> 命名空間中數個具備執行緒安全、快速和可擴充的集合類別，以及數個新的同步處理類型 (例如 <xref:System.Threading.Semaphore?displayProperty=nameWithType> 和 <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>)，這些類型在特定類型的工作負載上表現的比它們的前身更有效率。 .NET Framework 4 中還有其他新的類型 (例如 <xref:System.Threading.Barrier?displayProperty=nameWithType> 和 <xref:System.Threading.SpinLock?displayProperty=nameWithType>) 可提供舊版所沒有的功能。 如需詳細資訊，請參閱[適用於平行程式設計的資料結構](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)。  
  
## <a name="custom-task-types"></a>自訂工作類型  
 建議您不要繼承自 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 或 <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>， 建議您改用 <xref:System.Threading.Tasks.Task.AsyncState%2A> 屬性，建立其他資料或狀態與 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 物件的關聯。 您也可以使用擴充方法，擴充 <xref:System.Threading.Tasks.Task> 和 <xref:System.Threading.Tasks.Task%601> 類別的功能。 如需擴充方法的詳細資訊，請參閱[擴充方法](~/docs/csharp/programming-guide/classes-and-structs/extension-methods.md)和[擴充方法](~/docs/visual-basic/programming-guide/language-features/procedures/extension-methods.md)。  
  
 如果必須繼承自 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601>，則不可以使用 <xref:System.Threading.Tasks.Task.Run%2A>、<xref:System.Threading.Tasks.Task.Run%2A> 或 <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType>、<xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType> 或 <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> 類別來建立自訂工作類型的執行個體，因為這些機制只會建立 <xref:System.Threading.Tasks.Task> 和 <xref:System.Threading.Tasks.Task%601> 物件。 此外，也不可以使用 <xref:System.Threading.Tasks.Task>、<xref:System.Threading.Tasks.Task%601>、<xref:System.Threading.Tasks.TaskFactory> 和 <xref:System.Threading.Tasks.TaskFactory%601> 所提供的工作接續機制來建立自訂工作類型執行個體，因為這些機制也是只建立 <xref:System.Threading.Tasks.Task> 和 <xref:System.Threading.Tasks.Task%601> 物件。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-|-|  
|[使用接續工作鏈結工作](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md)|說明接續的運作方式。|  
|[附加與中斷連結的子工作](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)|說明附加的與中斷連結的子工作之間的差異。|  
|[工作取消](../../../docs/standard/parallel-programming/task-cancellation.md)|說明 <xref:System.Threading.Tasks.Task> 物件內建的取消支援。|  
|[例外狀況處理](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md)|說明並行執行緒上發生例外狀況時的處理方式。|  
|[操作說明：使用 Parallel.Invoke 執行平行作業](../../../docs/standard/parallel-programming/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|說明如何使用 <xref:System.Threading.Tasks.Parallel.Invoke%2A>。|  
|[操作說明：傳回工作的值](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md)|說明如何從工作傳回值。|  
|[如何：取消工作及其子系](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)|說明如何取消工作。|  
|[操作說明：建立經過預先計算的工作](../../../docs/standard/parallel-programming/how-to-create-pre-computed-tasks.md)|描述如何使用 <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> 方法擷取保留在快取中之非同步下載作業的結果。|  
|[操作說明：使用平行工作周遊二進位樹狀](../../../docs/standard/parallel-programming/how-to-traverse-a-binary-tree-with-parallel-tasks.md)|說明如何使用工作，在二進位樹狀目錄中周遊。|  
|[操作說明：解除包裝巢狀工作](../../../docs/standard/parallel-programming/how-to-unwrap-a-nested-task.md)|示範如何使用 <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> 擴充方法。|  
|[資料平行處理原則](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)|說明如何使用 <xref:System.Threading.Tasks.Parallel.For%2A> 和 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 建立資料的平行迴圈。|  
|[平行程式設計](../../../docs/standard/parallel-programming/index.md)|.NET Framework 平行程式設計的最上層節點。|  
  
## <a name="see-also"></a>另請參閱

- [平行程式設計](../../../docs/standard/parallel-programming/index.md)  
- [使用 .NET Framework 進行平行程式設計的範例](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
