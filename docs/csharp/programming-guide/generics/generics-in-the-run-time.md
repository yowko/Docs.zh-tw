---
title: 執行階段中的泛型 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], at run time
ms.assetid: 119df7e6-9ceb-49df-af36-24f8f8c0747f
ms.openlocfilehash: c7cc0580398eeb5c70422cba3569340133107b12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334531"
---
# <a name="generics-in-the-run-time-c-programming-guide"></a>執行階段中的泛型 (C# 程式設計手冊)
當泛型型別或方法編譯到 Microsoft intermediate language (MSIL) 時，會包含可將其識別為具有型別參數的中繼資料。 泛型型別 MSIL 的使用方法，因提供的型別參數為實值型別或參考型別而異。  
  
 第一次以實值型別將泛型型別建構為參數時，執行階段會使用提供的參數或在 MSIL 適當位置中取代的參數，建立特定的泛型型別。 用為參數的每個唯一實值型別只建立一次特定的泛型型別。  
  
 例如，假設程式碼宣告以整數建構的堆疊：  
  
 [!code-csharp[csProgGuideGenerics#42](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_1.cs)]  
  
 此時，執行階段會產生 <xref:System.Collections.Generic.Stack%601> 類別的特定版本，以整數適當取代其參數。 現在，每當程式碼使用整數堆疊時，執行階段都會重複使用所產生的特定 <xref:System.Collections.Generic.Stack%601> 類別。 在下例中，會建立兩個整數堆疊的執行個體，它們共用一個 `Stack<int>` 程式碼的單一執行個體：  
  
 [!code-csharp[csProgGuideGenerics#43](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_2.cs)]  
  
 不過，假設在程式碼的另一個點建立了另一個 <xref:System.Collections.Generic.Stack%601> 類別，以不同的實值型別 (如 `long`) 或使用者定義的結構做為其參數。 結果，執行階段會產生另一個版本的泛型型別，替代 MSIL 適當位置的 `long`。 因為每個特定的泛型類別原本就包含實值型別，所以不再需要轉換。  
  
 泛型在參考型別的運作方式稍有不同。 第一次搭配任何參考型別建構泛型型別時，執行階段會建立特定的泛型型別，以物件參考取代 MSIL 中的參數。 然後，建構類型每次搭配參考型別具現化為其參數時，不論類型為何，執行階段都會重複使用先前建立的特定版本泛型型別。 這之所以可能，是因為所有的參考大小都相同。  
  
 例如，假設您有兩個參考型別，`Customer` 類別和 `Order` 類別，也假設您建立了 `Customer` 類型的堆疊：  
  
 [!code-csharp[csProgGuideGenerics#47](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_3.cs)]  
  
 [!code-csharp[csProgGuideGenerics#44](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_4.cs)]  
  
 此時，執行階段會產生特定版本的 <xref:System.Collections.Generic.Stack%601> 類別，儲存稍後要填入的物件參考，而不是儲存資料。 假設下一行程式碼建立另一個參考型別的堆疊，名為 `Order`：  
  
 [!code-csharp[csProgGuideGenerics#45](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_5.cs)]  
  
 與實值型別不同，另一個特定版本的 <xref:System.Collections.Generic.Stack%601> 類別並非針對 `Order` 類型而建立。 改建立特定版本的 <xref:System.Collections.Generic.Stack%601> 類別執行個體，設定 `orders` 變數參考它。 假設您接下來遇到一行程式碼，建立 `Customer` 類型的堆疊：  
  
 [!code-csharp[csProgGuideGenerics#46](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_6.cs)]  
  
 如同先前使用以 `Order` 類型建立的 <xref:System.Collections.Generic.Stack%601> 類別一樣，建立另一個特定 <xref:System.Collections.Generic.Stack%601> 類別的執行個體。 其中包含的指標會設定為參考大小為 `Customer` 類型的記憶體區域。 因為程式與程式之間的參考型別數目大不相同，所以泛型的 C# 實作會將編譯器所建立的參考型別泛型類別的特定類別數目降低到一，大幅減少程式碼數量。  
  
 甚而，當泛型的 C# 類別使用實值型別或參考型別參數具現化時，反映會在執行階段查詢它，並確定其實際的類型及其型別參數。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Collections.Generic>  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [泛型簡介](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [泛型](~/docs/standard/generics/index.md)
