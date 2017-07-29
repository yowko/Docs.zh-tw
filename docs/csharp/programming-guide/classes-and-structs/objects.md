---
title: "物件 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- objects [C#], about objects
- variables [C#]
ms.assetid: af4a5230-fbf3-4eea-95e1-8b883c2f845c
caps.latest.revision: 26
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ab83f765d6cc66bc0808a316cecabf65af7a3843
ms.lasthandoff: 03/13/2017

---
# <a name="objects-c-programming-guide"></a>物件 (C# 程式設計手冊)
類別或結構定義就像是指定型別可以做什麼的藍圖。 物件基本上是根據藍圖配置和設定的記憶體區塊。 程式可建立許多同類別的物件。 物件也稱為執行個體，可儲存在具名變數或陣列或集合中。 用戶端程式碼是使用這些變數呼叫方法，並存取物件公用屬性的程式碼。 在 C# 之類的物件導向語言中，一般程式包含多個動態互動的物件。  
  
> [!NOTE]
>  靜態型別的行為會和此處描述的不同。 如需詳細資訊，請參閱[靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。  
  
## <a name="struct-instances-vs-class-instances"></a>結構執行個體與類別執行個體  
 因為類別是參考型別，所以類別物件的變數會將參考保留在 Managed 堆積上的物件位址中。 如果同型別的第二個物件指派給第一個物件，則這兩個變數都會參考位於該位址的物件。 本主題稍後會詳細討論這一點。  
  
 使用 [new 運算子](../../../csharp/language-reference/keywords/new-operator.md) 建立類別的執行個體。 在下例中，`Person` 是型別，而 `person1` 和 `person 2` 則是該型別的執行個體或物件。  
  
 [!code-cs[csProgGuideStatements#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_1.cs)]  
  
 因為結構是實值型別，所以結構物件的變數會保留完整物件的複本。 結構的執行個體也可以使用 `new` 運算子建立，但這不是必要項目，如下例所示︰  
  
 [!code-cs[csProgGuideStatements#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_2.cs)]  
  
 `p1` 和 `p2` 的記憶體都配置在執行緒堆疊上。 該記憶體會和其宣告所在的型別或方法一起回收。 這是在指派時複製結構的原因之一。 相較之下，當物件的所有參考都超出範圍時，通用語言執行平台會自動回收為類別執行個體配置的記憶體 (記憶體回收)。 您不可能像在 C++ 中一樣決定性終結類別物件。 如需 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 記憶體回收的詳細資訊，請參閱[記憶體回收](../../../standard/garbagecollection/index.md)。  
  
> [!NOTE]
>  通用語言執行平台中，已高度最佳化 Managed 堆積上的記憶體配置和解除配置。 在大部分情況下，在堆積上配置類別執行個體與在堆疊上配置結構執行個體，效能成本沒有任何重大差異。  
  
## <a name="object-identity-vs-value-equality"></a>物件識別與實值相等  
 當您比較兩個物件是否相等時，您必須先區別是否想要知道這兩個變數在記憶體中是否代表相同的物件，或者其欄位的一或多個值是否相等。 如果您打算比較值，就必須考慮物件是實值型別 (結構) 還是參考型別 (類別、委派、陣列) 的執行個體。  
  
-   若要判斷兩個類別執行個體在記憶體中是否參考相同的位置 (表示它們具有相同的「身分識別」**)，請使用靜態 <xref:System.Object.Equals%2A> 方法。 (<xref:System.Object?displayProperty=fullName> 是所有實值型別和參考型別的隱含基底類別，包括使用者定義的結構和類別。)  
  
-   若要判斷兩個結構執行個體中的執行個體欄位是否有相同的值，請使用 <xref:System.ValueType.Equals%2A?displayProperty=fullName> 方法。 因為所有結構都是隱含繼承自 <xref:System.ValueType?displayProperty=fullName>，所以您直接在物件上呼叫方法，如下例所示︰  
  
 [!code-cs[csProgGuideStatements#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_3.cs)]  
  
 `Equals` 的 <xref:System.ValueType?displayProperty=fullName> 實作使用反映，因為它必須能夠判斷任何結構中有哪些欄位。 建立您自己的結構時，請覆寫 `Equals` 方法以提供型別專屬的有效相等演算法。  
  
-   若要判斷兩個類別執行個體中的欄位值是否相等，您或許可以使用 <xref:System.Object.Equals%2A> 方法或 [== 運算子](../../../csharp/language-reference/operators/equality-comparison-operator.md)。 但請只有當類別覆寫或多載它們，以提供「相等」表示的型別物件的自訂定義時，才使用它們。 類別可能也實作 <xref:System.IEquatable%601> 介面或 <xref:System.Collections.Generic.IEqualityComparer%601> 介面。 這兩個介面都會提供可用以測試值相等的方法。 設計您自己的類別覆寫 `Equals` 時，請務必遵循[如何：定義型別的實值相等](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md)和 <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> 所述的指導方針。  
  
## <a name="related-sections"></a>相關章節  
 如需詳細資訊：  
  
-   [類別](../../../csharp/programming-guide/classes-and-structs/classes.md)  
  
-   [結構](../../../csharp/programming-guide/classes-and-structs/structs.md)  
  
-   [建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [解構函式](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [事件](../../../csharp/programming-guide/events/index.md)  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [object](../../../csharp/language-reference/keywords/object.md)   
 [繼承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)   
 [class](../../../csharp/language-reference/keywords/class.md)   
 [struct](../../../csharp/language-reference/keywords/struct.md)   
 [ew 運算子](../../../csharp/language-reference/keywords/new-operator.md)   
 [一般類型系統](http://msdn.microsoft.com/library/53c57c96-83e1-4ee3-9543-9ac832671a89)
