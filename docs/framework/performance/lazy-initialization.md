---
title: "延遲初始設定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET 中的延遲初始設定, 簡介"
ms.assetid: 56b4ae5c-4745-44ff-ad78-ffe4fcde6b9b
caps.latest.revision: 22
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 20
---
# 延遲初始設定
物件的「*延遲初始設定*」\(Lazy Initialization\) 表示物件的建立會延後到第一次使用為止 \(在本主題中，「*延遲初始設定*」\(Lazy Initialization\) 和「*延遲執行個體化*」\(Lazy Instantiation\) 是同義詞\)。延遲初始設定主要用於改善效能、避免浪費計算以及降低程式記憶體需求。  下面是最常見的案例：  
  
-   當您擁有高度耗費資源才能建立的物件，而且程式可能不會使用此物件時。  例如，假設您在記憶體中擁有一個 `Customer` 物件，而這個物件具有 `Orders` 屬性，其中包含需要資料庫連接才能初始化之 `Order` 物件的大型陣列。  如果使用者永遠不要求顯示 Orders 或在計算中使用這項資料，就沒有任何理由要使用系統記憶體或計算循環來建立它。  只要使用 `Lazy<Orders>`，將 `Orders` 物件宣告為延遲初始設定，您就可以避免在不使用此物件時浪費系統資源。  
  
-   當您擁有高度耗費資源才能建立的物件，而且想要延後物件的建立，直到其他高度耗費資源的作業完成為止時。  例如，假設您的程式在啟動時會載入許多物件執行個體，但是只立即需要使用其中部分執行個體。  您可以透過延後初始設定非必要的物件，直到建立必要的物件為止，改善程式的啟動效能。  
  
 雖然您可以撰寫自訂程式碼來執行延遲初始設定，不過我們建議您改用 <xref:System.Lazy%601>。  <xref:System.Lazy%601> 及其相關的型別也支援執行緒安全性而且可提供一致的例外狀況傳播原則。  
  
 下表列出 .NET Framework 4 版所提供的型別，可讓您在不同的案例中啟用延遲初始設定。  
  
|類型|說明|  
|--------|--------|  
|<xref:System.Lazy%601>|可針對任何類別庫和使用者定義型別提供延遲初始設定語意的包裝函式類別。|  
|<xref:System.Threading.ThreadLocal%601>|與 <xref:System.Lazy%601> 很相似，不過它會以執行緒區域的方式提供延遲初始設定語意。  每個執行緒都可以存取它自己的唯一值。|  
|<xref:System.Threading.LazyInitializer>|提供進階的 `static` \(Visual Basic 中的 `Shared`\) 方法，可延遲初始設定物件而不會產生類別的額外負荷。|  
  
