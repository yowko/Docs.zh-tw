---
title: "具名和選擇性引數 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "namedParameter_CSharpKeyword"
  - "cs_namedParameter"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "引數 [C#], 具名"
  - "引數 [C#], 選擇性"
  - "具名和選擇性引數 [C#]"
  - "具名引數 [C#]"
  - "選擇性引數 [C#]"
  - "參數 [C#], 具名"
  - "參數 [C#], 選擇性"
ms.assetid: 839c960c-c2dc-4d05-af4d-ca5428e54008
caps.latest.revision: 43
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 43
---
# 具名和選擇性引數 (C# 程式設計手冊)
[!INCLUDE[csharp_dev10_long](../../../csharp/programming-guide/classes-and-structs/includes/csharp-dev10-long-md.md)] 引進具名和選擇性引數。  「*具名引數*」\(Named Argument\) 可讓您指定特定參數的引數，方法是將引數與參數的名稱建立關聯，而不是與參數清單中的參數位置建立關聯。  「*選擇性引數*」\(Optional Argument\) 則可讓您省略某些參數的引數。  這兩種技術都能搭配方法、索引子、建構函式和委派使用。  
  
 使用具名和選擇性引數時，引數是依照其出現在引數清單 \(而非參數清單\) 中的順序加以評估。  
  
 具名和選擇性參數一起使用時，可讓您供應引數給選擇性參數清單中的少數參數。  這項功能可大幅加速對 COM 介面 \(例如 Microsoft Office Automation API\) 的呼叫。  
  
## 具名引數  
 具名引數讓您不用再記住或查詢參數在被呼叫方法之參數清單中的順序。  您可用參數名稱指定每個引數的參數。  例如，可以用標準方式呼叫計算身體質量指數 \(BMI\) 的函式，也就是依照位置 \(由函式定義的順序\) 傳送代表體重和身高的引數。  
  
 `CalculateBMI(123, 64);`  
  
 如果不記得參數順序，但您知道參數名稱，則可以任意順序傳送引數，體重先或身高先皆可。  
  
 `CalculateBMI(weight: 123, height: 64);`  
  
 `CalculateBMI(height: 64, weight: 123);`  
  
 具名引數因為可以識別每個引數所代表的意義，因此也可以提升程式碼的可讀性。  
  
 具名引數可以放在位置引數後面，如下所示。  
  
 `CalculateBMI(123, height: 64);`  
  
 但是位置引數不能放在具名引數後面。  下列陳述式會造成編譯器錯誤。  
  
 `//CalculateBMI(weight: 123, 64);`  
  
