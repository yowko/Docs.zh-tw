---
title: "延遲初始設定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lazy initialization in .NET, introduction
ms.assetid: 56b4ae5c-4745-44ff-ad78-ffe4fcde6b9b
caps.latest.revision: 22
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7c176079cba9e866c10d7979de8e5c118e3e438f
ms.contentlocale: zh-tw
ms.lasthandoff: 08/21/2017

---
# <a name="lazy-initialization"></a>延遲初始設定
物件的「延遲初始設定」表示物件一直延遲到第一次使用才建立。 (在本主題中，「延遲初始設定」和「延遲具現化」二詞為同義字。)延遲初始設定主要是用來改善效能，避免不必要的計算，並減少程式記憶體需求。 以下為最常見的案例：  
  
-   當建立某個物件會耗費大量資源，而程式可能不使用它時。 例如，假設您在記憶體中有 `Customer` 物件，它的 `Orders` 屬性包含大型的 `Order` 物件陣列，其初始化需要連接資料庫。 如果使用者從未要求顯示訂單，或使用資料進行計算，就沒必要使用系統記憶體或計算週期來建立它。 使用 `Lazy<Orders>` 宣告延遲初始設定 `Orders` 物件，可在不使用物件時，避免浪費系統資源。  
  
-   當建立某個物件會耗費大量資源，而您想要延遲到完成其他耗費資源的作業後，再建立它。 例如，假設當程式啟動時會載入數個物件執行個體，但只有部分是立即需要的。 您可以延遲到必要的物件皆已建立後，再對不需要的物件進行初始設定，以改善程式的啟動效能。  
  
 雖然您可以自行撰寫程式碼執行延遲初始設定，但仍建議您改用 <xref:System.Lazy%601>。 <xref:System.Lazy%601> 及其相關類型也支援安全執行緒，並提供一致的例外狀況傳播原則。  
  
 下表列出 .NET Framework 第 4 版提供的類型，以在不同案例中啟用延遲初始化。  
  
|類型|說明|  
|----------|-----------------|  
|<xref:System.Lazy%601>|為任何類別庫或使用者定義類型提供延遲初始化語意的包裝函式類別。|  
|<xref:System.Threading.ThreadLocal%601>|類似於 <xref:System.Lazy%601>，不同之處在於它是在執行緒區域上提供延遲初始化語意。 每個執行緒都可以存取自己的唯一值。|  
|<xref:System.Threading.LazyInitializer>|為物件的延遲初始設定提供進階 `static` (Visual Basic 為 `Shared`) 方法，沒有類別的額外負荷。|  
  
