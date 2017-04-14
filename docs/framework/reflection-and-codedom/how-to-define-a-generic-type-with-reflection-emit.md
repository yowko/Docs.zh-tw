---
title: "如何：使用反映發出定義泛型類型 | Microsoft Docs"
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
  - "反映發出, 泛型類型"
ms.assetid: 07d5f01a-7b5b-40ea-9b15-f21561098fe4
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：使用反映發出定義泛型類型
這個主題將示範如何建立具有兩個型別參數的簡單泛型型別、如何套用類別條件約束、介面條件約束及型別參數的特殊條件約束，以及如何建立將類別的型別參數當做參數型別和傳回型別使用的成員。  
  
> [!IMPORTANT]
>  方法不會只因為它屬於泛型型別及使用該型別的型別參數，就會是泛型；  只有在方法有它自己的型別參數清單時，才會是泛型。  如同這個範例所示，泛型型別上的大多數方法都不是泛型。  如需發出泛型方法的範例，請參閱 [如何：使用反映發出定義泛型方法](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-method-with-reflection-emit.md)。  
  
### 如何定義泛型型別  
  
1.  定義名為 `GenericEmitExample1` 的動態組件。  在此範例中，會執行此組件，並將它儲存到磁碟上，所以指定了 <xref:System.Reflection.Emit.AssemblyBuilderAccess?displayProperty=fullName>。  
  
     [!code-cpp[EmitGenericType#2](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#2)]
     [!code-csharp[EmitGenericType#2](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#2)]
     [!code-vb[EmitGenericType#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#2)]  
  
2.  定義動態模組。  組件是由可執行的模組所組成；  對於單一模組的組件而言，模組名稱與組件名稱相同，而檔名則是模組名稱加上副檔名。  
  
     [!code-cpp[EmitGenericType#3](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#3)]
     [!code-csharp[EmitGenericType#3](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#3)]
     [!code-vb[EmitGenericType#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#3)]  
  
3.  定義類別。  在這個範例中，此類別命名為 `Sample`。  
  
     [!code-cpp[EmitGenericType#4](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#4)]
     [!code-csharp[EmitGenericType#4](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#4)]
     [!code-vb[EmitGenericType#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#4)]  
  
4.  將包含參數名稱的字串陣列傳遞給 <xref:System.Reflection.Emit.TypeBuilder.DefineGenericParameters%2A?displayProperty=fullName> 方法來定義 `Sample` 的泛型型別參數，  如此會將類別變成泛型型別。  傳回值是表示型別參數的 <xref:System.Reflection.Emit.GenericTypeParameterBuilder> 物件陣列，這些參數可用於發出的程式碼中。  
  
     在下列程式碼中，`Sample` 會變成具有型別參數 `TFirst` 和 `TSecond` 的泛型型別。  為了要讓程式碼更容易讀取，每一個 <xref:System.Reflection.Emit.GenericTypeParameterBuilder> 都會放置於與型別參數同名的變數中。  
  
     [!code-cpp[EmitGenericType#5](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#5)]
     [!code-csharp[EmitGenericType#5](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#5)]
     [!code-vb[EmitGenericType#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#5)]  
  
5.  將特殊條件約束加入到型別參數中。  在此範例中，型別參數 `TFirst` 會限制為具有無參數的建構函式之型別以及參考型別。  
  
     [!code-cpp[EmitGenericType#6](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#6)]
     [!code-csharp[EmitGenericType#6](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#6)]
     [!code-vb[EmitGenericType#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#6)]  
  
6.  選擇性地將類別和介面條件約束加入到型別參數中。  在此範例中，型別參數 `TFirst` 限制為衍生自 <xref:System.Type> 物件 \(包含於變數 `baseType` 中\) 表示的基底類別，以及可實作介面 \(此介面的型別包含在變數 `interfaceA` 和 `interfaceB` 中\) 的型別。  請參閱程式碼範例，以了解這些變數的宣告和指派。  
  
     [!code-cpp[EmitGenericType#7](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#7)]
     [!code-csharp[EmitGenericType#7](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#7)]
     [!code-vb[EmitGenericType#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#7)]  
  
7.  定義欄位。  在此範例中，欄位型別由型別參數 `TFirst` 指定。  <xref:System.Reflection.Emit.GenericTypeParameterBuilder> 衍生自 <xref:System.Type>，因此在可以使用型別的位置都可以使用泛型型別參數。  
  
     [!code-cpp[EmitGenericType#21](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#21)]
     [!code-csharp[EmitGenericType#21](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#21)]
     [!code-vb[EmitGenericType#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#21)]  
  
8.  定義使用泛型型別之型別參數的方法。  請注意，這類方法除非有其自己的型別參數清單，否則不為泛型。  下列程式碼會定義 `static` 方法 \(Visual Basic 中為 `Shared`\)，此方法可接受 `TFirst` 的陣列，並傳回包含所有陣列元素的 `List<TFirst>` \(Visual Basic 中為 `List(Of TFirst)`\)。  若要定義這個方法，必須要建立 `List<TFirst>` 型別，其方式是呼叫泛型型別定義 `List<T>` 上的 <xref:System.Type.MakeGenericType%2A>。\(當您使用 `typeof` 運算子 \(Visual Basic 中為 `GetType`\) 來取得泛型型別定義時，會省略 `T`\)。可以使用 <xref:System.Type.MakeArrayType%2A> 方法來建立參數型別。  
  
     [!code-cpp[EmitGenericType#22](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#22)]
     [!code-csharp[EmitGenericType#22](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#22)]
     [!code-vb[EmitGenericType#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#22)]  
  
9. 發出方法主體。  方法主體是由三個 opcode 所組成，這些 opcode 會將輸入陣列載入到堆疊上、呼叫可接受 `IEnumerable<TFirst>` \(其會執行將輸入元素放入到清單中的所有工作\) 的 `List<TFirst>` 建構函式，然後傳回 \(讓新的 <xref:System.Collections.Generic.List%601> 物件留在堆疊上\)。  發出此程式碼的困難部分是取得此建構函式。  
  
     <xref:System.Reflection.Emit.GenericTypeParameterBuilder> 上並不支援 <xref:System.Type.GetConstructor%2A> 方法，所以無法直接取得 `List<TFirst>` 的建構函式。  首先，必須取得泛型型別定義 `List<T>` 的建構函式，然後呼叫可以將它轉換成 `List<TFirst>` 之對應建構函式的方法。  
  
     用於此程式碼範例的建構函式可接受 `IEnumerable<T>`；  但是請注意，這並不是 <xref:System.Collections.Generic.IEnumerable%601> 泛型介面的泛型型別定義；相反地，`List<T>` 中的型別參數 `T` 必須替代 `IEnumerable<T>` 的型別參數 `T`。\(因為這兩個型別都有名為 `T` 的型別參數，所以似乎讓人有點混淆；  因此，此程式碼範例使用 `TFirst` 和 `TSecond` 的名稱\)。若要取得建構函式引數的型別，請先從泛型型別定義 `IEnumerable<T>` 開始，然後使用 `List<T>` 的第一個泛型型別參數來呼叫 <xref:System.Type.MakeGenericType%2A>。  此建構函式引數清單必須以陣列形式傳遞 \(在此案例中，只有一個引數\)。  
  
    > [!NOTE]
    >  當您在 C\# 中使用 `typeof` 運算子時，泛型型別定義會表示為 `IEnumerable<>`；當您在 Visual Basic 中使用 `GetType` 運算子時，則表示為 `IEnumerable(Of )`。  
  
     現在，可以藉由呼叫泛型型別定義上的 <xref:System.Type.GetConstructor%2A> 來取得 `List<T>` 的建構函式。  若要將此建構函式轉換為 `List<TFirst>` 的對應建構函式，請將 `List<TFirst>` 和此建構函式從 `List<T>` 傳遞到靜態 <xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29?displayProperty=fullName> 方法。  
  
     [!code-cpp[EmitGenericType#23](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#23)]
     [!code-csharp[EmitGenericType#23](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#23)]
     [!code-vb[EmitGenericType#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#23)]  
  
10. 建立型別，然後儲存檔案。  
  
     [!code-cpp[EmitGenericType#8](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#8)]
     [!code-csharp[EmitGenericType#8](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#8)]
     [!code-vb[EmitGenericType#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#8)]  
  
11. 叫用方法。  `ExampleMethod` 不是泛型，但是它所屬的型別是泛型，所以為了要取得可以叫用的 <xref:System.Reflection.MethodInfo>，必須要從 `Sample` 的型別定義建立建構的型別。  此建構的型別會使用 `Example` 類別，而此類別可滿足 `TFirst` 上的條件約束，因為它是參考型別，而且有預設的無參數之建構函式，以及可滿足 `TSecond` 上的條件約束之 `ExampleDerived` 類別。\(`ExampleDerived` 的程式碼可以在範例程式碼一節中找到\)。這兩個型別會傳遞到 <xref:System.Type.MakeGenericType%2A>，以建立建構的型別。  然後，可以使用 <xref:System.Type.GetMethod%2A> 方法來取得 <xref:System.Reflection.MethodInfo>。  
  
     [!code-cpp[EmitGenericType#9](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#9)]
     [!code-csharp[EmitGenericType#9](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#9)]
     [!code-vb[EmitGenericType#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#9)]  
  
12. 下列程式碼會建立 `Example` 物件的陣列，並將該陣列放入型別 <xref:System.Object> 的陣列中 \(其表示要叫用之方法的引數\)，然後再將它們傳遞給 [Invoke\(Object, Object\<xref:System.Reflection.MethodBase.Invoke%28System.Object%2CSystem.Object%5B%5D%29> 方法。  <xref:System.Reflection.MethodBase.Invoke%2A> 方法的第一個引數為 null 參考，因為此方法是 `static`。  
  
     [!code-cpp[EmitGenericType#10](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#10)]
     [!code-csharp[EmitGenericType#10](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#10)]
     [!code-vb[EmitGenericType#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#10)]  
  
## 範例  
 下列程式碼範例會定義名為 `Sample` 的類別，連同基底類別和兩個介面。  程式會針對 `Sample` 定義兩個泛型型別參數，將它轉換成泛型型別。  型別參數是讓型別變成泛型的唯一條件；  程式會在型別參數定義之前和之後顯示一則測試訊息，以顯示這個條件。  
  
 型別參數 `TSecond` 是用來示範類別和介面條件約束，以使用基底類別和介面，而型別參數 `TFirst` 是用來示範特殊條件約束。  
  
 此程式碼範例會定義欄位和方法，透過的方式是使用該欄位型別和參數的類別之型別參數，以及方法的傳回型別。  
  
 當建立 `Sample` 類別之後，即會叫用此方法。  
  
 程式會加入一個可列出泛型型別相關資訊的方法，以及一個可列出型別參數上的特殊條件約束之方法。  這些方法可用來顯示與完成的 `Sample` 類別有關的資訊。  
  
 程式會將此完成的模組以 `GenericEmitExample1.dll` 形式儲存到磁碟中，所以您可利用 [Ildasm.exe \(IL Disassembler\)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 來開啟它，並檢視 `Sample` 類別中的 MSIL。  
  
 [!code-cpp[EmitGenericType#1](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#1)]
 [!code-csharp[EmitGenericType#1](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#1)]
 [!code-vb[EmitGenericType#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#1)]  
  
## 編譯程式碼  
  
-   此程式碼含有進行編譯所需的 C\# `using` 陳述式 \(Visual Basic 中的 `Imports`\)。  
  
-   不需要其他的組件參考。  
  
-   使用 csc.exe、vbc.exe 或 cl.exe 在命令列編譯程式碼。  若要在 Visual Studio 中編譯程式碼，請將程式碼放在主控台應用程式專案範本中。  
  
## 請參閱  
 <xref:System.Reflection.Emit.GenericTypeParameterBuilder>   
 [Using Reflection Emit](http://msdn.microsoft.com/zh-tw/ccc6540d-0e2c-4d89-b456-eb7353f9e9ac)   
 [Reflection Emit Dynamic Assembly Scenarios](http://msdn.microsoft.com/zh-tw/e1cc6750-e20f-473b-bb4e-f43bc66aecce)