## 範例  
 下列程式碼會實作本節中的範例。  
  
 [!code-cs[csProgGuideNamedAndOptional#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_1.cs)]  
  
## 選擇性引數  
 方法、建構函式、索引子或委派的定義可以指定其參數是必要的或選擇性的。  任何呼叫都必須提供所有必要參數的引數，但可以省略選擇性參數的引數。  
  
 每個選擇性參數的定義中都有預設值。  如果未傳送該參數的引數，便會使用預設值。  預設值必須是下列類型的運算式的其中一項：  
  
-   常數的運算式。  
  
-   形式的運算式`new ValType()`，其中`ValType`是實值型別，例如[列舉](../../../csharp/language-reference/keywords/enum.md)或[結構](../../../csharp/programming-guide/classes-and-structs/structs.md)。  
  
-   形式的運算式 [default\(ValType\)](../../../csharp/programming-guide/generics/default-keyword-in-generic-code.md)，其中`ValType`實值型別。  
  
 選擇性參數定義在參數清單的尾端，位在所有必要參數後面。  如果呼叫端想提供一連串選擇性參數其中一個的引數，則必須提供該參數前面所有選擇性參數的引數。  不支援在引數清單中使用逗號分隔的空格。  例如，在下列程式碼中，執行個體方法 `ExampleMethod` 以一個必要參數和兩個選擇性參數來定義。  
  
 [!code-cs[csProgGuideNamedAndOptional#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_2.cs)]  
  
 下列對 `ExampleMethod` 的呼叫會造成編譯器錯誤，因為有提供引數給第三個參數，但未提供給第二個參數。  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 不過，如果您知道第三個參數的名稱，則可使用具名引數來完成這項工作。  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 IntelliSense 使用中括弧表示選擇性參數，如下圖所示。  
  
 ![IntelliSense 對於 ExampleMethod 方法的快速諮詢。](../../../csharp/programming-guide/classes-and-structs/media/optional-parameters.png "Optional\_Parameters")  
ExampleMethod 中的選擇性參數  
  
> [!NOTE]
>  您也可以使用 .NET <xref:System.Runtime.InteropServices.OptionalAttribute> 類別來宣告選擇性參數。  `OptionalAttribute` 參數不需要預設值。  
  
## 範例  
 在下列範例中，`ExampleClass` 的建構函式有一個選擇性參數。  執行個體方法 `ExampleMethod` 有一個必要參數 `required`，以及兩個選擇性參數 `optionalstr` 和 `optionalint`。  `Main` 中的程式碼顯示叫用建構函式和方法的不同方法。  
  
 [!code-cs[csProgGuideNamedAndOptional#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_3.cs)]  
  
## COM 介面  
 具名和選擇性引數以及對動態物件和其他增強功能的支援，大幅增強了與 COM API \(例如 Office Automation API\) 的互通性。  
  
 例如，Microsoft Office Excel [Range](http://go.microsoft.com/fwlink/?LinkId=148196) 介面中的 [AutoFormat](http://go.microsoft.com/fwlink/?LinkId=148201) 方法有 7 個參數，全都是選擇性參數。  下圖顯示這些參數。  
  
 ![IntelliSense 對於 AutoFormat 方法的快速諮詢。](../../../csharp/programming-guide/classes-and-structs/media/autoformat-parameters.png "AutoFormat\_Parameters")  
AutoFormat 參數  
  
 在 C\# 3.0 \(含\) 以前版本中，每個參數都需要引數，如以下範例所示。  
  
 [!code-cs[csProgGuideNamedAndOptional#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_4.cs)]  
  
 不過，您可以使用 C\# 4.0 引進的具名和選擇性引數，大幅簡化對 `AutoFormat` 的呼叫。  具名和選擇性引數可讓您在不想變更選擇性參數的預設值時，省略該參數的引數。  在下列呼叫中，只指定 7 個參數其中一個參數的值。  
  
 [!code-cs[csProgGuideNamedAndOptional#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_5.cs)]  
  
 如需詳細資訊與範例，請參閱 [如何：在 Office 程式設計中使用具名和選擇性引數](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)與 [如何：使用 Visual C\#  功能存取 Office Interop 物件](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)。  
  
## 多載解析  
 使用具名和選擇性引數對多載解析的影響如下：  
  
-   如果方法、索引子或建構函式的每一個參數都是選擇性，或可由名稱或位置對應至呼叫陳述式中的單一引數，且該引數可轉換為該參數型別，則這個方法、索引子或建構函式就是執行的候選項。  
  
-   如果找到一個以上的候選項，則會對明確指定的引數套用多載解析規則的偏好轉換。  選擇性參數中的省略引數則會被忽略。  
  
-   如果有兩個候選項經評估為一樣適合，則傾向採用其選擇性參數在呼叫中沒有被省略引數的候選項。  這是來自多載解析偏向採用參數較少之候選項的一般性偏好。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [如何：在 Office 程式設計中使用具名和選擇性引數](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)   
 [使用動態類型](../../../csharp/programming-guide/types/using-type-dynamic.md)   
 [使用建構函式](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)   
 [使用索引子](../../../csharp/programming-guide/indexers/using-indexers.md)