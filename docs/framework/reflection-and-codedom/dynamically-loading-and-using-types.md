---
title: "動態載入和使用類型 | Microsoft Docs"
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
  - "動態載入和使用類型"
  - "早期繫結"
  - "隱含晚期繫結"
  - "晚期繫結, 關於晚期繫結"
  - "反映, 動態使用類型"
ms.assetid: db985bec-5942-40ec-b13a-771ae98623dc
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# 動態載入和使用類型
反映 \(Reflection\) 提供語言編譯器 \(例如 [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] 和 JScript\) 用來實作隱含晚期繫結的基礎結構。  繫結是找出對應唯一指定型別的宣告 \(即實作\) 的過程。  當這個過程出現在執行階段而非編譯時期時，就稱為晚期繫結  [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] 可以讓您在程式碼中使用隱含晚期繫結，Visual Basic 編譯器會呼叫使用反映取得物件型別的 Helper 方法。  傳遞至 Helper 方法的引數使得適當的方法在執行階段被叫用。  這些引數是用以叫用方法的執行個體 \(物件\)、叫用的方法的名稱 \(字串\)，和傳遞至叫用的方法的引數 \(物件陣列\)。  
  
 在下列程式碼範例中，Visual Basic  編譯器隱含地使用反映呼叫物件上的方法，其型別在編譯時間為未知。  **HelloWorld** 類別具有 **PrintHello** 方法，印出與傳遞至 **PrintHello** 方法的一些文字串連的 "Hello World"。  這個範例中呼叫的 **PrintHello** 方法實際上是 <xref:System.Type.InvokeMember%2A?displayProperty=fullName>；Visual Basic 程式碼允許叫用 **PrintHello** 方法，就好像物件 \(helloObj\) 的型別在編譯時間 \(早期繫結\) 已經知道，而非在執行階段 \(晚期繫結\)。  
  
