---
title: "泛型方法 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
caps.latest.revision: "27"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 63252dbe4307889f57d35e23eb0575f84358d737
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="generic-methods-c-programming-guide"></a>泛型方法 (C# 程式設計手冊)
泛型方法是使用型別參數宣告的方法，如下所示：  
  
 [!code-csharp[csProgGuideGenerics#22](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_1.cs)]  
  
 下列程式碼範例示範一種方法，使用型別引數的 `int`呼叫方法：  
  
 [!code-csharp[csProgGuideGenerics#23](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_2.cs)]  
  
 您也可以省略型別引數，編譯器會推斷它。 以下對 `Swap` 的呼叫，相當於先前的呼叫：  
  
 [!code-csharp[csProgGuideGenerics#24](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_3.cs)]  
  
 相同的型別推斷規則適用於靜態方法和執行個體方法。 編譯器可以根據您傳入的方法引數推斷型別參數，但無法只從條件約束或傳回值推斷型別參數。 因此，型別推斷對沒有參數的方法不起作用。 編譯時期先出現型別推斷，編譯器才嘗試解析多載的方法簽章。 編譯器會將型別推斷邏輯套用到所有共用相同名稱的泛型方法。 在多載解析步驟中，編譯器只包含型別推斷已成功的那些泛型方法。  
  
 在泛型類別中，非泛型方法可以存取類別層級類型的參數，如下所示：  
  
 [!code-csharp[csProgGuideGenerics#25](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_4.cs)]  
  
 如果您定義的泛型方法接受與包含類別相同的型別參數，編譯器會產生警告 CS0693，因為在方法範圍內，為內部 `T` 提供的引數會隱藏為外部 `T` 提供的引數。 在類別具現化後，如果您需要以不是提供的型別引數來彈性呼叫泛型類別方法，請考慮為方法的型別參數提供另一個識別碼，如下列範例中的 `GenericList2<T>` 所示。  
  
 [!code-csharp[csProgGuideGenerics#26](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_5.cs)]  
  
 使用條件約束，在方法中的型別參數上啟用更多特定作業。 本版的 `Swap<T>` 現在名為 `SwapIfGreater<T>`，只能搭配實作 <xref:System.IComparable%601> 的型別引數一起使用。  
  
 [!code-csharp[csProgGuideGenerics#27](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_6.cs)]  
  
 泛型方法可以多載到數個型別參數上。 例如，下列方法可以全都位於相同的類別中：  
  
 [!code-csharp[csProgGuideGenerics#28](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_7.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 如需詳細資訊，請參閱＜[C# 語言規格](../../../csharp/language-reference/language-specification/index.md)＞。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Collections.Generic>  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [泛型簡介](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)