## <a name="basic-lazy-initialization"></a>基本延遲初始設定  
 若要定義延遲初始化類型，例如 `MyType`，請使用 `Lazy<MyType>` (Visual Basic 為 `Lazy(Of MyType)`)，如下列範例所示。 如果沒有委派傳入 <xref:System.Lazy%601> 建構函式，第一次存取 Value 屬性時，會使用 <xref:System.Activator.CreateInstance%2A?displayProperty=fullName> 建立包裝類型。 如果類型沒有預設的建構函式，就會擲回執行階段例外狀況。  
  
 在下例中，假設 `Orders` 是類別，包含從資料庫擷取的 `Order` 物件陣列。 `Customer` 物件包含 `Orders` 的執行個體，但視使用者的動作而 定，可能不需要來自 `Orders` 物件的資料。  
  
 [!code-csharp[Lazy#1](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#1)] [!code-vb[Lazy#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#1)]  
  
 您也可以在 <xref:System.Lazy%601> 建構函式中傳遞委派，此建構函式會在特定時間於包裝類型上叫用特定的建構函式多載，執行任何其他需要的初始設定步驟，如下列範例中所示。  
  
 [!code-csharp[Lazy#2](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#2)] [!code-vb[Lazy#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#2)]  
  
 建立延遲物件後，要到第一次存取延遲變數的 <xref:System.Lazy%601.Value%2A> 屬性後，才會建立 `Orders` 的執行個體。 第一次存取時，會建立並傳回包裝類型，儲存以供未來存取。  
  
 [!code-csharp[Lazy#3](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#3)] [!code-vb[Lazy#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#3)]  
  
 <xref:System.Lazy%601> 物件一律傳回相同的物件或隨之初始化的值。 因此，<xref:System.Lazy%601.Value%2A> 屬性是唯讀的。 如果 <xref:System.Lazy%601.Value%2A> 儲存參考型別，您就無法指派新的物件給它。 (不過，您可以變更其可設定的公用欄位和屬性的值。)如果 <xref:System.Lazy%601.Value%2A> 儲存實值型別，您就無法修改其值。 不過，您可以使用新的引數再次叫用變數的建構函式，建立新的變數。  
  
 [!code-csharp[Lazy#4](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#4)] [!code-vb[Lazy#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#4)]  
  
 新的延遲執行個體，像舊版一樣，一直要到第一次存取其 <xref:System.Lazy%601.Value%2A> 屬性後，才會具現化 `Orders`。  
  
### <a name="thread-safe-initialization"></a>初始化安全執行緒  
 根據預設，<xref:System.Lazy%601> 物件是安全執行緒。 也就是說，如果建構函式不指定執行緒安全的種類，它建立的 <xref:System.Lazy%601> 物件就會是安全執行緒。 在多執行緒案例中，第一個存取安全執行緒 <xref:System.Lazy%601> 物件的 <xref:System.Lazy%601.Value%2A> 屬性的執行緒，會將它初始化以在所有的執行緒上進行所有的後續存取，且所有執行緒都共用相同的資料。 因此，哪個執行緒初始化物件不重要，只要是良性的競爭條件即可。  
  
> [!NOTE]
>  您可以使用快取例外狀況，擴充錯誤條件的一致性。 如需詳細資訊，請參閱下一節[延遲物件的例外狀況](../../../docs/framework/performance/lazy-initialization.md#ExceptionsInLazyObjects)。  
  
 下列範例示範，相同的 `Lazy<int>` 執行個體在三個不同的執行緒有相同的值。  
  
 [!code-csharp[Lazy#8](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#8)] [!code-vb[Lazy#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#8)]  
  
 如果每個執行緒需要個別的資料，請使用 <xref:System.Threading.ThreadLocal%601> 類型，如本主題稍後所述。  
  
 某些 <xref:System.Lazy%601> 建構函式有名為 `isThreadSafe` 的布林參數，用來指定是否從多個執行緒存取 <xref:System.Lazy%601.Value%2A> 屬性。 如果您只打算從一個執行緒存取屬性，請傳入 `false` 以取得適度的效能優勢。 如果打算從多個執行緒存取屬性，請傳入 `true` 指示 <xref:System.Lazy%601> 執行個體正確處理一個執行緒在初始化階段擲出例外狀況的競爭條件。  
  
 某些 <xref:System.Lazy%601> 建構函式有名為 `mode` 的 <xref:System.Threading.LazyThreadSafetyMode> 參數。 這些建構函式提供其他的執行緒安全性模式。 下表顯示指定執行緒安全性的建構函式參數如何影響 <xref:System.Lazy%601> 物件的執行緒安全性。 每個建構函式最多只有一個這類參數。  
  
|物件的執行緒安全性|`LazyThreadSafetyMode` `mode` 參數|布林 `isThreadSafe` 參數|沒有執行緒安全性參數|  
|---------------------------------|---------------------------------------------|--------------------------------------|---------------------------------|  
|完整的安全執行緒，一次只有一個執行緒嘗試初始化值。|<xref:System.Threading.LazyThreadSafetyMode>|`true`|可以。|  
|不具備安全執行緒。|<xref:System.Threading.LazyThreadSafetyMode>|`false`|不適用。|  
|完整的安全執行緒，多個執行緒競相初始化值。|<xref:System.Threading.LazyThreadSafetyMode>|不適用。|不適用。|  
  
 如本表所示，指定 `mode` 參數的 <xref:System.Threading.LazyThreadSafetyMode?displayProperty=fullName> 如同指定 `isThreadSafe` 參數的 `true`，而指定 <xref:System.Threading.LazyThreadSafetyMode?displayProperty=fullName> 如同指定 `false`。  
  
 指定 <xref:System.Threading.LazyThreadSafetyMode?displayProperty=fullName> 可讓多個執行緒嘗試初始化 <xref:System.Lazy%601> 執行個體。 只有一個執行緒可贏得這場競賽，所有其他的執行緒都會收到成功的執行緒所初始化的值。 如果在初始化期間，對執行緒擲回例外狀況，該執行緒就不會收到成功的執行緒所設定的值。 例外狀況不會被快取，所以後續嘗試存取 <xref:System.Lazy%601.Value%2A> 屬性會導致成功初始化。 這不同於其他方法處理例外狀況的方式，下節中會對此加以說明。 如需詳細資訊，請參閱 <xref:System.Threading.LazyThreadSafetyMode> 列舉。  
  
<a name="ExceptionsInLazyObjects"></a>   
## <a name="exceptions-in-lazy-objects"></a>延遲物件的例外狀況  
 如前所述，<xref:System.Lazy%601> 物件一律會傳回隨之初始化的相同物件或值，因此 <xref:System.Lazy%601.Value%2A> 屬性是唯讀的。 如果啟用例外狀況快取，此不變性也會延伸至例外狀況行為。 如果延遲初始化的物件啟用了例外狀況快取，並在第一次存取 <xref:System.Lazy%601.Value%2A> 屬性時，從它的初始設定方法擲回例外狀況，則後續每次嘗試存取 <xref:System.Lazy%601.Value%2A> 屬性都會擲回相同的例外狀況。 換句話說，即使在多執行緒案例中，也絕對不會重新叫用包裝類型的建構函式。 因此，<xref:System.Lazy%601> 物件無法在某次存取中擲回例外狀況，並在後續存取中傳回值。  
  
 當您使用任何採用初始設定方法 (`valueFactory` 參數) 的 <xref:System.Lazy%601?displayProperty=fullName> 建構函式時，就啟用了例外狀況快取；例如，它會在您使用 `Lazy(T)(Func(T))` 建構函式時啟用。 如果建構函式也採用 <xref:System.Threading.LazyThreadSafetyMode> 值 (`mode` 參數)，請指定 <xref:System.Threading.LazyThreadSafetyMode?displayProperty=fullName> 或 <xref:System.Threading.LazyThreadSafetyMode?displayProperty=fullName>。 指定初始設定方法，可啟用這兩種模式的例外狀況快取。 初始設定方法可以非常簡單。 例如，它可能會呼叫 `T` 的預設建構函式：C# 為 `new Lazy<Contents>(() => new Contents(), mode)`，或 Visual Basic 為 `New Lazy(Of Contents)(Function() New Contents())`。 如果您使用未指定初始設定方法的 <xref:System.Lazy%601?displayProperty=fullName> 建構函式，則不會快取 `T` 的預設建構函式擲回的例外狀況。 如需詳細資訊，請參閱 <xref:System.Threading.LazyThreadSafetyMode> 列舉。  
  
> [!NOTE]
>  如果您建立的 <xref:System.Lazy%601> 物件是將 `isThreadSafe` 建構函式參數設定為 `false`，或將 `mode` 建構函式參數設定為 <xref:System.Threading.LazyThreadSafetyMode?displayProperty=fullName>，您即必須從單一執行緒存取 <xref:System.Lazy%601> 物件，或提供您自己的同步處理。 這適用該物件的所有層面，包括例外狀況快取。  
  
 如前一節中所述，透過指定 <xref:System.Threading.LazyThreadSafetyMode?displayProperty=fullName> 所建立的 <xref:System.Lazy%601> 物件，會以不同的方式處理例外狀況。 有了 <xref:System.Threading.LazyThreadSafetyMode>，多個執行緒可爭奪初始化 <xref:System.Lazy%601> 執行個體。 本例中未快取例外狀況，但會繼續嘗試存取 <xref:System.Lazy%601.Value%2A> 屬性，直到成功初始化。  
  
 下表摘要說明 <xref:System.Lazy%601> 建構函式控制例外狀況快取的方式。  
  
|建構函式|執行緒安全模式|使用初始設定方法|已快取例外狀況|  
|-----------------|------------------------|--------------------------------|---------------------------|  
|Lazy(T)()|(<xref:System.Threading.LazyThreadSafetyMode>)|否|否|  
|Lazy(T)(Func(T))|(<xref:System.Threading.LazyThreadSafetyMode>)|是|是|  
|Lazy(T)(Boolean)|`True` (<xref:System.Threading.LazyThreadSafetyMode>) 或 `false` (<xref:System.Threading.LazyThreadSafetyMode>)|否|否|  
|Lazy(T)(Func(T), Boolean)|`True` (<xref:System.Threading.LazyThreadSafetyMode>) 或 `false` (<xref:System.Threading.LazyThreadSafetyMode>)|是|是|  
|Lazy(T)(LazyThreadSafetyMode)|使用者指定的|否|否|  
|Lazy(T)(Func(T), LazyThreadSafetyMode)|使用者指定的|是|如果使用者指定了 <xref:System.Threading.LazyThreadSafetyMode> 則為否；否則為是。|  
  
## <a name="implementing-a-lazy-initialized-property"></a>實作延遲初始化的屬性  
 若要使用延遲初始設定來實作公用屬性，請將屬性的支援欄位定義為 <xref:System.Lazy%601>，並從屬性的 `get` 存取子傳回 <xref:System.Lazy%601.Value%2A> 屬性。  
  
 [!code-csharp[Lazy#5](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#5)] [!code-vb[Lazy#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#5)]  
  
 <xref:System.Lazy%601.Value%2A> 屬性是唯讀的；因此，公開它的屬性沒有任何 `set` 存取子。 如果您需要 <xref:System.Lazy%601> 物件支援的讀取/寫入屬性，`set` 存取子必須建立新的 <xref:System.Lazy%601> 物件，並指派到備份存放區。 `set` 存取子必須建立 Lambda 運算式，傳回已傳遞給 `set` 存取子的新屬性值，並將該 Lambda 運算式傳遞至新 <xref:System.Lazy%601> 物件的建構函式。 下一次存取 <xref:System.Lazy%601.Value%2A> 屬性會初始化新的 <xref:System.Lazy%601>，且其 <xref:System.Lazy%601.Value%2A> 屬性之後也會傳回已指派給屬性的新值。 之所以如此迂迴排列，是為了保留內建在 <xref:System.Lazy%601> 的多執行緒保護。 否則，屬性存取子就必須快取 <xref:System.Lazy%601.Value%2A> 屬性傳回的第一個值，且只能修改快取的值，而您則必須撰寫自己的執行緒安全程式碼以完成此作業。 因為 <xref:System.Lazy%601> 物件支援的讀取/寫入屬性需要額外的初始設定，效能可能不太令人滿意。 此外，根據特定的案例，可能需要其他協調以避免 setter 與 getter 之間的競爭條件。  
  
## <a name="thread-local-lazy-initialization"></a>執行緒區域延遲初始設定  
 在某些多執行緒的情況下，您可能想要向各執行緒提供它專用的私用資料。 這類資料稱為「執行緒區域資料」。 在 .NET Framework 3.5 版或更舊的版本中，您可以將 `ThreadStatic` 屬性套用到靜態變數，使其成為執行緒區域變數。 不過，使用 `ThreadStatic` 屬性可能會導致極其細小的錯誤。 例如，即使基本的初始化陳述式，也只會在第一個存取它的執行緒上初始化變數，如下列範例所示。  
  
 [!code-csharp[Lazy#6](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#6)] [!code-vb[Lazy#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#6)]  
  
 在所有其他的執行緒上，變數都是使用其預設值 (零) 來初始化。 在 .NET Framework 第 4 版中它是替代方案，您可以使用 <xref:System.Threading.ThreadLocal%601?displayProperty=fullName> 類型建立執行個體式的執行緒本機變數，由您提供的 <xref:System.Action%601> 委派在所有執行緒上初始化。 在下列範例中，存取 `counter` 的所有執行緒都會看到其起始值為 1。  
  
 [!code-csharp[Lazy#7](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#7)] [!code-vb[Lazy#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#7)]  
  
 <xref:System.Threading.ThreadLocal%601> 包裝其物件的方法，和 <xref:System.Lazy%601> 極其相似，但有以下基本差異：  
  
-   每個執行緒都是使用不能從其他執行緒存取的專用私用資料，來初始化執行緒區域變數。  
  
-   <xref:System.Threading.ThreadLocal%601.Value%2A?displayProperty=fullName> 屬性是讀寫的，不限修改次數。 這會影響例外狀況傳播，例如，一個 `get` 作業可能會引發例外狀況，但下一個卻可以成功初始化值。  
  
-   如未提供任何初始設定委派，則 <xref:System.Threading.ThreadLocal%601> 會使用預設的類型值初始化其包裝類型。 在這方面，<xref:System.Threading.ThreadLocal%601> 和 <xref:System.ThreadStaticAttribute> 屬性一致。  
  
 下列範例示範，存取 `ThreadLocal<int>` 執行個體的每一個執行緒都會取得自己唯一的資料複本。  
  
 [!code-csharp[Lazy#9](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#9)] [!code-vb[Lazy#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#9)]  
  
## <a name="thread-local-variables-in-parallelfor-and-foreach"></a>Parallel.For 和 ForEach 的執行緒區域變數  
 當您使用 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName> 方法或 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> 方法平行逐一查看資料來源時，您可以使用有執行緒區域資料內建支援的多載。 在這些方法中，執行緒位置是使用本機委派建立、存取和清除資料所達成的。 如需詳細資訊，請參閱[如何：撰寫含有執行緒區域變數的 Parallel.For 迴圈](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)和[如何：撰寫含有執行緒區域變數的 Parallel.ForEach 迴圈](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-thread-local-variables.md)。  
  
## <a name="using-lazy-initialization-for-low-overhead-scenarios"></a>低負荷情況下使用延遲初始設定  
 在必須延遲初始化大量物件的情況下，您可能會判定，包裝 <xref:System.Lazy%601> 中的每個物件需要太多記憶體或太多的運算資源。 或者，您可能對延遲初始設定的公開方式有嚴格的要求。 在這種情況下，您可以使用 <xref:System.Threading.LazyInitializer?displayProperty=fullName> 類別的 `static` (Visual Basic 為 `Shared`) 方法，延遲初始化每個物件，不將它包裝在 <xref:System.Lazy%601> 的執行個體中。  
  
 在下列範例中，假設不將整個 `Orders` 物件包裝在一個 <xref:System.Lazy%601> 物件中，您只有在必要時才會延遲初始化個別的 `Order` 物件。  
  
 [!code-csharp[Lazy#10](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#10)] [!code-vb[Lazy#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#10)]  
  
 請注意，本例是在每次反覆迴圈時叫用初始化程序。 在多執行緒案例中，第一個叫用初始化程序的執行緒，其值會被所有執行緒看到。 後續其他執行緒也會叫用初始化程序，但其結果不被採用。 如果無法接受這種潛在的競爭條件，請使用採用布林值引數和同步處理物件的 <xref:System.Threading.LazyInitializer.EnsureInitialized%2A?displayProperty=fullName> 多載。  
  
## <a name="see-also"></a>另請參閱  
 [Managed 執行緒處理的基本概念](../../../docs/standard/threading/managed-threading-basics.md)   
 [執行緒和執行緒處理](../../../docs/standard/threading/threads-and-threading.md)   
 [工作平行程式庫 (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)   
 [如何：執行物件的延遲初始化](../../../docs/framework/performance/how-to-perform-lazy-initialization-of-objects.md)

