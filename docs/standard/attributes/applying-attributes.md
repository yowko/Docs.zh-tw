---
title: "套用屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "組件 [.NET Framework], 屬性"
  - "屬性 [.NET Framework], 套用"
ms.assetid: dd7604eb-9fa3-4b60-b2dd-b47739fa3148
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 19
---
# 套用屬性
使用下列程序將屬性套用到您的程式碼項目。  
  
1.  從 .NET Framework 匯入它的命名空間 \(Namespace\) 來定義新屬性或使用現存的屬性。  
  
2.  將屬性 \(Attribute\) 放在緊接於程式碼項目之前的位置，藉此將屬性套用到此項目。  
  
     每個語言皆有自己的屬性語法。  在 C\+\+ 和 C\# 中，屬性是以方括號括住，並以可包含分行符號的泛空白字元 \(White Space\) 與項目分隔。  在 Visual Basic 中，屬性是以角括弧括住，並且必須位於相同的邏輯程式敘述行 \(Logical Line\)；如果需要使用分行符號，可以使用行接續符號字元。  在 J\# 中，會使用特殊的註解語法附加屬性。  
  
3.  指定屬性的位置參數和具名參數。  
  
     位置參數是必要項，並且必須在任何具名參數之前，且會對應到一個屬性建構函式 \(Constructor\) 的參數。  具名參數是選擇性參數，且會對應到屬性 \(Attribute\) 的讀取\/寫入屬性 \(Property\)。  在 C\+\+、C\# 和 J\# 中，為每個選擇性參數指定 `name`\=`value`，其中 `name` 為屬性的名稱。  在 Visual Basic 中，指定 `name`:\=`value`。  
  
 此屬性會在您編譯程式碼時發送至中繼資料內，並且透過執行階段反映服務，在 Common Language Runtime 和任何自訂工具或應用程式中使用。  
  
 依照慣例，所有屬性名稱以 Attribute 作結尾。  然而，許多以執行階段為目標的語言，例如 Visual Basic 和 C\#，不需要您指定屬性的完整名稱。  例如，如果您想要初始化 <xref:System.ObsoleteAttribute?displayProperty=fullName>，就只需要以 **Obsolete** 參考它。  
  
## 將屬性套用至方法  
 下列程式碼範例示範如何宣告 **System.ObsoleteAttribute**，其標記程式碼為過時的。  字串 `"Will be removed in next version"` 會傳遞至屬性。  當呼叫屬性所描述的程式碼時，這個屬性產生編譯器警告以顯示傳遞的字串。  
  
 [!code-cpp[Conceptual.Attributes.Usage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#3)]
 [!code-csharp[Conceptual.Attributes.Usage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#3)]
 [!code-vb[Conceptual.Attributes.Usage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#3)]  
  
## 在組件層級套用屬性  
 如果您想要在組件 \(Assembly\) 層級套用屬性，請使用 **assembly** 關鍵字。\(在版本Visual Basic中使用`Assembly` 下列程式碼示範在組件層級套用 **AssemblyTitleAttribute**。  
  
 [!code-cpp[Conceptual.Attributes.Usage#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#2)]
 [!code-csharp[Conceptual.Attributes.Usage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#2)]
 [!code-vb[Conceptual.Attributes.Usage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#2)]  
  
 當套用這個屬性後，`"My Assembly"` 字串將被放在檔案的中繼資料裡的組件資訊清單 \(Assembly Manifest\) 中。  您可以使用 [MSIL 反組譯工具 \(Ildasm.exe\)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 或者建立擷取屬性的自訂程式來檢視屬性。  
  
## 請參閱  
 [屬性](../../../docs/standard/attributes/index.md)   
 [擷取儲存於屬性中的資訊](../../../docs/standard/attributes/retrieving-information-stored-in-attributes.md)   
 [Concepts](../Topic/Attributed%20Programming%20Concepts.md)   
 [屬性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)