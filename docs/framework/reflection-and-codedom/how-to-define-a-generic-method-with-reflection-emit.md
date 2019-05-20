---
title: 作法：使用反映發出定義泛型方法
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generics [.NET Framework], reflection emit
- reflection emit, generic methods
- generics [.NET Framework], dynamic types
ms.assetid: 93892fa4-90b3-4ec4-b147-4bec9880de2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2bf8610a1e2ad11d12acd55c69fbb98d078f7cc9
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586154"
---
# <a name="how-to-define-a-generic-method-with-reflection-emit"></a>作法：使用反映發出定義泛型方法
第一個程序示範如何建立有兩個類型參數的簡單泛型方法，以及如何將類別條件約束、介面條件約束和特殊條件約束套用至類型參數。  
  
 第二個程序示範如何發出方法主體，以及如何使用泛型方法的類型參數建立泛型型別的執行個體並呼叫其方法。  
  
 第三個程序示範如何叫用泛型方法。  
  
> [!IMPORTANT]
>  方法不是只因為屬於泛型型別並使用該類型的類型參數，而成為泛型。 方法只有在有自己的類型參數清單時，才會是泛型。 泛型方法可以出現在非泛型型別中，如本例所示。 如需泛型型別的非泛型方法範例，請參閱[如何：使用反映發出定義泛型型別](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)。  
  
### <a name="to-define-a-generic-method"></a>定義泛型方法  
  
