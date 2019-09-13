---
title: 動態載入和使用類型
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- late binding, about late binding
- early binding
- dynamically loading and using types
- implicit late binding
- reflection, dynamically using types
ms.assetid: db985bec-5942-40ec-b13a-771ae98623dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5dbbf0f71eaefd0ef7fc7f2b5e69e47ce7b8db26
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894890"
---
# <a name="dynamically-loading-and-using-types"></a>動態載入和使用類型
反映會提供語言編譯器所使用的基礎結構，以實作隱含晚期繫結。 繫結是尋找對應至唯一指定的類型宣告 (也就是實作) 的程序。 當此程序發生在執行階段，而不是在編譯時期時，它稱為晚期繫結。 Visual Basic 可讓您在程式碼內使用隱含晚期繫結；Visual Basic 編譯器會呼叫 Helper 方法，它會使用反映來取得物件類型。 傳遞至 helper 方法的引數會導致在執行階段叫用適當的方法。 這些引數是在其上叫用方法的執行個體 (物件)、被叫用方法的名稱 (字串)，以及傳遞給被叫用方法的引數 (物件陣列)。  
  
 在下列範例中，Visual Basic 編譯器會隱含地使用反映，對一個在編譯階段不知道其類型的物件呼叫方法。 **HelloWorld** 類別具有 **PrintHello** 方法，它會列印出 "Hello World" 並串連傳遞給 **PrintHello** 方法的部分文字。 在此範例中呼叫的 **PrintHello** 方法實際上是 <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType>；Visual Basic 程式碼允許叫用 **PrintHello** 方法，就彷彿已在編譯階段知道物件 (helloObj) 的類型 (早期繫結)，而不是執行階段知道 (晚期繫結)。  
  
```vb
Module Hello  
    Sub Main()  
        ' Sets up the variable.  
        Dim helloObj As Object  
        ' Creates the object.  
        helloObj = new HelloWorld()  
        ' Invokes the print method as if it was early bound  
        ' even though it is really late bound.  
        helloObj.PrintHello("Visual Basic Late Bound")  
    End Sub  
End Module  
```  
  
