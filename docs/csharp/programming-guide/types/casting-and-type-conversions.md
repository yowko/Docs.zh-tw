---
title: "轉型和類型轉換 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "轉型 [C#]"
  - "轉換 [C#], 類型"
  - "轉換類型 [C#]"
  - "資料類型轉換 [C#]"
  - "數值轉換 [C#]"
  - "類型轉換 [C#]"
ms.assetid: 568df58a-d292-4b55-93ba-601578722878
caps.latest.revision: 52
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 52
---
# 轉型和類型轉換 (C# 程式設計手冊)
因為 C\# 在編譯時期採用靜態型別，所以變數在經過宣告之後，就無法再次宣告或用來儲存任何其他型別的值，除非該型別可以轉換為變數的型別。  例如，整數和任意字串間不能轉換。  因此，在您將 `i` 宣告為整數之後，便無法指派字串 "Hello" 給它，如下列程式碼中所示。  
  
```c#  
int i;  
i = "Hello"; // Error: "Cannot implicitly convert type 'string' to 'int'"  
```  
  
 不過，您有時可能需要將值複製到其他型別的變數或方法參數中。  例如，您必須將整數變數傳遞至參數型別為 `double` 的方法。  或者，您可能需要將類別變數指派給介面型別 \(Interface Type\) 的變數。  此類作業稱為「*型別轉換*」\(Type Conversion\)。  在 C\# 中，您可以執行以下類型的轉換：  
  
-   **隱含轉換**：不必使用特殊語法，因為這類轉換屬於型別安全轉換，而且不會遺失資料。  這類範例包括從小型到大型整數型別的轉換，以及從衍生類別 \(Derived Class\) 到基底類別 \(Base Class\) 的轉換。  
  
-   **明確轉換 \(轉型\)**：明確轉換需要使用轉型運算子。  當資料可能在轉換中遺失，或轉換可能因故無法成功時，進行轉換 \(Cast\) 有其必要。例如，對精確度較低或範圍較小型別的數值轉換以及基底類別對衍生類別的轉換都是常見的轉換。  
  
-   **使用者定義轉換**：使用者定義轉換是由特殊方法執行，您可以定義這些特殊方法，以啟用自訂型別 \(不具有基底類別與衍生類別的關聯性\) 之間的明確和隱含轉換。  如需詳細資訊，請參閱 [轉換運算子](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)。  
  
-   **使用 Helper 類別的轉換**：為了在不相容型別 \(例如整數與 <xref:System.DateTime?displayProperty=fullName> 物件或十六進位字串與位元組陣列\) 之間進行轉換，您可以使用 <xref:System.BitConverter?displayProperty=fullName> 類別、<xref:System.Convert?displayProperty=fullName> 類別和內建數字型別 \(Numeric Type\) 的 `Parse` 方法，例如 <xref:System.Int32.Parse%2A?displayProperty=fullName>。  如需詳細資訊，請參閱 [如何：將位元組陣列轉換成整數](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)、[如何：將字串轉換為數值](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)和[如何：在十六進位字串和數字類型間轉換](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)。  
  
## 隱含轉換  
 對於內建數字型別，如果要儲存的值能完全符合變數需求而不需捨去或進位，則可進行隱含轉換。  例如，[long](../../../csharp/language-reference/keywords/long.md) 型別的變數 \(8 位元組的整數\) 可以儲存 [int](../../../csharp/language-reference/keywords/int.md) \(32 位元電腦中的 4 個位元組\) 能夠儲存的任何值。  在下列範例中，編譯器會將右邊的值隱含轉換為 `long` 型別之後，才指派給 `bigNum`。  
  
 [!code-cs[csProgGuideTypes#34](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_1.cs)]  
  
 如需隱含數值轉換的完整清單，請參閱[隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。  
  
 針對參考型別 \(Reference Type\)，將類別轉換為其任何直接或間接基底類別或介面時，一律會使用隱含轉換。  不必使用特殊語法，因為衍生類別一定包含基底類別的所有成員。  
  
```  
Derived d = new Derived();  
Base b = d; // Always OK.  
```  
  
## 明確轉換  
 如果轉換可能會造成資料遺失，編譯器會要求您執行明確轉換，這稱為「*轉型*」\(Cast\)。  轉型是明確告知編譯器您打算進行轉換而且知道可能會造成資料遺失的一種方式。  若要執行轉型，請在要轉換的值或變數前面的括號內指定要轉換的目標型別。  下列程式會將 [double](../../../csharp/language-reference/keywords/double.md) 轉型為  [int](../../../csharp/language-reference/keywords/int.md)。  若沒有進行轉型，就無法編譯程式。  
  
 [!code-cs[csProgGuideTypes#2](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_2.cs)]  
  
 如需可用的明確數值轉換清單，請參閱[明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)。  
  
 針對參考型別，如果需要從基底型別轉換成衍生型別，就必須進行明確轉換：  
  
```c#  
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
  
 參考型別之間的轉型作業並不會變更基礎物件的執行階段型別，只會變更做為該物件參考之值的型別。  如需詳細資訊，請參閱 [多型](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)。  
  
## 執行階段發生的型別轉換例外狀況  
 對於有些參考型別轉換，編譯器無法判斷轉型是否有效。  因此轉型作業編譯正確，但卻可能會在執行階段失敗。  如下列範例所示，型別轉換 \(Type Cast\) 在執行階段失敗將導致擲回 <xref:System.InvalidCastException>。  
  
 [!code-cs[csProgGuideTypes#41](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_3.cs)]  
  
 C\# 提供 [is](../../../csharp/language-reference/keywords/is.md) 和 [as](../../../csharp/language-reference/keywords/as.md) 運算子，讓您可在實際執行轉型之前先測試相容性。  如需詳細資訊，請參閱 [如何：使用 as 和 is 運算子進行安全轉型](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md)。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 精選書籍章節  
 [更多關於變數](完整.嗎？LinkId%20=%20221230) 在 [開頭 2010 視覺化 C\#](完整.嗎？LinkId%20=%20221214)  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [類型](../../../csharp/programming-guide/types/index.md)   
 [\(\) 運算子](../../../csharp/language-reference/operators/invocation-operator.md)   
 [explicit](../../../csharp/language-reference/keywords/explicit.md)   
 [隱含](../../../csharp/language-reference/keywords/implicit.md)   
 [轉換運算子](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)   
 [Generalized Type Conversion](../Topic/Generalized%20Type%20Conversion.md)   
 [Exported Type Conversion](http://msdn.microsoft.com/zh-tw/1dfe55f4-07a2-4b61-aabf-a8cf65783a6b)   
 [如何：將字串轉換為數值](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)