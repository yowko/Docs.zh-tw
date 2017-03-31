---
title: "具名和選擇性引數 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- namedParameter_CSharpKeyword
- cs_namedParameter
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], named
- named arguments [C#]
- arguments [C#], named
- optional arguments [C#]
- arguments [C#], optional
- parameters [C#], optional
- named and optional arguments [C#]
ms.assetid: 839c960c-c2dc-4d05-af4d-ca5428e54008
caps.latest.revision: 43
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
ms.openlocfilehash: 9827553c1362d92bdf68a50e840b33474a22dcaa
ms.lasthandoff: 03/13/2017

---
# <a name="named-and-optional-arguments-c-programming-guide"></a>具名和選擇性引數 (C# 程式設計手冊)
[!INCLUDE[csharp_dev10_long](../../../csharp/programming-guide/classes-and-structs/includes/csharp_dev10_long_md.md)] 介紹具名和選擇性引數。 「具名引數」**可讓您使用參數的名稱而非使用參數清單中的參數位置來關聯引數，指定特定參數的引數。 「選擇性引數」**可讓您省略某些參數的引數。 這兩種技巧都可以搭配方法、索引子、建構函式和委派使用。  
  
 當您使用具名和選擇性引數時，會依照引數清單中的引數顯示順序來評估引數，不是依照參數清單的順序。  
  
 具名和選擇性參數一起使用時，可讓您只為選擇性參數清單中的幾個參數提供引數。 這項功能大幅有助呼叫 COM 介面，例如 Microsoft Office Automation API。  
  
## <a name="named-arguments"></a>具名引數  
 具名引數讓您不需要記住或查詢呼叫方法參數清單中的參數順序。 參數名稱可以指定每個引數的參數。 例如，依函式定義的順序來傳送位置的體重和身高引數，可以標準方式呼叫計算身體質量指數 (BMI) 的函式。  
  
 `CalculateBMI(123, 64);`  
  
 如果您不記得參數的順序，但知道它們的名稱，您可以依照任何順序傳送引數：體重先或身高先。  
  
 `CalculateBMI(weight: 123, height: 64);`  
  
 `CalculateBMI(height: 64, weight: 123);`  
  
 具名引數也藉由識別每個引數所代表的意義，改善程式碼的可讀性。  
  
 具名引數可以接在位置引數後面，如下所示。  
  
 `CalculateBMI(123, height: 64);`  
  
 但位置引數不能接在具名引數後面。 下列陳述式會導致編譯器錯誤。  
  
 `//CalculateBMI(weight: 123, 64);`  
  
## <a name="example"></a>範例  
 下列程式碼會實作本節的範例。  
  
 [!code-cs[csProgGuideNamedAndOptional#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_1.cs)]  
  
## <a name="optional-arguments"></a>選擇性引數  
 方法、建構函式、索引子或委派的定義可以指定其參數為必要項目或選擇項目。 任何呼叫都必須提供所有必要參數的引數，但可以省略選擇性參數的引數。  
  
 每個選擇性參數都有預設值，為其定義的一部分。 如不傳送該參數的任何引數，則使用預設值。 預設值必須是下列其中一個運算式類型︰  
  
-   常數運算式；  
  
-   `new ValType()` 形式的運算式，其中 `ValType` 是實值型別，例如 [enum](../../../csharp/language-reference/keywords/enum.md) 或 [struct](../../../csharp/programming-guide/classes-and-structs/structs.md)；  
  
-   [default(ValType)](../../../csharp/programming-guide/generics/default-keyword-in-generic-code.md) 形式的運算式，其中 `ValType` 是實值型別。  
  
 選擇性參數是定義在參數清單的結尾，在任何必要參數之後。 如果呼叫端為任何一個連續的選擇性參數提供引數，它就必須提供所有前面選擇性參數的引數。 不支援引數清單使用逗點分隔間距。 例如，在下列程式碼中，執行個體方法 `ExampleMethod` 使用一個必要參數及兩個選擇性參數來定義。  
  
 [!code-cs[csProgGuideNamedAndOptional#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_2.cs)]  
  
 以下呼叫 `ExampleMethod` 子句會造成編譯器錯誤，因為提供了第三個參數的引數，但未提供第二個參數的引數。  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 不過，如果您知道第三個參數的名稱，您可以使用具名引數來完成工作。  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 IntelliSense 使用括弧表示選擇性參數，如下圖所示。  
  
 ![IntelliSense 對於 ExampleMethod 方法的快速諮詢](../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional_Parameters")  
ExampleMethod 的選擇性參數  
  
> [!NOTE]
>  您也可以使用 .NET <xref:System.Runtime.InteropServices.OptionalAttribute> 類別宣告選擇性參數。 `OptionalAttribute` 參數不需要預設值。  
  
## <a name="example"></a>範例  
 在下例中，`ExampleClass` 的建構函式有一個參數，而它是選擇性的。 `ExampleMethod` 執行個體方法有一個必要參數 `required` 和兩個選擇性參數 `optionalstr` 及 `optionalint`。 `Main` 中的程式碼會示範叫用建構函式和方法的不同方式。  
  
 [!code-cs[csProgGuideNamedAndOptional#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_3.cs)]  
  
## <a name="com-interfaces"></a>COM 介面  
 具名和選擇性引數以及對動態物件和其他增強功能的支援，大幅改善與 COM API 的互通性，例如 Office Automation API。  
  
 例如，Microsoft Office Excel [Range Interface](http://go.microsoft.com/fwlink/?LinkId=148196) (範圍介面) 的 [AutoFormat](http://go.microsoft.com/fwlink/?LinkId=148201) 方法有七個參數，它們都是選擇性參數。 下圖會顯示這些參數。  
  
 ![IntelliSense 對於 AutoFormat 方法的快速諮詢](../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat_Parameters")  
AutoFormat 參數  
  
 在 C# 3.0 和舊版中，每個參數都需要引數，如下例所示。  
  
 [!code-cs[csProgGuideNamedAndOptional#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_4.cs)]  
  
 不過，您可以使用 C# 4.0 引入的具名和選擇性引數，大幅簡化對 `AutoFormat` 的呼叫。 如果您不想變更參數的預設值，具名和選擇性引數可讓您省略選擇性參數的引數。 在下列的呼叫中，只指定七個參數其中之一的值。  
  
 [!code-cs[csProgGuideNamedAndOptional#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_5.cs)]  
  
 如需詳細資訊和範例，請參閱[如何︰在 Office 程式設計中使用具名和選擇性引數](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)和[如何︰使用 Visual C# 功能存取 Office Interop 物件](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)。  
  
## <a name="overload-resolution"></a>Overload Resolution  
 使用具名和選擇性引數會以下列方式影響多載解析︰  
  
-   如果每個參數都是選擇性或為依名稱或位置對應要呼叫之陳述式的單一引數，且該引數可以轉換成參數的型別，則方法、索引子或建構函式就是執行的候選項目。  
  
-   如果找到多個候選項目，則慣用轉換的多載解析規則會套用至明確指定的引數。 會忽略選擇性參數的省略引數。  
  
-   如果兩個候選項目的評斷結果一樣好，則偏向沒有選擇性參數的候選項目，其會在呼叫中省略引數。 這是多載解析一般偏好參數較少之候選項目的結果。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [如何：在 Office 程式設計中使用具名和選擇性引數](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)   
 [使用動態型別](../../../csharp/programming-guide/types/using-type-dynamic.md)   
 [使用建構函式](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)   
 [使用索引子](../../../csharp/programming-guide/indexers/using-indexers.md)
