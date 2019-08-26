---
title: 具名和選擇性引數 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- namedParameter_CSharpKeyword
- cs_namedParameter
helpviewer_keywords:
- parameters [C#], named
- named arguments [C#]
- arguments [C#], named
- optional arguments [C#]
- arguments [C#], optional
- parameters [C#], optional
- named and optional arguments [C#]
ms.assetid: 839c960c-c2dc-4d05-af4d-ca5428e54008
ms.openlocfilehash: ad3f7949e01a387c3c7de2a0702d11b106ea0040
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922202"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a>具名和選擇性引數 (C# 程式設計手冊)
C# 4 引進具名和選擇性引數。 「具名引數」  可讓您使用參數的名稱而非使用參數清單中的參數位置來關聯引數，指定特定參數的引數。 「選擇性引數」  可讓您省略某些參數的引數。 這兩種技巧都可以搭配方法、索引子、建構函式和委派使用。  
  
 當您使用具名和選擇性引數時，會依照引數清單中的引數顯示順序來評估引數，不是依照參數清單的順序。  
  
 具名和選擇性參數一起使用時，可讓您只為選擇性參數清單中的幾個參數提供引數。 這項功能大幅有助呼叫 COM 介面，例如 Microsoft Office Automation API。  
  
## <a name="named-arguments"></a>具名引數  
 具名引數讓您不需要記住或查詢呼叫方法參數清單中的參數順序。 參數名稱可以指定每個引數的參數。 例如，依函式定義的順序來傳送位置的引數，可透過標準方式呼叫可列印訂單詳細資料的函式 (例如，賣方名稱、訂單號碼和產品名稱)。
  
 `PrintOrderDetails("Gift Shop", 31, "Red Mug");`
  
 如果您不記得參數的順序，但知道它們的名稱，則可以依照任何順序傳送引數。  
  
 `PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");`
  
 `PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);`
  
 具名引數也藉由識別每個引數所代表的意義，改善程式碼的可讀性。 在下列範例方法中，`sellerName` 不可以為 Null 或空白字元。 因為 `sellerName` 和 `productName` 都是字串類型，所以可以使用具名引數來區分兩者，並減少讀取程式碼的任何人的混淆，而不是依位置傳送引數。
  
 在下列情況下，具名引數在與位置引數搭配使用時有效： 

- 它們的後面沒有任何位置引數，或

 `PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");`

- _從 C# 7.2 開始_，它們會用於正確的位置。 在下列範例中，`orderNum` 參數位於正確位置，但未明確命名。

 `PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");`
  
 不過，如果失序具名引數的後面接著位置引數，則無效。

 ```csharp
 // This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
 PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
 ```
  
## <a name="example"></a>範例  
 下列程式碼會實作本節的範例，以及一些其他範例。  
  
 [!code-csharp[csProgGuideNamedAndOptional#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/program.cs#1)]  
  
## <a name="optional-arguments"></a>選擇性引數  
 方法、建構函式、索引子或委派的定義可以指定其參數為必要項目或選擇項目。 任何呼叫都必須提供所有必要參數的引數，但可以省略選擇性參數的引數。  
  
 每個選擇性參數都有預設值，為其定義的一部分。 如不傳送該參數的任何引數，則使用預設值。 預設值必須是下列其中一個運算式類型︰  
  
- 常數運算式；  
  
- `new ValType()` 形式的運算式，其中 `ValType` 是實值型別，例如 [enum](../../language-reference/keywords/enum.md) 或 [struct](./structs.md)；  
  
- [default(ValType)](../../language-reference/operators/default.md) 形式的運算式，其中 `ValType` 是實值型別。  
  
 選擇性參數是定義在參數清單的結尾，在任何必要參數之後。 如果呼叫端為任何一個連續的選擇性參數提供引數，它就必須提供所有前面選擇性參數的引數。 不支援引數清單使用逗點分隔間距。 例如，在下列程式碼中，執行個體方法 `ExampleMethod` 使用一個必要參數及兩個選擇性參數來定義。  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]  
  
 以下呼叫 `ExampleMethod` 子句會造成編譯器錯誤，因為提供了第三個參數的引數，但未提供第二個參數的引數。  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 不過，如果您知道第三個參數的名稱，您可以使用具名引數來完成工作。  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 IntelliSense 使用括弧表示選擇性參數，如下圖所示：  
  
 ![顯示 ExampleMethod 方法之 IntelliSense 快速諮詢的螢幕擷取畫面。](./media/named-and-optional-arguments/optional-examplemethod-parameters.png)  
  
> [!NOTE]
> 您也可以使用 .NET <xref:System.Runtime.InteropServices.OptionalAttribute> 類別來宣告選擇性參數。 `OptionalAttribute` 參數不需要預設值。  
  
## <a name="example"></a>範例  
 在下例中，`ExampleClass` 的建構函式有一個參數，而它是選擇性的。 `ExampleMethod` 執行個體方法有一個必要參數 `required` 和兩個選擇性參數 `optionalstr` 及 `optionalint`。 `Main` 中的程式碼會示範叫用建構函式和方法的不同方式。  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]  
  
## <a name="com-interfaces"></a>COM 介面  
 具名和選擇性引數以及對動態物件和其他增強功能的支援，大幅改善與 COM API 的互通性，例如 Office Automation API。  
  
 例如，Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> 介面的 <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> 方法有七個參數，都是選擇性參數。 下圖會顯示這些參數：  
  
 ![顯示 AutoFormat 方法之 IntelliSense 快速諮詢的螢幕擷取畫面。](./media/named-and-optional-arguments/autoformat-method-parameters.png)  
  
 在 C# 3.0 和舊版中，每個參數都需要引數，如下例所示。  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]  
  
 不過，您可以使用 C# 4.0 引入的具名和選擇性引數，大幅簡化對 `AutoFormat` 的呼叫。 如果您不想變更參數的預設值，具名和選擇性引數可讓您省略選擇性參數的引數。 在下列的呼叫中，只指定七個參數其中之一的值。  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]  
  
 如需詳細資訊及範例，請參閱[如何：在 Office 程式設計中使用具名和選擇性引數](./how-to-use-named-and-optional-arguments-in-office-programming.md)和[如何：使用 Visual C# 功能存取 Office Interop 物件](../interop/how-to-access-office-onterop-objects.md)。  
  
## <a name="overload-resolution"></a>Overload Resolution  
 使用具名和選擇性引數會以下列方式影響多載解析︰  
  
- 如果每個參數都是選擇性或為依名稱或位置對應要呼叫之陳述式的單一引數，且該引數可以轉換成參數的型別，則方法、索引子或建構函式就是執行的候選項目。  
  
- 如果找到多個候選項目，則慣用轉換的多載解析規則會套用至明確指定的引數。 會忽略選擇性參數的省略引數。  
  
- 如果兩個候選項目的評斷結果一樣好，則偏向沒有選擇性參數的候選項目，其會在呼叫中省略引數。 這是多載解析一般偏好參數較少之候選項目的結果。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [如何：在 Office 程式設計中使用具名和選擇性引數](./how-to-use-named-and-optional-arguments-in-office-programming.md)
- [使用動態型別](../types/using-type-dynamic.md)
- [使用建構函式](./using-constructors.md)
- [使用索引子](../indexers/using-indexers.md)
