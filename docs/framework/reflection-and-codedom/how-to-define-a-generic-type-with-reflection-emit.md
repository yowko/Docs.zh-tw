---
title: "如何：使用反映發出定義泛型類型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET Framework], reflection emit
- generics [.NET Framework], dynamic types
- reflection emit, generic types
ms.assetid: 07d5f01a-7b5b-40ea-9b15-f21561098fe4
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6096a54c6a530035bd32c24d427ba047f905476
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-define-a-generic-type-with-reflection-emit"></a>如何：使用反映發出定義泛型類型
本主題示範如何建立具有兩個型別參數的簡單泛型類型、如何將類別條件約束、介面條件約束及特殊條件約束套用至型別參數，以及如何建立成員，以使用類別的型別參數作為參數類型及傳回類型。  
  
> [!IMPORTANT]
>  方法不是只因為屬於泛型型別並使用該類型的型別參數，而成為泛型。 方法只有在有自己的型別參數清單時，才會是泛型。 泛型型別上的大部分方法不是泛型，如本例所示。 如需發出泛型方法的範例，請參閱[如何︰使用反映發出定義泛型方法](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-method-with-reflection-emit.md)。  
  
### <a name="to-define-a-generic-type"></a>定義泛型型別  
  
1.  定義名為 `GenericEmitExample1` 的動態組件。 在本例中，組件在執行後會儲存到磁碟，因此指定 <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndSave?displayProperty=nameWithType>。  
  
     [!code-cpp[EmitGenericType#2](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#2)]
     [!code-csharp[EmitGenericType#2](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#2)]
     [!code-vb[EmitGenericType#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#2)]  
  
2.  定義動態模組。 組件是由可執行模組組成。 組件如僅有一個模組，則模組名稱和組件名稱相同，且檔案名稱是模組名稱加上副檔名。  
  
     [!code-cpp[EmitGenericType#3](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#3)]
     [!code-csharp[EmitGenericType#3](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#3)]
     [!code-vb[EmitGenericType#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#3)]  
  
3.  定義類別。 本例中的類別名為 `Sample`。  
  
     [!code-cpp[EmitGenericType#4](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#4)]
     [!code-csharp[EmitGenericType#4](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#4)]
     [!code-vb[EmitGenericType#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#4)]  
  
4.  將包含參數名稱的字串陣列傳遞至 <xref:System.Reflection.Emit.TypeBuilder.DefineGenericParameters%2A?displayProperty=nameWithType> 方法，以定義 `Sample` 的泛型型別參數。 這可讓類別成為泛型型別。 傳回值是代表型別參數的 <xref:System.Reflection.Emit.GenericTypeParameterBuilder> 物件陣列，可用於發出的程式碼中。  
  
     在下列程式碼中，`Sample` 會成為具有型別參數 `TFirst` 和 `TSecond` 的泛型型別。 若要讓程式碼便於閱讀，每個 <xref:System.Reflection.Emit.GenericTypeParameterBuilder> 都要放在與型別參數同名的變數中。  
  
     [!code-cpp[EmitGenericType#5](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#5)]
     [!code-csharp[EmitGenericType#5](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#5)]
     [!code-vb[EmitGenericType#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#5)]  
  
5.  將特殊條件約束新增至型別參數。 在此範例中，型別參數 `TFirst` 限為具有無參數建構函式的類型及參考型別。  
  
     [!code-cpp[EmitGenericType#6](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#6)]
     [!code-csharp[EmitGenericType#6](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#6)]
     [!code-vb[EmitGenericType#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#6)]  
  
6.  或者將類別和介面條件約束新增至類型參數。 在本例中，型別參數 `TFirst` 限制為衍生自基底類別的類型，而此基底類別是由包含在變數 `baseType` 中的 <xref:System.Type> 物件所表示；以及實作介面的類型，而此介面的類型包含在變數 `interfaceA` 和 `interfaceB` 中。 請參閱宣告和指派這些變數的程式碼範例。  
  
     [!code-cpp[EmitGenericType#7](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#7)]
     [!code-csharp[EmitGenericType#7](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#7)]
     [!code-vb[EmitGenericType#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#7)]  
  
7.  定義欄位。 本例中的欄位類型是由型別參數 `TFirst` 所指定。 <xref:System.Reflection.Emit.GenericTypeParameterBuilder> 衍生自 <xref:System.Type>，所以只要可以使用類型的位置，都可以使用泛型型別參數。  
  
     [!code-cpp[EmitGenericType#21](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#21)]
     [!code-csharp[EmitGenericType#21](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#21)]
     [!code-vb[EmitGenericType#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#21)]  
  
8.  定義使用泛型型別之型別參數的方法。 請注意，這類方法不是泛型，除非它們有自己的型別參數清單。 下列程式碼定義 `static` 方法 (Visual Basic 為 `Shared`)，其接受 `TFirst` 陣列並傳回包含陣列所有項目的 `List<TFirst>` (Visual Basic 為 `List(Of TFirst)`)。 若要定義這個方法，即必須在泛型型別定義 `List<T>` 呼叫 <xref:System.Type.MakeGenericType%2A>，以建立類型 `List<TFirst>`。 (當您使用 `typeof` 運算子時會省略 `T` (Visual Basic 為 `GetType`)，以取得泛型型別定義。)參數類型是使用 <xref:System.Type.MakeArrayType%2A> 方法所建立。  
  
     [!code-cpp[EmitGenericType#22](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#22)]
     [!code-csharp[EmitGenericType#22](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#22)]
     [!code-vb[EmitGenericType#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#22)]  
  
9. 發出方法主體。 方法主體中包含三個作業碼，可將輸入陣列載入至堆疊，呼叫接受 `IEnumerable<TFirst>` (它會執行所有將輸入項目放入清單中的工作) 的 `List<TFirst>` 建構函式 ，並傳回 (將新的 <xref:System.Collections.Generic.List%601> 物件留在堆疊上)。 發出此程式碼最困難的部分是取得建構函式。  
  
     <xref:System.Reflection.Emit.GenericTypeParameterBuilder> 不支援 <xref:System.Type.GetConstructor%2A> 方法，所以不可能直接取得 `List<TFirst>` 的建構函式。 首先，必須取得泛型型別定義 `List<T>` 的建構函式，然後呼叫能將它轉換成對應的 `List<TFirst>` 建構函式的方法。  
  
     此程式碼範例所使用的建構函式接受 `IEnumerable<T>`。 但是請注意，這不是 <xref:System.Collections.Generic.IEnumerable%601> 泛型介面的泛型型別定義；相反地，來自 `List<T>` 的型別參數 `T` 必須取代 `IEnumerable<T>` 的型別參數 `T`。 (這似乎很令人困惑，只因為這兩個類型都有名為 `T` 的型別參數。 這就是這個程式碼範例使用名稱 `TFirst` 和 `TSecond` 的原因。)若要取得建構函式引數的類型，請從使用泛型型別定義 `IEnumerable<T>`，並以 `List<T>` 的第一個泛型型別參數呼叫 <xref:System.Type.MakeGenericType%2A> 開始。 建構函式引數清單必須當成陣列傳遞，本例中只有一個引數。  
  
    > [!NOTE]
    >  當您在 C# 中使用 `typeof` 運算子時，泛型型別定義會表示為 `IEnumerable<>`；在 Visual Basic 中使用 `GetType` 運算子時，會表示為 `IEnumerable(Of )`。  
  
     現在，在泛型型別定義上呼叫 <xref:System.Type.GetConstructor%2A>，即可能取得 `List<T>` 的建構函式。 若要將此建構函式轉換成對應的 `List<TFirst>` 的建構函式，請從 `List<T>` 將 `List<TFirst>` 和建構函式傳遞至靜態的 <xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29?displayProperty=nameWithType> 方法。  
  
     [!code-cpp[EmitGenericType#23](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#23)]
     [!code-csharp[EmitGenericType#23](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#23)]
     [!code-vb[EmitGenericType#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#23)]  
  
10. 建立類型並儲存檔案。  
  
     [!code-cpp[EmitGenericType#8](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#8)]
     [!code-csharp[EmitGenericType#8](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#8)]
     [!code-vb[EmitGenericType#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#8)]  
  
11. 叫用方法。 `ExampleMethod` 不是泛型，但其所屬類型是泛型，因此為取得可以叫用的 <xref:System.Reflection.MethodInfo>，必須從 `Sample` 的類型定義建立建構的類型。 建構的類型使用符合 `TFirst` 條件約束的 `Example` 類別，因為它是參考型別，且有預設的無參數建構函式；也使用符合 `TSecond` 條件約束的 `ExampleDerived` 類別。 (`ExampleDerived` 的程式碼請參見＜範例程式碼＞一節。)這兩種類型都會傳遞至 <xref:System.Type.MakeGenericType%2A>，以建立建構的類型。 然後，使用 <xref:System.Type.GetMethod%2A> 方法取得 <xref:System.Reflection.MethodInfo>。  
  
     [!code-cpp[EmitGenericType#9](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#9)]
     [!code-csharp[EmitGenericType#9](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#9)]
     [!code-vb[EmitGenericType#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#9)]  
  
12. 下列程式碼會建立 `Example` 物件的陣列，將該陣列放在代表要叫用之方法引數的類型 <xref:System.Object> 陣列中，並將它們傳遞至 <xref:System.Reflection.MethodBase.Invoke%28System.Object%2CSystem.Object%5B%5D%29> 方法。 <xref:System.Reflection.MethodBase.Invoke%2A> 方法的第一個引數為 Null 參考，因為方法是 `static`。  
  
     [!code-cpp[EmitGenericType#10](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#10)]
     [!code-csharp[EmitGenericType#10](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#10)]
     [!code-vb[EmitGenericType#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#10)]  
  
## <a name="example"></a>範例  
 下列程式碼範例會定義名為 `Sample` 的類別，以及一個基底類別和兩個介面。 程式會為 `Sample` 定義兩個泛型型別參數，將它轉換成泛型型別。 型別參數是唯一可將類型變成泛型的物件。 程式會顯示定義型別參數之前和之後的測試訊息，以顯示此變化。  
  
 使用基底類別和介面的型別參數 `TSecond` 用於示範類別和介面條件約束，而型別參數 `TFirst` 用於示範特殊條件約束。  
  
 程式碼範例會定義欄位和方法，針對欄位類別和參數使用類別的型別參數，並傳回方法的類型。  
  
 建立 `Sample` 類別之後，即叫用方法。  
  
 程式包含兩種方法，一種會列出泛型型別的相關資訊，一種會列出型別參數的特殊條件約束。 這些方法用來顯示已完成之 `Sample` 類別的相關資訊。  
  
 程式會在磁碟儲存已完成的模組 `GenericEmitExample1.dll`，因此您可以用 [Ildasm.exe (IL 反組譯工具)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 開啟它，並檢查 MSIL 是否有 `Sample` 類別。  
  
 [!code-cpp[EmitGenericType#1](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#1)]
 [!code-csharp[EmitGenericType#1](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#1)]
 [!code-vb[EmitGenericType#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   此程式碼包含編譯所需的 C# `using` 陳述式 (Visual Basic 為 `Imports`)。  
  
-   不需要任何其他組件參考。  
  
-   在命令列使用 csc.exe、vbc.exe 或 cl.exe 編譯程式碼。 若要編譯 Visual Studio 中的程式碼，請將它放在主控台應用程式專案範本。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Reflection.Emit.GenericTypeParameterBuilder>  
 [使用反映發出](http://msdn.microsoft.com/library/ccc6540d-0e2c-4d89-b456-eb7353f9e9ac)  
 [反映發出動態組件案例](http://msdn.microsoft.com/library/e1cc6750-e20f-473b-bb4e-f43bc66aecce)