## 基本延遲初始設定  
 若要定義延遲初始化型別 \(例如 `MyType`\)，請使用 `Lazy<MyType>` \(Visual Basic 中的 `Lazy(Of MyType)`\)，如下列範例所示。  如果沒有任何委派傳入 <xref:System.Lazy%601> 建構函式，第一次存取 value 屬性時，就會使用 <xref:System.Activator.CreateInstance%2A?displayProperty=fullName> 來建立包裝型別。  如果此型別沒有預設建構函式，就會擲回執行階段例外狀況。  
  
 在下列範例中，假設 `Orders` 是一個類別，其中包含擷取自資料庫的 `Order` 物件陣列。  `Customer` 物件包含 `Orders` 的執行個體，但是根據使用者動作，可能不需要使用來自 `Orders` 物件的資料。  
  
 [!code-csharp[Lazy#1](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#1)]
 [!code-vb[Lazy#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#1)]  
  
 您也可以將委派傳入 <xref:System.Lazy%601> 建構函式，以便在建立時針對包裝型別叫用特定建構函式多載，並且執行任何其他必要的初始設定步驟，如下列範例所示。  
  
 [!code-csharp[Lazy#2](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#2)]
 [!code-vb[Lazy#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#2)]  
  
 建立延遲物件之後，在第一次存取延遲變數的 <xref:System.Lazy%601.Value%2A> 屬性之前，不會建立任何 `Orders` 的執行個體。  第一次存取時，系統會建立並傳回包裝型別，並且儲存供未來的存取使用。  
  
 [!code-csharp[Lazy#3](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#3)]
 [!code-vb[Lazy#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#3)]  
  
 <xref:System.Lazy%601> 物件一定會傳回用來初始化此物件的相同物件或值。  因此，<xref:System.Lazy%601.Value%2A> 屬性是唯讀的。  如果 <xref:System.Lazy%601.Value%2A> 儲存了參考型別，您就無法指派新的物件給它 \(不過，您可以變更其可設定之公用欄位和屬性的值\)。如果 <xref:System.Lazy%601.Value%2A> 儲存了實值型別，您就無法修改其值。  儘管如此，您還是可以使用新的引數來再次叫用變數建構函式，藉以建立新的變數。  
  
 [!code-csharp[Lazy#4](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#4)]
 [!code-vb[Lazy#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#4)]  
  
 新的延遲執行個體 \(與先前的執行個體一樣\) 要等到第一次存取 <xref:System.Lazy%601.Value%2A> 屬性之後，才會執行個體化 `Orders`。  
  
### 安全執行緒初始設定  
 根據預設，<xref:System.Lazy%601> 物件具備執行緒安全。  也就是說，如果建構函式沒有指定執行緒安全性的種類，它所建立的 <xref:System.Lazy%601> 物件就會具備執行緒安全。  在多執行緒案例中，存取具備執行緒安全的<xref:System.Lazy%601> 物件之 <xref:System.Lazy%601.Value%2A> 屬性的第一個執行緒會為所有執行緒的後續存取初始化此屬性，而且所有執行緒都會共用相同的資料。  因此，哪個執行緒初始化此物件並不重要，而且競爭情形是良性的。  
  
> [!NOTE]
>  您可以使用例外狀況快取將此一致性擴充至錯誤條件。  如需詳細資訊，請參閱下一節中[延遲物件的例外狀況](../../../docs/framework/performance/lazy-initialization.md#ExceptionsInLazyObjects)。  
  
 下列範例顯示相同 `Lazy<int>` 執行個體的三個個別執行緒都具有相同的值。  
  
 [!code-csharp[Lazy#8](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#8)]
 [!code-vb[Lazy#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#8)]  
  
 如果您需要讓每個執行緒具有不同的資料，請使用 <xref:System.Threading.ThreadLocal%601> 型別，如本主題後面所述。  
  
 某些 <xref:System.Lazy%601> 建構函式具有名為 `isThreadSafe` 的布林值參數，可用來指定是否要從多個執行緒存取 <xref:System.Lazy%601.Value%2A> 屬性。  如果您只要從單一執行緒存取此屬性，請傳入 `false` 以便取得適度的效能優勢。  如果您要從多個執行緒存取此屬性，請傳入 `true`，以便指示 <xref:System.Lazy%601> 執行個體正確處理單一執行緒在初始設定時擲回例外狀況的競爭情形。  
  
 某些 <xref:System.Lazy%601> 建構函式具有名為 `mode` 的 <xref:System.Threading.LazyThreadSafetyMode> 參數。  這些建構函式會提供其他執行緒安全性模式。  下表將顯示指定執行緒安全性的建構函式參數如何影響 <xref:System.Lazy%601> 物件的執行緒安全性。  每個建構函式最多只有一個這類參數。  
  
|物件的執行緒安全性|`LazyThreadSafetyMode` `mode` 參數|`isThreadSafe` 布林值參數|沒有執行緒安全性參數|  
|---------------|--------------------------------------|--------------------------|----------------|  
|具備完整執行緒安全。一次只有一個執行緒會嘗試初始化此值。|<xref:System.Threading.LazyThreadSafetyMode>|`true`|可以。|  
|不具備執行緒安全。|<xref:System.Threading.LazyThreadSafetyMode>|`false`|不適用。|  
|具備完整執行緒安全。執行緒會彼此競爭以初始化此值。|<xref:System.Threading.LazyThreadSafetyMode>|不適用。|不適用。|  
  
 如上表所示，針對 `mode` 參數指定 <xref:System.Threading.LazyThreadSafetyMode?displayProperty=fullName> 與針對 `isThreadSafe` 參數指定 `true` 相同，而且指定 <xref:System.Threading.LazyThreadSafetyMode?displayProperty=fullName> 與指定 `false` 相同。  
  
 指定 <xref:System.Threading.LazyThreadSafetyMode?displayProperty=fullName> 會允許多個執行緒嘗試初始化 <xref:System.Lazy%601> 執行個體。  只有一個執行緒會贏得此競爭，而且所有其他執行緒都會接收成功執行緒所初始化的值。  如果某個執行緒在初始化期間擲回例外狀況，該執行緒就不會接收成功執行緒所設定的值。  由於系統不會快取例外狀況，因此後續嘗試存取 <xref:System.Lazy%601.Value%2A> 屬性的行為可能會產生成功的初始設定。  這與其他模式處理例外狀況的方式不同，下一節將說明這點。  如需詳細資訊，請參閱 <xref:System.Threading.LazyThreadSafetyMode> 列舉。  
  
<a name="ExceptionsInLazyObjects"></a>   
## 延遲物件的例外狀況  
 如先前所述，<xref:System.Lazy%601> 物件一定會傳回用來初始化此物件的相同物件或值，因此 <xref:System.Lazy%601.Value%2A> 屬性是唯讀的。  如果您啟用例外狀況快取，這種不變性也會擴充至例外狀況行為。  第一次存取 <xref:System.Lazy%601.Value%2A> 屬性時，如果鬆散 \(Lazy\) 初始化的物件已啟用例外狀況快取，而且從其初始設定方法擲回例外狀況，則之後每次嘗試存取 <xref:System.Lazy%601.Value%2A> 屬性時，都會擲回相同的例外狀況。  換言之，系統永遠不會重新叫用包裝型別的建構函式，即使在多執行緒案例中也一樣。  因此，<xref:System.Lazy%601> 物件無法在某次存取時擲回例外狀況，而在後續存取時傳回值。  
  
 當您使用採取初始設定方法 \(`valueFactory` 參數\) 的任何 <xref:System.Lazy%601?displayProperty=fullName> 建構函式時，例外狀況快取便會啟用。例如，當您使用 `Lazy(T)(Func(T))` 建構函式時，它就會啟用。  如果建構函式同時採用 <xref:System.Threading.LazyThreadSafetyMode> 值 \(`mode` 參數\)，請指定 <xref:System.Threading.LazyThreadSafetyMode?displayProperty=fullName> 或 <xref:System.Threading.LazyThreadSafetyMode?displayProperty=fullName>。  指定初始設定方法會啟用這兩種模式的例外狀況快取。  初始設定方法可能非常簡單。  例如，這種方法可能會呼叫 `T` 的預設建構函式：`new Lazy<Contents>(() => new Contents(), mode)` \(在 C\# 中\) 或 `New Lazy(Of Contents)(Function() New Contents())` \(在 Visual Basic 中\)。  如果您使用未指定初始設定方法的 <xref:System.Lazy%601?displayProperty=fullName> 建構函式，則不會快取 `T` 的預設建構函式擲回的例外狀況。  如需詳細資訊，請參閱 <xref:System.Threading.LazyThreadSafetyMode> 列舉。  
  
> [!NOTE]
>  如果您建立 <xref:System.Lazy%601> 物件，且其中 `isThreadSafe` 建構函式參數設為 `false` 或 `mode` 建構函式參數設為 <xref:System.Threading.LazyThreadSafetyMode?displayProperty=fullName>，則必須從單一執行緒存取 <xref:System.Lazy%601> 物件，或是提供自己的同步處理。  這會套用到物件的所有方面，包括例外狀況快取。  
  
 如上一節所述，透過指定 <xref:System.Threading.LazyThreadSafetyMode?displayProperty=fullName> 所建立的 <xref:System.Lazy%601> 物件會以不同方式處理例外狀況。  使用 <xref:System.Threading.LazyThreadSafetyMode> 時，多個執行緒可能會彼此競爭以初始化 <xref:System.Lazy%601> 執行個體。  在這種情況下，系統不會快取例外狀況，而且嘗試存取 <xref:System.Lazy%601.Value%2A> 屬性的行為可能會繼續直到初始設定成功為止。  
  
 下表摘要說明 <xref:System.Lazy%601> 建構函式控制例外狀況快取的方式。  
  
|建構函式|執行緒安全模式|使用初始設定方法|已快取例外狀況|  
|----------|-------------|--------------|-------------|  
|Lazy\(T\)\(\)|\(<xref:> System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?qualifyHint=False&autoUpgrade=True\)|沒有|沒有|  
|Lazy\(T\)\(Func\(T\)\)|\(<xref:> System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?qualifyHint=False&autoUpgrade=True\)|有|有|  
|Lazy\(T\)\(Boolean\)|`True` \(<xref:> System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?qualifyHint=False&autoUpgrade=True\) 或 `false` \(<xref:> System.Threading.LazyThreadSafetyMode.None?qualifyHint=False&autoUpgrade=True\)|沒有|沒有|  
|Lazy\(T\)\(Func\(T\), Boolean\)|`True` \(<xref:> System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?qualifyHint=False&autoUpgrade=True\) 或 `false` \(<xref:> System.Threading.LazyThreadSafetyMode.None?qualifyHint=False&autoUpgrade=True\)|有|有|  
|Lazy\(T\)\(LazyThreadSafetyMode\)|使用者指定|沒有|沒有|  
|Lazy\(T\)\(Func\(T\), LazyThreadSafetyMode\)|使用者指定|有|如果使用者指定 <xref:> System.Threading.LazyThreadSafetyMode.PublicationOnly?qualifyHint=False&autoUpgrade=True，則為否，否則為是。|  
  
## 實作延遲初始化屬性  
 若要使用延遲初始設定來實作公用屬性，請將此屬性的支援欄位定義成 <xref:System.Lazy%601>，並且從此屬性的 `get` 存取子傳回 <xref:System.Lazy%601.Value%2A> 屬性。  
  
 [!code-csharp[Lazy#5](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#5)]
 [!code-vb[Lazy#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#5)]  
  
 <xref:System.Lazy%601.Value%2A> 屬性是唯讀的。因此，公開此屬性的屬性沒有任何 `set` 存取子。  如果您需要 <xref:System.Lazy%601> 物件所支援的讀取\/寫入屬性，`set` 存取子就必須建立新的 <xref:System.Lazy%601> 物件，並將它指派給備份存放區。  `set` 存取子必須建立可傳回傳遞給 `set` 存取子之新屬性值的 Lambda 運算式，並且將該 Lambda 運算式傳遞給新 <xref:System.Lazy%601> 物件的建構函式。  <xref:System.Lazy%601.Value%2A> 屬性的下一次存取將會導致新 <xref:System.Lazy%601> 的初始設定，而且其 <xref:System.Lazy%601.Value%2A> 屬性將因而傳回指派給此屬性的新值。  進行這種迂迴排列的原因是要保留 <xref:System.Lazy%601> 內建的多執行緒保護。  否則，屬性存取子就必須快取 <xref:System.Lazy%601.Value%2A> 屬性所傳回的第一個值並且僅修改快取的值，而且您必須撰寫自訂執行緒安全程式碼來進行該作業。  由於 <xref:System.Lazy%601> 物件所支援的讀取\/寫入屬性需要其他初始設定，所以您可能無法接受其效能。  此外，根據特定案例，可能需要進行其他協調，才能避免 Setter 與 Getter 之間的競爭情形。  
  
## 執行緒區域延遲初始設定  
 在某些多執行緒案例中，您可能想要提供自訂私用資料給每個執行緒。  這類資料稱為「*執行緒區域資料*」\(Thread\-Local Data\)。  在 .NET Framework 3.5 版和先前的版本中，您可以將 `ThreadStatic` 屬性套用至靜態變數，讓它成為執行緒區域變數。  不過，使用 `ThreadStatic` 屬性可能會導致小錯誤。  例如，甚至是基本初始設定陳述式也會導致此變數只在存取它的第一個執行緒上初始化，如下列範例所示。  
  
 [!code-csharp[Lazy#6](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#6)]
 [!code-vb[Lazy#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#6)]  
  
 在所有其他執行緒上，此變數將使用其預設值 \(零\) 初始化。  不過，在 .NET Framework 4 版中，您可以使用 <xref:System.Threading.ThreadLocal%601?displayProperty=fullName> 型別來建立以執行個體為基礎的執行緒區域變數，而您所提供的 <xref:System.Action%601> 委派會在所有執行緒上初始化此變數。  在下列範例中，存取 `counter` 的所有執行緒會將其起始值視為 1。  
  
 [!code-csharp[Lazy#7](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#7)]
 [!code-vb[Lazy#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#7)]  
  
 <xref:System.Threading.ThreadLocal%601> 包裝其物件的方式與 <xref:System.Lazy%601> 很相似，不過具有下列基本差異：  
  
-   每個執行緒都會使用無法從其他執行緒存取的自訂私用資料來初始化執行緒區域變數。  
  
-   <xref:System.Threading.ThreadLocal%601.Value%2A?displayProperty=fullName> 屬性是可讀寫的，而且修改次數不受限制。  這可能會影響例外狀況傳播。例如，某個 `get` 作業可能會引發例外狀況，而下一個作業可能會成功初始化此值。  
  
-   如果沒有提供任何初始設定委派，<xref:System.Threading.ThreadLocal%601> 就會使用此型別的預設值來初始化其包裝型別。  就這點而言，<xref:System.Threading.ThreadLocal%601> 與 <xref:System.ThreadStaticAttribute> 屬性一致。  
  
 下列範例示範存取 `ThreadLocal<int>` 執行個體的每個執行緒都會取得資料的自訂唯一複本。  
  
 [!code-csharp[Lazy#9](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#9)]
 [!code-vb[Lazy#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#9)]  
  
## Parallel.For 和 ForEach 中的執行緒區域變數  
 當您使用 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName> 方法或 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> 方法，以平行方式逐一查看資料來源時，就可以使用內建支援執行緒區域資料的多載。  在這些方法中，執行緒區域性是使用區域委派來建立、存取和清除資料而達成。  如需詳細資訊，請參閱[How to: Write a Parallel.For Loop with Thread\-Local Variables](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)與[How to: Write a Parallel.ForEach Loop with Thread\-Local Variables](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-thread-local-variables.md)。  
  
## 針對低額外負荷案例使用延遲初始設定  
 在您必須延遲初始化大量物件的案例中，可能會決定在 <xref:System.Lazy%601> 中包裝每個物件需要使用過多記憶體或過多運算資源。  或者，您可能會有關於如何公開延遲初始設定的需求。  在這類情況下，您可以使用 <xref:System.Threading.LazyInitializer?displayProperty=fullName> 類別的 `static` \(Visual Basic 中的 `Shared`\) 方法來延遲初始化每個物件，而不需要在 <xref:System.Lazy%601> 的執行個體中包裝物件。  
  
 在下列範例中，假設您已經延遲初始化個別 `Order` 物件 \(只在需要時\)，而非將整個 `Orders` 物件包裝在單一 <xref:System.Lazy%601> 物件中。  
  
 [!code-csharp[Lazy#10](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#10)]
 [!code-vb[Lazy#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#10)]  
  
 在此範例中，請注意，系統會在每次反覆運算迴圈時叫用初始設定程序。  在多執行緒案例中，叫用初始設定程序的第一個執行緒就是所有執行緒都會查看其值的執行緒。  雖然後續執行緒也會叫用初始設定程序，不過卻不會使用其結果。  如果您無法接受這種可能的競爭情形，請使用採用布林值引數和同步處理物件的 <xref:System.Threading.LazyInitializer.EnsureInitialized%2A?displayProperty=fullName> 多載。  
  
## 請參閱  
 [Managed Threading Basics](../../../docs/standard/threading/managed-threading-basics.md)   
 [Threads and Threading](../../../docs/standard/threading/threads-and-threading.md)   
 [Task Parallel Library \(TPL\)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)   
 [如何：執行物件的延遲初始化](../../../docs/framework/performance/how-to-perform-lazy-initialization-of-objects.md)