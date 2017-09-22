---
title: "using 陳述式 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
caps.latest.revision: 31
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 201dde951b4f92d92b7d78b3d71a3f3cfb559507
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="using-statement-c-reference"></a>using 陳述式 (C# 參考)
提供方便的語法，以確保正確使用 <xref:System.IDisposable> 物件。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 using 陳述式。  
  
 [!code-cs[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_1.cs)]  
  
## <a name="remarks"></a>備註  
 <xref:System.IO.File> 和 <xref:System.Drawing.Font> 是 Managed 類型的範例，這些類型會存取 Unmanaged 資源 (在本例中為檔案控制代碼和裝置內容)。 還有許多其他類型的 Unmanaged 資源，以及封裝這些資源的類別庫類型。 所有這類類型都必須實作 <xref:System.IDisposable> 介面。  
  
 一般而言，當您使用 `IDisposable` 物件時，您應該在 `using` 陳述式中宣告並具現化該物件。 `using` 陳述式會在物件上正確地呼叫 <xref:System.IDisposable.Dispose%2A> 方法，而且 (當您如稍早所示使用它時) 它也會在呼叫 <xref:System.IDisposable.Dispose%2A> 時導致物件本身超出範圍。 在 `using` 區塊內，物件是唯讀的，而且無法加以修改或重新指派。  
  
 `using` 陳述式可確保呼叫 <xref:System.IDisposable.Dispose%2A>，即使在物件上呼叫方法時發生例外狀況也一樣。 您可以將物件放在 try 區塊內，然後在 finally 區塊中呼叫 <xref:System.IDisposable.Dispose%2A>，來達到相同的結果；事實上，這就是編譯器轉譯 `using` 陳述式的方式。 稍早的程式碼範例會在編譯時期展開為下列程式碼 (注意額外的大括號是為了建立物件的有限範圍)：  
  
 [!code-cs[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_2.cs)]  
  
 您可以在 `using` 陳述式中宣告一種類型的多個執行個體，如下列範例所示。  
  
 [!code-cs[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_3.cs)]  
  
 您可以具現化資源物件，然後將變數傳遞至 `using` 陳述式，但這不是最佳做法。 在此情況下，物件會在控制權離開 `using` 區塊之後留在範圍內，不過它可能無法再存取其 Unmanaged 資源。 換句話說，您再也無法將它完整初始化。 如果您嘗試在 `using` 區塊外部使用該物件，則會有導致擲回例外狀況的風險。 因此，通常最好在 `using` 陳述式中具現化物件，並將其範圍限制為 `using` 區塊。  
  
 [!code-cs[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_4.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [using 指示詞](../../../csharp/language-reference/keywords/using-directive.md)   
 [記憶體回收](../../../standard/garbage-collection/index.md)   
 [實作 Dispose 方法](../../../standard/garbage-collection/implementing-dispose.md)

