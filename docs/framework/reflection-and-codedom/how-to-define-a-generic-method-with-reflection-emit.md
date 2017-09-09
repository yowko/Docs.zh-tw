---
title: "如何：使用反映發出定義泛型方法 | Microsoft Docs"
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
  - "泛型 [.NET Framework], 動態類型"
  - "泛型 [.NET Framework], 反映發出"
  - "反映發出, 泛型方法"
ms.assetid: 93892fa4-90b3-4ec4-b147-4bec9880de2b
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：使用反映發出定義泛型方法
第一個程序是示範如何建立具有兩個型別參數的簡單泛型方法，以及如何套用類別條件約束、介面條件約束及型別參數的特殊條件約束。  
  
 第二個程序是示範如何發出方法主體，以及如何使用泛型方法的型別參數來建立泛型型別的執行個體以及呼叫其方法。  
  
 第三個程序將示範如何叫用泛型方法。  
  
> [!IMPORTANT]
>  方法不會只因為它屬於泛型型別及使用該型別的型別參數，就會是泛型；  只有在方法有它自己的型別參數清單時，才會是泛型。  泛型方法可以出現在非泛型型別上，如這個範例所示。  如需泛型型別上的非泛型方法的範例，請參閱 [如何：使用反映發出定義泛型類型](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)。  
  
### 若要定義泛型方法  
  
