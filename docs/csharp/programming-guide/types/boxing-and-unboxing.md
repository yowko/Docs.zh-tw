---
title: Boxing 和 Unboxing - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
ms.openlocfilehash: 5db3d759daec273a29dccfeff9879d0edcc9a269
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595009"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a>Boxing 和 Unboxing (C# 程式設計手冊)
Boxing 是將[實值型別](../../../csharp/language-reference/keywords/value-types.md)轉換為 `object` 類型或是由這個實值型別實作之任何介面類型的程序。 當 CLR Box 處理實值類型時，它會將值包裝在 System.Object 內，並儲存到 Managed 堆積上。 Unbox 處理則會從物件中擷取實值類型。 Boxing 是隱含處理，unboxing 則是明確處理。 Boxing 和 unboxing 的概念是 C# 類型系統統一檢視的基礎，其中任何類型的值都可視為物件。  
  
 在下列範例中，整數變數 `i` 會經過 *Box* 處理並且指派給 `o` 物件。  
  
 [!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]  
  
 接著就可以對物件 `o` 進行 Unbox 處理，並將該物件指派給整數變數 `i`：  
  
 [!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]  
  
 下列範例將說明在 C# 中使用 boxing 的方式。  
  
 [!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]  
  
## <a name="performance"></a>效能  
 相對於單純的指派，boxing 和 unboxing 是會耗費大量運算資源的處理序。 當實值類型經過 Box 處理時，必須配置及建構新的物件。 Unboxing 所需的轉換雖然較為簡單，但也同樣需要大量運算資源。 如需詳細資訊，請參閱[效能](../../../../docs/framework/performance/performance-tips.md)。  
  
## <a name="boxing"></a>Boxing  
 Boxing 可用來儲存記憶體回收堆積中的實值類型。 Boxing 是一種隱含轉換，可將[實值型別](../../../csharp/language-reference/keywords/value-types.md)轉換為 `object` 類型，或是由這個實值型別實作的任何介面類型。 對實值類型進行 Boxing 處理時，會在堆積上配置物件執行個體，並將值複製到新物件中。  
  
 請考慮下列實值類型變數的宣告：  
  
 [!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]  
  
 下列陳述式會以隱含方式對變數 `i` 套用 boxing 作業：  
  
 [!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]  
  
 這個陳述式的結果是在堆疊上建立物件參考 `o`，用於參考堆積中 `int` 類型的值。 這個值是指派給變數 `i` 之實值類型值的複本。 `i` 和 `o` 這兩個變數之間的差異如下方 Boxing 轉換圖所示：  
  
 ![顯示 i 和 o 變數之間差異的圖形。](./media/boxing-and-unboxing/boxing-operation-i-o-variables.gif)    
  
 您也可以執行明確的 boxing 處理，如同下列範例中所示，但是明確的 boxing 處理並非必要：  
  
 [!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]  
  
## <a name="description"></a>說明  
 這個範例會使用 Boxing 將整數變數 `i` 轉換為物件 `o`。 接著，儲存在變數 `i` 中的值就會從 `123` 變更為 `456`。 這個範例顯示，原始實值類型以及經過 Box 處理的物件分別使用不同的記憶體位置，因此可以儲存不同的值。  
  
## <a name="example"></a>範例  
 [!code-csharp[csProgGuideTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#16)]  
  
## <a name="unboxing"></a>Unboxing  
 Unboxing 是將 `object` 類型明確轉換為[實值型別](../../../csharp/language-reference/keywords/value-types.md)，或將介面類型明確轉換為實作介面之實值型別的程序。 Unboxing 作業包含：  
  
- 檢查物件執行個體，確定它是所指定實值類型經過 Box 處理的值。  
  
- 將值從執行個體複製到實值類型變數。  
  
 下列陳述式將示範 boxing 和 unboxing 作業：  
  
 [!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]  
  
 下圖示範上述陳述式的結果： 
  
 ![顯示 Unboxing 轉換的圖形。](./media/boxing-and-unboxing/unboxing-conversion-operation.gif)
  
 若要在執行階段成功對實值類型進行 Unbox 處理，要進行 Unbox 處理的項目必須是物件的參考，而且該物件是先前對該實值類型的執行個體進行 Box 處理所建立的物件。 嘗試對 `null` 進行 Unbox 處理會造成 <xref:System.NullReferenceException>。 嘗試對不相容的實值類型參考進行 Unbox 處理會造成 <xref:System.InvalidCastException>。  
  
## <a name="example"></a>範例  
 下列範例將示範 Unboxing 無效且產生 `InvalidCastException` 的案例。 若使用 `try` 和 `catch`，則會在發生錯誤時顯示錯誤訊息。  
  
 [!code-csharp[csProgGuideTypes#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#20)]  
  
 這個程式會輸出：  
  
 `Specified cast is not valid. Error: Incorrect unboxing.`  
  
 如果您將陳述式：  
  
```csharp
int j = (short) o;  
```  
  
 變更為：  
  
```csharp
int j = (int) o;  
```  
  
 轉換將會執行，而且您會得到下列輸出結果：  
  
 `Unboxing OK.`  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="related-sections"></a>相關章節  
 如需詳細資訊：  
  
- [參考型別](../../../csharp/language-reference/keywords/reference-types.md)  
  
- [實值型別](../../../csharp/language-reference/keywords/value-types.md)  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