1. 開始之前，最好先查看使用高階語言撰寫時的泛型方法顯示方式。 下列程式碼和呼叫泛型方法的程式碼一起包含在本主題的範例程式碼中。 方法有兩個類型參數 `TInput`和`TOutput`，第二個必須是參考型別 (`class`)，必須有無參數建構函式 (`new`)，且必須實作 `ICollection(Of TInput)` (C# 為 `ICollection<TInput>`)。 此介面條件約束確保 <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> 方法可用來將項目新增至該方法所建立的 `TOutput` 集合。 方法具有一個型式參數 `input`，這是一個 `TInput` 陣列。 此方法會建立類型 `TOutput` 的集合，並將 `input` 的項目複製至集合。  
  
     [!code-csharp[GenericMethodHowTo#20](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#20)]
     [!code-vb[GenericMethodHowTo#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#20)]  
  
2. 定義動態組件和動態模組，以包含泛型方法所屬的類型。 在此情況下，組件僅有一個模組，名為 `DemoMethodBuilder1`，而且模組名稱是組件名稱加上副檔名。 在本例中，組件儲存到磁碟並執行，因此指定了 <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndSave?displayProperty=nameWithType>。 您可以使用 [Ildasm.exe (IL 反組譯工具)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 檢查 DemoMethodBuilder1.dll，並比較它和 Microsoft 中繼語言 (MSIL) 在步驟 1 中顯示的方法。  
  
     [!code-csharp[GenericMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#2)]
     [!code-vb[GenericMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#2)]  
  
3. 定義泛型方法所屬的類型。 類型不必是泛型。 泛型方法可以屬於泛型或非泛型型別。 在本例中，類型是類別、不是泛型，且名為 `DemoType`。  
  
     [!code-csharp[GenericMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#3)]
     [!code-vb[GenericMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#3)]  
  
4. 定義泛型方法。 如果泛型方法的型式參數類型是由泛型方法的泛型型別參數所指定，請使用 <xref:System.Reflection.Emit.TypeBuilder.DefineMethod%28System.String%2CSystem.Reflection.MethodAttributes%29> 方法多載來定義方法。 方法的泛型型別參數尚未定義，因此您無法在對 <xref:System.Reflection.Emit.TypeBuilder.DefineMethod%2A> 的呼叫中指定方法的型式參數類型。 在本例中，方法名為 `Factory`。 方法是公用且 `static` (Visual Basic 為 `Shared`)。  
  
     [!code-csharp[GenericMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#4)]
     [!code-vb[GenericMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#4)]  
  
5. 將包含參數名稱的字串陣列傳遞至 <xref:System.Reflection.Emit.MethodBuilder.DefineGenericParameters%2A?displayProperty=nameWithType> 方法，以定義 `DemoMethod` 的泛型型別參數。 這會讓方法成為泛型方法。 下列程式碼使 `Factory` 成為具有類型參數 `TInput` 和 `TOutput` 的泛型方法。 為更方便閱讀程式碼，會建立有這些名稱的變數以保留代表兩個類型參數的 <xref:System.Reflection.Emit.GenericTypeParameterBuilder> 物件。  
  
     [!code-csharp[GenericMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#5)]
     [!code-vb[GenericMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#5)]  
  
6. 或者將特殊條件約束新增至類型參數。 使用 <xref:System.Reflection.Emit.GenericTypeParameterBuilder.SetGenericParameterAttributes%2A> 方法新增特殊條件約束。 在本例中，`TOutput` 受限為參考型別，且具有無參數建構函式。  
  
     [!code-csharp[GenericMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#6)]
     [!code-vb[GenericMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#6)]  
  
7. 或者將類別和介面條件約束新增至類型參數。 在本例中，類型參數 `TOutput` 受限為實作 `ICollection(Of TInput)` (C# 為 `ICollection<TInput>`) 介面的類型。 這會確保 <xref:System.Collections.Generic.ICollection%601.Add%2A> 方法可用來新增項目。  
  
     [!code-csharp[GenericMethodHowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#7)]
     [!code-vb[GenericMethodHowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#7)]  
  
8. 使用 <xref:System.Reflection.Emit.MethodBuilder.SetParameters%2A> 方法定義方法的型式參數。 在本例中，`Factory` 方法有一個參數，是 `TInput` 的陣列。 此類型是透過對代表 `TInput` 的 <xref:System.Reflection.Emit.GenericTypeParameterBuilder> 呼叫 <xref:System.Type.MakeArrayType%2A> 方法所建立。 <xref:System.Reflection.Emit.MethodBuilder.SetParameters%2A> 的引數是 <xref:System.Type> 物件的陣列。  
  
     [!code-csharp[GenericMethodHowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#8)]
     [!code-vb[GenericMethodHowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#8)]  
  
9. 使用 <xref:System.Reflection.Emit.MethodBuilder.SetReturnType%2A> 方法定義方法的傳回類型。 在本例中，會傳回 `TOutput` 的執行個體。  
  
     [!code-csharp[GenericMethodHowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#9)]
     [!code-vb[GenericMethodHowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#9)]  
  
10. 使用 <xref:System.Reflection.Emit.ILGenerator> 發出方法主體。 如需詳細資訊，請參閱發出方法主體所伴隨的程序。  
  
    > [!IMPORTANT]
    >  當您向泛型型別的方法發出呼叫，而這些類型的類型引數是泛型方法的類型參數時，您必須使用 <xref:System.Reflection.Emit.TypeBuilder> 類別的 `static`<xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29>、<xref:System.Reflection.Emit.TypeBuilder.GetMethod%28System.Type%2CSystem.Reflection.MethodInfo%29> 和 <xref:System.Reflection.Emit.TypeBuilder.GetField%28System.Type%2CSystem.Reflection.FieldInfo%29> 方法多載取得方法的建構形式。 發出方法主體的伴隨程序會示範此作業。  
  
11. 完成包含方法的類型，並儲存組件。 叫用泛型方法伴隨的程序將示範叫用此完成的方法的兩種方式。  
  
     [!code-csharp[GenericMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#14)]
     [!code-vb[GenericMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#14)]  
  
<a name="procedureSection1"></a>   
### <a name="to-emit-the-method-body"></a>發出方法主體  
  
1. 取得程式碼產生器，並宣告區域變數和標籤。 宣告區域變數是使用 <xref:System.Reflection.Emit.ILGenerator.DeclareLocal%2A> 方法。 `Factory` 方法有四個區域變數︰`retVal` 保留方法傳回的新 `TOutput`，`ic` 在投射到 `ICollection(Of TInput)` 時保留 `TOutput` (C# 為`ICollection<TInput>`)，`input` 保留 `TInput` 物件的輸入陣列，而 `index` 則逐一查看陣列。 此方法也有兩個標籤，一個是進入迴圈 (`enterLoop`)，另一個用於迴圈的頂端 (`loopAgain`)，使用 <xref:System.Reflection.Emit.ILGenerator.DefineLabel%2A> 方法所定義。  
  
     此方法做的第一件事是使用 <xref:System.Reflection.Emit.OpCodes.Ldarg_0> 作業碼載入其引數，並使用 <xref:System.Reflection.Emit.OpCodes.Stloc_S> 作業碼將它儲存在區域變數 `input` 中。  
  
     [!code-csharp[GenericMethodHowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#10)]
     [!code-vb[GenericMethodHowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#10)]  
  
2. 使用 <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> 方法的泛型方法多載，發出程式碼以建立 `TOutput` 的執行個體。 指定的類型需要有無參數建構函式才能使用此多載，這是在 `TOutput` 新增該條件約束的原因。 將 `TOutput` 傳遞到 <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>，以建立建構的泛型方法。 發出程式碼以呼叫方法後，再使用 <xref:System.Reflection.Emit.OpCodes.Stloc_S> 發出程式碼將它儲存在區域變數 `retVal` 中。  
  
     [!code-csharp[GenericMethodHowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#11)]
     [!code-vb[GenericMethodHowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#11)]  
  
3. 發出程式碼將新的 `TOutput` 物件投射成 `ICollection(Of TInput)`，並將它儲存在區域變數 `ic` 中。  
  
     [!code-csharp[GenericMethodHowTo#31](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#31)]
     [!code-vb[GenericMethodHowTo#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#31)]  
  
4. 取得代表 <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> 方法的 <xref:System.Reflection.MethodInfo>。 方法作用於 `ICollection(Of TInput)` (C# 為 `ICollection<TInput>`)，因此有必要取得專門針對該建構類型的 `Add` 方法。 您不能使用 <xref:System.Type.GetMethod%2A> 方法直接從 `icollOfTInput` 取得此 <xref:System.Reflection.MethodInfo>，因為已使用 <xref:System.Reflection.Emit.GenericTypeParameterBuilder> 建構的類型不支援 <xref:System.Type.GetMethod%2A>。 請改呼叫 `icoll` 的 <xref:System.Type.GetMethod%2A>，它包含 <xref:System.Collections.Generic.ICollection%601> 泛型介面的泛型型別定義。 然後使用 <xref:System.Reflection.Emit.TypeBuilder.GetMethod%28System.Type%2CSystem.Reflection.MethodInfo%29>`static` 方法產生建構類型的 <xref:System.Reflection.MethodInfo>。 下列程式碼可示範這項處理。  
  
     [!code-csharp[GenericMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#12)]
     [!code-vb[GenericMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#12)]  
  
5. 載入 32 位元的整數 0 並將其儲存在變數中，以發出程式碼來初始化 `index` 變數。 發出程式碼以分支到標籤 `enterLoop`。 此標籤尚未標示，因為它是在迴圈內。 下個步驟會發出此迴圈的程式碼。  
  
     [!code-csharp[GenericMethodHowTo#32](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#32)]
     [!code-vb[GenericMethodHowTo#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#32)]  
  
6. 發出此迴圈的程式碼。 第一個步驟是呼叫有 `loopAgain` 標籤的 <xref:System.Reflection.Emit.ILGenerator.MarkLabel%2A>，來標記迴圈頂端。 使用標籤的分支陳述式現在會分支到程式碼的這個點。 下個步驟推送 `TOutput` 物件、投射到 `ICollection(Of TInput)`，再到堆疊。 它不是立即需要，但要就位以待呼叫 `Add` 方法。 接下來，將輸入陣列推送至堆疊，再將包含目前索引的 `index` 變數推送至陣列。 <xref:System.Reflection.Emit.OpCodes.Ldelem> 作業碼會從堆疊取出索引和陣列，並將索引的陣列項目推送至堆疊。 堆疊已就緒可呼叫 <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> 方法，它會從堆疊取出集合和新的項目，並將項目新增至集合。  
  
     迴圈中其餘的程式碼會遞增索引，並測試看迴圈是否已結束：索引和 32 位元整數 1 會推送到堆疊並相加，將總和留在堆疊上，總和會儲存在 `index` 中。 呼叫 <xref:System.Reflection.Emit.ILGenerator.MarkLabel%2A> 以將此點設定為迴圈的進入點。 再次載入索引。 輸入陣列會推送到堆疊，並發出 <xref:System.Reflection.Emit.OpCodes.Ldlen> 取得其長度。 索引和長度現在都在堆疊上，而 <xref:System.Reflection.Emit.OpCodes.Clt> 會發出以比較兩者。 如果索引小於長度，<xref:System.Reflection.Emit.OpCodes.Brtrue_S> 就會分支回到迴圈的開頭。  
  
     [!code-csharp[GenericMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#13)]
     [!code-vb[GenericMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#13)]  
  
7. 發出程式碼將 `TOutput` 物件推送至堆疊，並從方法傳回。 區域變數 `retVal` 和 `ic` 同時包含新 `TOutput` 的參考；`ic` 僅用於存取 <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> 方法。  
  
     [!code-csharp[GenericMethodHowTo#33](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#33)]
     [!code-vb[GenericMethodHowTo#33](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#33)]  
  
<a name="procedureSection2"></a>   
### <a name="to-invoke-the-generic-method"></a>叫用泛型方法。  
  
1. `Factory` 是泛型方法定義。 為叫用它，您必須將類型指派給其泛型型別參數。 請使用 <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> 方法完成此作業。 下列程式碼會建立建構泛型方法，為 `TInput` 指定 <xref:System.String>，為 `TOutput` 指定 `List(Of String)` (C# 為 `List<string>`)，並顯示代表方法的字串。  
  
     [!code-csharp[GenericMethodHowTo#21](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#21)]
     [!code-vb[GenericMethodHowTo#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#21)]  
  
2. 若要叫用晚期繫結方法，請使用 <xref:System.Reflection.MethodBase.Invoke%2A> 方法。 下列程式碼會建立 <xref:System.Object> 的陣列，將其唯一項目包含為字串陣列，並將其當成泛型方法的引數清單傳遞。 <xref:System.Reflection.MethodBase.Invoke%2A> 的第一個參數為 Null 參考，因為方法是 `static`。 傳回值會投射到 `List(Of String)`，並顯示其第一個項目。  
  
     [!code-csharp[GenericMethodHowTo#22](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#22)]
     [!code-vb[GenericMethodHowTo#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#22)]  
  
3. 若要使用委派叫用方法，您必須有符合建構泛型方法簽章的委派。 執行此作業的簡單方法是建立泛型委派。 下列程式碼會使用 <xref:System.Delegate.CreateDelegate%28System.Type%2CSystem.Reflection.MethodInfo%29?displayProperty=nameWithType> 方法多載建立在範例程式碼中定義之泛型委派 `D` 的執行個體，並叫用委派。 委派執行優於晚期繫結呼叫。  
  
     [!code-csharp[GenericMethodHowTo#23](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#23)]
     [!code-vb[GenericMethodHowTo#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#23)]  
  
4. 您也可以從指向已儲存組件的程式呼叫發出的方法。  
  
## <a name="example"></a>範例  
 下列程式碼範例會建立具有泛型方法 `Factory` 的非泛型型別 `DemoType`。 此方法有兩個泛型型別參數：`TInput` 指定輸入類型，而 `TOutput` 指定輸出類型。 `TOutput` 類型參數受限實作 `ICollection<TInput>` (Visual Basic 為 `ICollection(Of TInput)`)、為參考型別，且具有無參數建構函式。  
  
 方法具有一個型式參數，這是一個 `TInput` 陣列。 此方法會傳回 `TOutput` 的執行個體，包含該輸入陣列的所有項目。 `TOutput` 可以是任何實作 <xref:System.Collections.Generic.ICollection%601> 泛型介面的泛型集合類型。  
  
 執行程式碼時，動態組件會儲存為 DemoGenericMethod1.dll，以及可以使用檢查[Ildasm.exe （IL 反組譯工具）](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)。  
  
> [!NOTE]
>  若要瞭解如何發出程式碼的好方法是撰寫執行的工作，您嘗試發出，並可用於檢查編譯器所產生的 MSIL 反組譯工具的 Visual Basic、 C# 或 Visual c + + 程式。  
  
 程式碼範例包含相當於發出的方法的原始程式碼。 發出的方法會叫用晚期繫結，也使用泛型委派宣告在程式碼範例。  
  
 [!code-csharp[GenericMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#1)]
 [!code-vb[GenericMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Reflection.Emit.MethodBuilder>
- [如何：使用反映發出定義泛型型別](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)