## <a name="custom-binding"></a>自訂繫結  
 除了編譯器隱含地用來進行晚期繫結，反映也可明確地用於程式碼，來完成晚期繫結。  
  
 [Common Language Runtime](../../standard/clr.md) 支援多種程式設計語言，而這些語言的繫結規則不同。 在早期繫結案例中，程式碼產生器可以完全控制這個繫結。 不過，在透過反映的晚期繫結中，繫結必須受自訂繫結控制。 <xref:System.Reflection.Binder> 類別會提供成員選取和叫用的自訂控制。  
  
 您可以使用自訂繫結，在執行階段載入組件、取得該組件中的類型相關資訊、指定您要的類型，然後對該類型叫用方法或存取欄位或屬性。 這個技術非常有用，如果您在編譯時期不知道物件的類型，例如當物件類型取決於使用者輸入之時。  
  
 下列範例將示範簡單的自訂繫結，它不提供任何引數類型轉換。 `Simple_Type.dll` 的程式碼在主要範例之前。 請務必建置 `Simple_Type.dll`，然後在建置階段的專案中包含對它的參考。  
  
 [!code-cpp[Conceptual.Types.Dynamic#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.dynamic/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.Dynamic#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.dynamic/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.Dynamic#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.dynamic/vb/source1.vb#1)]  
  
### <a name="invokemember-and-createinstance"></a>InvokeMember 和 CreateInstance  
 使用 <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType> 來叫用類型的成員。 各種類別的 **CreateInstance** 方法，例如 <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> 和 <xref:System.Reflection.Assembly.CreateInstance%2A?displayProperty=nameWithType>，是 **InvokeMember** 的特殊形式，會建立指定類型的新執行個體。 **Binder** 類別用來在這些方法中進行多載解析和引數強制型轉。  
  
 下列範例顯示引數強制型轉 (類型轉換) 和成員選取的三種可能組合。 案例 1 中不需要任何引數強制型轉或成員選取。 案例 2 中只需要成員選取。 案例 3 中只需要引數強制型轉。  
  
 [!code-cpp[Conceptual.Types.Dynamic#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.dynamic/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.Dynamic#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.dynamic/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.Dynamic#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.dynamic/vb/source2.vb#2)]  
  
 有多個相同名稱的成員可用時，需要多載解析。 <xref:System.Reflection.Binder.BindToMethod%2A?displayProperty=nameWithType> 和 <xref:System.Reflection.Binder.BindToField%2A?displayProperty=nameWithType> 方法用來解析對單一成員的繫結。 **Binder.BindToMethod** 也透過 **get** 和 **set** 屬性存取子提供屬性解析。  
  
 **BindToMethod** 會傳回要叫用的 <xref:System.Reflection.MethodBase>，如果不可能進行這種叫用則傳回 null 參考 (在 Visual Basic 中為 **Nothing**)。 **MethodBase** 傳回值不一定要是 *match* 參數中所包含的其中一者，雖然這是常見的情況。  
  
 有 ByRef 引數存在時，呼叫端可能會想要取回它們。 因此，**Binder** 允許用戶端將引數的陣列對應回其原始形式，如果 **BindToMethod** 已操作引數陣列的話。 若要這樣做，必須向呼叫端保證，引數的順序不變。 依名稱傳遞引數時，**Binder** 會重新排列引數陣列，那也是呼叫端看到的情況。 如需詳細資訊，請參閱 <xref:System.Reflection.Binder.ReorderArgumentArray%2A?displayProperty=nameWithType>。  
  
 可用成員的集合是在類型或任何基底類型中定義的成員。 如果指定 <xref:System.Reflection.BindingFlags>，則會在集合中傳回任何存取範圍的成員。 如果未指定 **BindingFlags.NonPublic**，繫結器必須強制執行存取範圍規則。 指定 **Public** 或 **NonPublic** 繫結旗標時，您也必須指定 **Instance** 或 **Static** 繫結旗標，否則不會傳回任何成員。  
  
 如果指定名稱的成員只有一個，便不需要回呼，會對該方法進行任何繫結。 程式碼範例的案例 1 將說明這一點：只有一個 **PrintBob** 方法可用，因此不需要回呼。  
  
 如果可用的集合中有多個成員，這些方法全都會傳遞至 **BindToMethod**，它會選取適當的方法，並傳回它。 在程式碼範例的案例 2 中，有兩個方法，名為 **PrintValue**。 呼叫 **BindToMethod** 會選取適當的方法。  
  
 <xref:System.Reflection.Binder.ChangeType%2A> 會執行引數強制型轉 (類型轉換)，這會將實際引數轉換為所選方法的正式引數的類型。 即使類型完全相符，也會為每個引數呼叫 **ChangeType**。  
  
 程式碼範例的案例 3 中，類型 **String** 的實際引數以及值 "5.5" 會傳遞至具有類型 **Double** 的型式引數的方法。 叫用要成功，字串值 "5.5" 必須轉換為雙精度浮點數值。 **ChangeType** 會執行這項轉換。  
  
 **ChangeType** 只能執行不失真或[擴展強制型轉](../../standard/base-types/type-conversion.md)，如下表所示。  
  
|來源類型|目標類型|  
|-----------------|-----------------|  
|任何型別|基底類型|  
|任何型別|實作的介面|  
|Char|UInt16、UInt32、Int32、UInt64、Int64、Single、Double|  
|Byte|Char、UInt16、Int16、UInt32、Int32、UInt64、Int64、Single、Double|  
|SByte|Int16、Int32、Int64、Single、Double|  
|UInt16|UInt32、Int32、UInt64、Int64、Single、Double|  
|Int16|Int32、Int64、Single、Double|  
|UInt32|UInt64、Int64、Single、Double|  
|Int32|Int64、Single、Double|  
|UInt64|Single、Double|  
|Int64|Single、Double|  
|Single|Double|  
|非參考類型|參考型別|  
  
 <xref:System.Type> 類別具有 **Get** 方法，使用類型 **Binder** 的參數來解析對特定成員的參考。 <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType>、<xref:System.Type.GetMethod%2A?displayProperty=nameWithType> 和 <xref:System.Type.GetProperty%2A?displayProperty=nameWithType> 會搜尋目前類型的特定成員，方法是提供該成員的簽章資訊。 接著回來呼叫 <xref:System.Reflection.Binder.SelectMethod%2A?displayProperty=nameWithType> 和 <xref:System.Reflection.Binder.SelectProperty%2A?displayProperty=nameWithType>，選取適當方法的指定簽章資訊。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- [檢視類型資訊](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
- [.NET Framework 中的型別轉換](../../standard/base-types/type-conversion.md)