1.  在開始之前，當使用高階語言編寫時，查看泛型方法出現的方式會很有幫助。  下列程式碼會包含在這個主題的範例程式碼中，連同呼叫泛型方法的程式碼。  此方法有兩個型別參數 `TInput` 和 `TOutput`，第二個參數必須是參考型別 \(`class`\)、必須有無參數的建構函式 \(`new`\)，也必須實作 `ICollection(Of TInput)` \(C\# 中為 `ICollection<TInput>`\)。  此介面條件約束可確保 <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=fullName> 方法可用來將項目將入到方法所建立的 `TOutput` 集合中。  此方法有一個型式參數 `input`，它是 `TInput` 的陣列。  此方法會建立 `TOutput` 型別的集合，並將 `input` 的項目複製到此集合中。  
  
     [!code-csharp[GenericMethodHowTo#20](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#20)]
     [!code-vb[GenericMethodHowTo#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#20)]  
  
2.  定義動態組件和動態模組，以包含泛型方法所屬的型別。  在此情況下，此組件只有一個模組 \(名為 `DemoMethodBuilder1`\)，而此模組名稱與組件名稱相同，再加上副檔名。  在此範例中，會將此組件儲存到磁碟上並執行它，所以指定了 <xref:System.Reflection.Emit.AssemblyBuilderAccess?displayProperty=fullName>。  您可以使用 [Ildasm.exe \(IL Disassembler\)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 來檢查 DemoMethodBuilder1.dll，並將它與步驟 1 的方法之 Microsoft intermediate language \(MSIL\) 相比較。  
  
     [!code-csharp[GenericMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#2)]
     [!code-vb[GenericMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#2)]  
  
3.  定義此泛型方法所屬的型別，  此型別不需要是泛型；  泛型方法可以屬於泛型或非泛型型別。  在此範例中，型別是類別、不是泛型，且命名為 `DemoType`。  
  
     [!code-csharp[GenericMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#3)]
     [!code-vb[GenericMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#3)]  
  
4.  定義泛型方法。  如果泛型方法的型式參數之型別是由泛型方法的泛型型別參數所指定，請使用 <xref:System.Reflection.Emit.TypeBuilder.DefineMethod%28System.String%2CSystem.Reflection.MethodAttributes%29> 方法多載來定義此方法。  尚未定義此方法的泛型型別參數，所以您無法在 <xref:System.Reflection.Emit.TypeBuilder.DefineMethod%2A> 的呼叫中指定此方法的型式參數之型別。  在此範例中，此方法命名為 `Factory`。  此方法為公用及 `static` \(Visual Basic 中為 `Shared`\)。  
  
     [!code-csharp[GenericMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#4)]
     [!code-vb[GenericMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#4)]  
  
5.  將包含參數名稱的字串陣列傳遞給 <xref:System.Reflection.Emit.MethodBuilder.DefineGenericParameters%2A?displayProperty=fullName> 方法來定義 `DemoMethod` 的泛型型別參數，  如此會將方法變成泛型方法。  下列程式碼會讓 `Factory` 變成具有型別參數 `TInput` 和 `TOutput` 的泛型方法。  若要讓程式碼更容易讀取，會建立具有這些名稱的變數，以保存表示這兩個型別參數的 <xref:System.Reflection.Emit.GenericTypeParameterBuilder> 物件。  
  
     [!code-csharp[GenericMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#5)]
     [!code-vb[GenericMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#5)]  
  
6.  選擇性地將特殊條件約束加入到型別參數中；  會使用 <xref:System.Reflection.Emit.GenericTypeParameterBuilder.SetGenericParameterAttributes%2A> 方法來加入特殊條件約束。  在此範例中，會將 `TOutput` 限制為參考型別及擁有無參數的建構函式。  
  
     [!code-csharp[GenericMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#6)]
     [!code-vb[GenericMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#6)]  
  
7.  選擇性地將類別和介面條件約束加入到型別參數中。  在此範例中，會將型別參數 `TOutput` 限制為實作 `ICollection(Of TInput)` \(C\# 中為 `ICollection<TInput>`\) 介面的型別；  如此可確保 <xref:System.Collections.Generic.ICollection%601.Add%2A> 方法可以用來加入項目。  
  
     [!code-csharp[GenericMethodHowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#7)]
     [!code-vb[GenericMethodHowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#7)]  
  
8.  定義此方法的型式參數 \(利用 <xref:System.Reflection.Emit.MethodBuilder.SetParameters%2A> 方法\)。  在此範例中，`Factory` 方法有一個參數，亦即 `TInput` 的陣列。  建立此型別的方式，是在表示 `TInput` 的 <xref:System.Reflection.Emit.GenericTypeParameterBuilder> 上呼叫 <xref:System.Type.MakeArrayType%2A> 方法。  <xref:System.Reflection.Emit.MethodBuilder.SetParameters%2A> 的引數是 <xref:System.Type> 物件的陣列。  
  
     [!code-csharp[GenericMethodHowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#8)]
     [!code-vb[GenericMethodHowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#8)]  
  
9. 為此方法定義傳回型別 \(利用 <xref:System.Reflection.Emit.MethodBuilder.SetReturnType%2A> 方法\)。  在此範例中，會傳回 `TOutput` 的執行個體。  
  
     [!code-csharp[GenericMethodHowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#9)]
     [!code-vb[GenericMethodHowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#9)]  
  
10. 發出方法主體 \(利用 <xref:System.Reflection.Emit.ILGenerator>\)。  如需詳細資訊，請參閱伴隨的程序以發出方法主體。  
  
    > [!IMPORTANT]
    >  當您發出泛型型別方法的呼叫，而這些型別的型別引數為泛型方法的型別參數時，您必須使用  `static` <xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29>, <xref:System.Reflection.Emit.TypeBuilder.GetMethod%28System.Type%2CSystem.Reflection.MethodInfo%29>, 以及 <xref:System.Reflection.Emit.TypeBuilder.GetField%28System.Type%2CSystem.Reflection.FieldInfo%29> 採用 <xref:System.Reflection.Emit.TypeBuilder> 方法多載來取得這些方法的建構之形式。   發出方法主體所伴隨的程序將示範這樣的處理方式。  
  
11. 完成包含此方法的型別，然後儲存組件。  伴隨的程序若要叫用泛型方法將示範叫用此完成方法的兩個方式。  
  
     [!code-csharp[GenericMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#14)]
     [!code-vb[GenericMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#14)]  
  
<a name="procedureSection1"></a>   
### 若要發出方法主體  
  
1.  取得程式碼產生器，並宣告區域變數和標籤。  <xref:System.Reflection.Emit.ILGenerator.DeclareLocal%2A> 方法是用來宣告區域變數；  `Factory` 方法則有四個區域變數：`retVal` 是用來保存此方法傳回的新 `TOutput`、`ic` 是用在 `TOutput` 轉換成  `ICollection(Of TInput)` \(C\# 中為 `ICollection<TInput>`\) 時保存它、`input` 是用來保存 `TInput` 物件的輸入陣列，而 `index` 則可逐一查看此陣列。  此方法也有兩個標籤，一個可用來進入迴圈 \(`enterLoop`\)，而另一個則可用於迴圈的最上方 \(`loopAgain`\)，透過 <xref:System.Reflection.Emit.ILGenerator.DefineLabel%2A> 方法來定義。  
  
     此方法做的第一件事是使用 <xref:System.Reflection.Emit.OpCodes.Ldarg_0> opcode 載入它的引數，並使用 <xref:System.Reflection.Emit.OpCodes.Stloc_S> opcode 將它儲存在區域變數 `input` 中。  
  
     [!code-csharp[GenericMethodHowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#10)]
     [!code-vb[GenericMethodHowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#10)]  
  
2.  使用 <xref:System.Activator.CreateInstance%2A?displayProperty=fullName> 方法的泛型方法多載，發出程式碼來建立 `TOutput` 的執行個體。  使用這個多載需要指定之型別擁有無參數的建構函式，而這是將該條件約束加入到 `TOutput` 中的理由。  建立建構的泛型方法，其方式是將 `TOutput` 傳遞給 <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>。  在發出程式碼來呼叫此方法之後，請利用 <xref:System.Reflection.Emit.OpCodes.Stloc_S> 發出程式碼，將它儲存在區域變數 `retVal` 中。  
  
     [!code-csharp[GenericMethodHowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#11)]
     [!code-vb[GenericMethodHowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#11)]  
  
3.  發出程式碼，將新的 `TOutput` 物件轉換成 `ICollection(Of TInput)`，並將它儲存在區域變數 `ic` 中。  
  
     [!code-csharp[GenericMethodHowTo#31](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#31)]
     [!code-vb[GenericMethodHowTo#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#31)]  
  
4.  取得 <xref:System.Reflection.MethodInfo>表示<xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=fullName> 方法.  這個方法會在 `ICollection(Of TInput)` 上運作 \(C\# 中為 `ICollection<TInput>`\)，所以必須要取得該建構的型別所特有的 `Add` 方法。  您不能使用 <xref:System.Type.GetMethod%2A> 方法來直接從 `icollOfTInput` 當中取得這個 <xref:System.Reflection.MethodInfo>，因為在已經使用 <xref:System.Reflection.Emit.GenericTypeParameterBuilder> 建構的型別上不支援 <xref:System.Type.GetMethod%2A>。  而是要改為在 `icoll` 上呼叫 <xref:System.Type.GetMethod%2A>，其中包含 <xref:System.Collections.Generic.ICollection%601> 泛型介面的泛型型別定義。  然後，使用 <xref:System.Reflection.Emit.TypeBuilder.GetMethod%28System.Type%2CSystem.Reflection.MethodInfo%29> `static` 方法為建構的型別產生 <xref:System.Reflection.MethodInfo>。  下列程式碼可示範這項處理。  
  
     [!code-csharp[GenericMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#12)]
     [!code-vb[GenericMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#12)]  
  
5.  發出程式碼來初始化 `index` 變數，透過的方式是載入 32 位元整數 0，並將它儲存在此變數中。  發出程式碼來分支到標籤 `enterLoop`，  這個標籤尚未被標記，因為它位於迴圈中；  下一個步驟中會發出此迴圈的程式碼。  
  
     [!code-csharp[GenericMethodHowTo#32](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#32)]
     [!code-vb[GenericMethodHowTo#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#32)]  
  
6.  發出此迴圈的程式碼。  第一個步驟是標記此迴圈的最上方，其方式是呼叫具有 `loopAgain` 標籤的 <xref:System.Reflection.Emit.ILGenerator.MarkLabel%2A>，  使用此標籤的分支陳述式現在會分支到程式碼中的這個點。  下一個步驟是在堆疊上推入 `TOutput` 物件，並轉換成 `ICollection(Of TInput)`。  並不會立即需要它，但是它必須要就定位之後，才能呼叫 `Add` 方法。  接下來，輸入陣列會推入到堆疊上，然後是將包含目前索引的 `index` 變數推入到陣列中。  <xref:System.Reflection.Emit.OpCodes.Ldelem> opcode 會將此索引和陣列從堆疊中移除，並將具索引的陣列元素推入到堆疊上。  現在，此堆疊便可準備好開始呼叫 <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=fullName> 方法，此方法會將集合和新的元素從堆疊中移除，並將此元素加入到集合中。  
  
     迴圈中的其餘程式碼會讓索引遞增，並測試看看迴圈是否已完成：此索引和 32 位元整數 1 會推入到堆疊上並相加，在堆疊上留下總和，而此總和會儲存在 `index` 中。  接著會呼叫 <xref:System.Reflection.Emit.ILGenerator.MarkLabel%2A>，將這個點設定為迴圈的進入點。  然後會再次載入此索引；  輸入陣列會推入到堆疊上，並發出 <xref:System.Reflection.Emit.OpCodes.Ldlen> 來取得其長度。  現在，此索引和長度會在堆疊上，且會發出 <xref:System.Reflection.Emit.OpCodes.Clt> 來比較它們。  如果此索引小於長度，則 <xref:System.Reflection.Emit.OpCodes.Brtrue_S> 會分支回到迴圈的開頭。  
  
     [!code-csharp[GenericMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#13)]
     [!code-vb[GenericMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#13)]  
  
7.  發出程式碼將 `TOutput` 物件推入到堆疊上，並從方法傳回。  區域變數 `retVal` 和 `ic` 都包含新 `TOutput` 的參考；`ic` 僅用來存取 <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=fullName> 方法。  
  
     [!code-csharp[GenericMethodHowTo#33](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#33)]
     [!code-vb[GenericMethodHowTo#33](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#33)]  
  
<a name="procedureSection2"></a>   
### 若要叫用泛型方法  
  
1.  `Factory` 是泛型方法定義；  為了要叫用它，您必須將型別指派給它的泛型型別參數。  請使用 <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> 方法來進行這項處理。  下列程式碼會建立建構的泛型方法，為 `TInput` 指定 <xref:System.String>，以及為 `TOutput` 指定 `List(Of String)` \(C\# 中為 `List<string>`\)，並顯示一個表示此方法的字串。  
  
     [!code-csharp[GenericMethodHowTo#21](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#21)]
     [!code-vb[GenericMethodHowTo#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#21)]  
  
2.  若要叫用晚期繫結的方法，請使用 <xref:System.Reflection.MethodBase.Invoke%2A> 方法。  下列程式碼會建立 <xref:System.Object> 的陣列、將字串陣列當做它的唯一元素來加入，並將它當做泛型方法的引數清單傳遞。  <xref:System.Reflection.MethodBase.Invoke%2A> 的第一個參數是 null 參考，因為此方法為 `static`。  傳回值會轉換成 `List(Of String)`，且會顯示它的第一個元素。  
  
     [!code-csharp[GenericMethodHowTo#22](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#22)]
     [!code-vb[GenericMethodHowTo#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#22)]  
  
3.  若要使用委派叫用方法，您必須有一個符合建構的泛型方法之簽章的委派；  一個簡單的方法是建立泛型委派。  下列程式碼會建立定義於範例程式碼中的泛型委派 `D` 之執行個體 \(利用 <xref:System.Delegate.CreateDelegate%28System.Type%2CSystem.Reflection.MethodInfo%29?displayProperty=fullName> 方法多載\)，並叫用此委派。  委派的執行效能優於晚期繫結呼叫。  
  
     [!code-csharp[GenericMethodHowTo#23](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#23)]
     [!code-vb[GenericMethodHowTo#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#23)]  
  
4.  也可以從參考儲存的組件之程式來呼叫發出的方法。  
  
## 範例  
 下列程式碼範例會建立具有泛型方法 `Factory` 的非泛型型別 `DemoType`。  這個方法有兩個泛型型別參數，`TInput` 可用來指定輸入型別，而 `TOutput` 則可指定輸出型別。  會將 `TOutput` 型別參數限制為必須實作 `ICollection<TInput>` \(Visual Basic 中為 `ICollection(Of TInput)`\)、必須是參考型別，且必須有無參數的建構函式。  
  
 此方法有一個型式參數，它是 `TInput` 的陣列。  這個方法會傳回包含輸入陣列中所有元素的 `TOutput` 執行個體。  `TOutput` 可以是實作 <xref:System.Collections.Generic.ICollection%601> 泛型介面的任一泛型集合型別。  
  
 當執行此程式碼時，動態組件會儲存為 DemoGenericMethod1.dll，而且可以利用 [Ildasm.exe \(IL Disassembler\)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 來加以檢查。  
  
> [!NOTE]
>  有一個很好的方法可以學習如何發出程式碼，那就是編寫 Visual Basic、C\# 或 Visual C\+\+ 程式 \(此程式可執行您嘗試要發出的工作\)，並使用反組譯工具來檢查編譯器產生的 MSIL。  
  
 此程式碼範例會加入與發出的方法相等的原始程式碼；  發出的方法會以晚期繫結形式叫用，也可透過程式碼範例中宣告的泛型委派來叫用。  
  
 [!code-csharp[GenericMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#1)]
 [!code-vb[GenericMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#1)]  
  
## 編譯程式碼  
  
-   此程式碼含有進行編譯所需的 C\# `using` 陳述式 \(Visual Basic 中的 `Imports`\)。  
  
-   不需要其他的組件參考。  
  
-   使用 csc.exe、vbc.exe 或 cl.exe 在命令列編譯程式碼。  若要在 Visual Studio 中編譯程式碼，請將程式碼放在主控台應用程式專案範本中。  
  
## 請參閱  
 <xref:System.Reflection.Emit.MethodBuilder>   
 [如何：使用反映發出定義泛型類型](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)