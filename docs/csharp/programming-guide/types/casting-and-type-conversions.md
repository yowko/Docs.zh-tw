---
title: "轉型和類型轉換 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- type conversion [C#]
- data type conversion [C#]
- numeric conversions [C#]
- conversions [C#], type
- casting [C#]
- converting types [C#]
ms.assetid: 568df58a-d292-4b55-93ba-601578722878
caps.latest.revision: "52"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1361a7f115e2bae4b2d1f6271fa9020706581691
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="casting-and-type-conversions-c-programming-guide"></a>轉型和類型轉換 (C# 程式設計手冊)
因為 C# 在編譯時期是靜態類型，所以宣告變數之後，除非該類型可轉換為變數的類型，否則無法再次宣告或用來儲存另一個類型的值。 例如，沒有從整數到任何任意字串的轉換。 因此，將 `i` 宣告為整數之後，無法對其指派字串 "Hello"，如下列程式碼所示。  
  
```csharp  
int i;  
i = "Hello"; // Error: "Cannot implicitly convert type 'string' to 'int'"  
```  
  
 不過，您有時可能需要將值複製至另一種類型的變數或方法參數。 例如，您的整數變數可能需要傳遞給參數類型為 `double` 的方法。 或者，您可能需要將類別變數指派給介面類型的變數。 這些類型的作業稱為「類型轉換」。 在 C# 中，您可以執行下列類型的轉換：  
  
-   **隱含轉換**︰因為轉換為型別安全，所以不需要特殊語法，因此將不會造成資料遺失。 範例包括從較小到較大整數型別的轉換，以及從衍生類別到基底類別的轉換。  
  
-   **明確轉換 (轉換)**：明確轉換需要轉換運算子。 如果資訊可能會在轉換時遺失，或轉換因其他原因而失敗，則需要轉換。  一般範例包括將數字轉換為較少有效位數或較小範圍的類型，以及將基底類別執行個體轉換為衍生類別。  
  
-   **使用者定義的轉換**：使用者定義的轉換是透過特殊方法所執行，而您可以定義特殊方法來啟用沒有基底類別/衍生類別關聯性之自訂類型間的明確和隱含轉換。 如需詳細資訊，請參閱[轉換運算子](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)。  
  
-   **使用協助程式類別轉換**：若要轉換不相容類型 (例如，整數和 <xref:System.DateTime?displayProperty=nameWithType> 物件，或十六進位字串和位元組陣列)，您可以使用 <xref:System.BitConverter?displayProperty=nameWithType> 類別、<xref:System.Convert?displayProperty=nameWithType> 類別，以及內建數字類型的 `Parse` 方法 (例如，<xref:System.Int32.Parse%2A?displayProperty=nameWithType>)。 如需詳細資訊，請參閱[如何：將位元組陣列轉換為整數](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)、[如何：將字串轉換為數值](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)和[如何：在十六進位字串和數字類型間轉換](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)。  
  
## <a name="implicit-conversions"></a>隱含轉換  
 針對內建數字類型，如果要儲存的值可以放入變數中，而不需進行截斷或四捨五入，則可以進行隱含轉換。 例如，[long](../../../csharp/language-reference/keywords/long.md) (8 位元組整數) 類型的變數可以儲存 [int](../../../csharp/language-reference/keywords/int.md) (32 位元電腦上的 4 個位元組) 可儲存的任何值。 在下列範例中，編譯器會先將右側的值隱含地轉換為類型 `long`，再將它指派給 `bigNum`。  
  
 [!code-csharp[csProgGuideTypes#34](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_1.cs)]  
  
 如需所有隱含數值轉換的完整清單，請參閱[隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。  
  
 針對參考型別，一律會執行從某個類別到其任何一個直接或間接基底類別或介面的隱含轉換。 因為衍生類別一律會包含基底類別的所有成員，所以不需要特殊語法。  
  
```  
Derived d = new Derived();  
Base b = d; // Always OK.  
```  
  
## <a name="explicit-conversions"></a>明確轉換  
 不過，如果進行轉換，而有遺失資訊的風險，則編譯器需要您執行稱為「轉換」的明確轉換。 轉換是一種方式，可明確通知編譯器，您想要進行轉換並且了解可能發生資料遺失。 若要執行轉換，請在要轉換的值或變數前面的括弧中指定要轉換為的類型。 下列程式會將 [double](../../../csharp/language-reference/keywords/double.md) 轉型為 [int](../../../csharp/language-reference/keywords/int.md)。沒有轉型，就不會編譯程式。  
  
 [!code-csharp[csProgGuideTypes#2](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_2.cs)]  
  
 如需允許的明確數值轉換清單，請參閱[明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)。  
  
 針對參考型別，如果您需要將基底類型轉換為衍生類型，則需要明確轉換︰  
  
```csharp  
// Create a new derived type.  
Giraffe g = new Giraffe();  
  
// Implicit conversion to base type is safe.  
Animal a = g;  
  
// Explicit conversion is required to cast back  
// to derived type. Note: This will compile but will  
// throw an exception at run time if the right-side  
// object is not in fact a Giraffe.  
Giraffe g2 = (Giraffe) a;  
```  
  
 參考型別之間的轉型作業不會變更基礎物件的執行階段類型；它只會變更將用作該物件之參考值的類型。 如需詳細資訊，請參閱[多型](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)。  
  
## <a name="type-conversion-exceptions-at-run-time"></a>執行階段的類型轉換例外狀況  
 在某些參考型別轉換中，編譯器無法判斷轉換是否有效。 正確編譯的轉型作業可能會在執行階段失敗。 如下列範例所示，在執行階段失敗的型別轉型將導致擲回 <xref:System.InvalidCastException>。  
  
 [!code-csharp[csProgGuideTypes#41](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_3.cs)]  
  
 C# 提供 [is](../../../csharp/language-reference/keywords/is.md) 和 [as](../../../csharp/language-reference/keywords/as.md) 運算子，可讓您先測試相容性，再實際執行轉型。 如需詳細資訊，請參閱[如何：使用 as 和 is 運算子進行安全轉型](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md)。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a>請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [型別](../../../csharp/programming-guide/types/index.md)  
 [() 運算子](../../../csharp/language-reference/operators/invocation-operator.md)  
 [explicit](../../../csharp/language-reference/keywords/explicit.md)  
 [implicit](../../../csharp/language-reference/keywords/implicit.md)  
 [轉換運算子](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)  
 [產生的類型轉換](http://msdn.microsoft.com/library/49253ae6-7657-4810-82ab-1176a6feeada)  
 [匯出的類型轉換](http://msdn.microsoft.com/library/1dfe55f4-07a2-4b61-aabf-a8cf65783a6b)  
 [如何：將字串轉換為數值](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)