```  
Imports System  
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
  
## 自訂繫結  
 除了要被編譯器隱含地使用作晚期繫結之外，反映還可以在程式碼中明確地用來完成晚期繫結。  
  
 [Common Language Runtime](../../../docs/standard/clr.md) 支援多個程式設計語言，而這些語言的繫結規則各有不同。  在早期繫結的情況中，程式碼產生器可以完全控制這個繫結。  然而，在透過反映的晚期繫結中，繫結必須受自訂繫結的控制。  <xref:System.Reflection.Binder> 類別提供成員選取和引動過程的自訂控制項。  
  
 使用自訂繫結，您可以在執行階段載入組件，取得該組件中型別的資訊，指定您想要的型別，並接著叫用方法，或存取該型別上的欄位或屬性。  這個技術很有用，如果您在編譯時間不知道物件的型別，例如當物件型別靠使用者輸入時。  
  
 以下範例示範不提供引數型別轉換的簡單自訂繫結器 \(Binder\)。  `Simple_Type.dll` 的程式碼位於主要範例之前。  在建置時間中，請務必建置 `Simple_Type.dll`，然後再將參考納入專案中。  
  
 [!code-cpp[Conceptual.Types.Dynamic#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.dynamic/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.Dynamic#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.dynamic/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.Dynamic#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.dynamic/vb/source1.vb#1)]  
  
### InvokeMember 和 CreateInstance  
 使用 <xref:System.Type.InvokeMember%2A?displayProperty=fullName> 叫用型別成員。  各種類別的 **CreateInstance** 方法，例如 [System.Activator](frlrfSystemActivatorClassCreateInstanceTopic) 和 [System.Reflection.Assembly](frlrfSystemReflectionAssemblyClassCreateInstanceTopic)，都是 **InvokeMember** 的特殊形式，可以建立指定型別的新執行個體。  **Binder** 類別被使用於這些方法中的多載解析 \(Overload Resolution\) 和引數強制。  
  
 下列程式碼範例說明引數強制型轉 \(型別轉換\) 和成員選取的三種可能組合。  案例 1，不需要引數強制或成員選取。  案例 2，只需要成員選取。  案例 3，只需要引數強制。  
  
 [!code-cpp[Conceptual.Types.Dynamic#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.dynamic/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.Dynamic#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.dynamic/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.Dynamic#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.dynamic/vb/source2.vb#2)]  
  
 當有多個具相同名稱的成員可供使用時，需要多載解析。  <xref:System.Reflection.Binder.BindToMethod%2A?displayProperty=fullName> 和 <xref:System.Reflection.Binder.BindToField%2A?displayProperty=fullName> 方法用來解析單一成員的繫結。  **Binder.BindToMethod** 也透過 **get** 和 **set** 屬性存取子提供屬性解析。  
  
 **BindToMethod** 會傳回要叫用的 <xref:System.Reflection.MethodBase>，如果無法叫用，則會傳回 null 參考 \(Visual Basic 中為 **Nothing**\)。  **MethodBase** 傳回值不一定要是那些包含於 *match*  參數的其中之一，雖然常是如此。  
  
 當 ByRef 引數出現時，呼叫端可能會想將它們取回。  因此，**Binder** 允許用戶端將引數陣列對應回到它的原來形式，如果 **BindToMethod** 已經操作引數陣列的話。  為了這樣做，呼叫端必須保證不變更引數的順序。  當引數按名稱傳遞時，繫結器 **Binder** 會重新排列引述陣列，而那就是呼叫端所看到的。  如需詳細資訊，請參閱 <xref:System.Reflection.Binder.ReorderArgumentArray%2A?displayProperty=fullName>。  
  
 可用成員的集合為那些在型別或任何基底型別 \(Base Type\) 中定義的成員。  如果 [BindingFlags.NonPublic](frlrfSystemReflectionBindingFlagsClassTopic) 已指定，任何存取範圍的成員將在集合中傳回。  如果不指定 **BindingFlags.NonPublic**，繫結器必須強制使用存取範圍規則。  指定 **Public** 或 **NonPublic** 繫結旗標時，您也必須指定 **Instance** 或 **Static** 繫結旗標，否則將不會傳回成員。  
  
 如果只有一個指定名稱的成員，則沒有回呼 \(Callback\) 的必要，而繫結即在那個方法上完成。  程式碼範例的案例 1 說明了這一點：只有一個 **PrintBob** 方法可用，因此不需要回呼。  
  
 如果有多個成員在可用集合中，這些方法會全部傳遞至 **BindToMethod**，以選取適當的方法並傳回它。  程式碼範例的案例 2 中，有兩個名為 **PrintValue** 的方法。  適當的方法經由呼叫 **BindToMethod** 來選取。  
  
 <xref:System.Reflection.Binder.ChangeType%2A> 執行引數強制 \(型別轉換\)，轉換實際引數至選取方法的型式引數 \(Formal Argument\) 型別。  即使型別完全相符，**ChangeType** 仍會被每個引數呼叫。  
  
 在程式碼範例的案例 3 中，**String** 型別的實際引數，會將其值 "5.5" 傳遞至具有 **Double** 型別的型式引數 \(Formal Argument\) 的方法。  為使引動過程成功，字串值 "5.5" 必須轉換為雙精度浮點數 \(Double\) 值。  **ChangeType** 會負責執行轉換。  
  
 **ChangeType** 只會執行無遺漏或[擴展強制型轉 \(Coercion\)](../../../docs/standard/base-types/type-conversion.md)，如下表所示。  
  
|來源型別|目標型別|  
|----------|----------|  
|任何型別|其基底型別|  
|任何型別|它實作的介面|  
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
|非參考型別|參考型別|  
  
 <xref:System.Type> 類別具有 **Get** 方法，使用 **Binder** 型別的參數解析參考至特定的成員。  <xref:System.Type.GetConstructor%2A?displayProperty=fullName>、<xref:System.Type.GetMethod%2A?displayProperty=fullName> 和 <xref:System.Type.GetProperty%2A?displayProperty=fullName> 會藉由提供該成員的簽章資訊，搜尋目前型別的特殊成員。  會再次呼叫 <xref:System.Reflection.Binder.SelectMethod%2A?displayProperty=fullName> 和 <xref:System.Reflection.Binder.SelectProperty%2A?displayProperty=fullName>，以選取適當方法的指定簽章資訊。  
  
## 請參閱  
 <xref:System.Type.InvokeMember%2A?displayProperty=fullName>   
 <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>   
 [檢視類型資訊](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)   
 [.NET Framework 中的類型轉換](../../../docs/standard/base-types/type-conversion.md)