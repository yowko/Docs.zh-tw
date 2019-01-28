---
title: 匿名類型 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#]
- C# Language, anonymous types
ms.assetid: 59c9d7a4-3b0e-475e-b620-0ab86c088e9b
ms.openlocfilehash: 179e49f44b2dbf711dae2ce81a1ef14815b7d18a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729755"
---
# <a name="anonymous-types-c-programming-guide"></a>匿名類型 (C# 程式設計手冊)
匿名類型提供一個便利的方法，將一組唯讀屬性封裝成一個物件，而不需要事先明確定義類型。 類型名稱會由編譯器產生，並且無法在原始程式碼層級使用。 每個屬性的類型會由編譯器推斷。  
  
 您可以搭配物件初始設定式使用 [new](../../../csharp/language-reference/keywords/new.md) 運算子，來建立匿名型別。 如需物件初始設定式的詳細資訊，請參閱[物件和集合初始設定式](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)。  
  
 下列範例顯示以兩個名為 `Amount` 和 `Message` 的屬性初始化的匿名類型。  
  
```csharp  
var v = new { Amount = 108, Message = "Hello" };  
  
// Rest the mouse pointer over v.Amount and v.Message in the following  
// statement to verify that their inferred types are int and string.  
Console.WriteLine(v.Amount + v.Message);  
```  
  
 您通常可以在查詢運算式的 [select](../../../csharp/language-reference/keywords/select-clause.md) 子句中使用匿名型別，以從來源序列中的每個物件傳回屬性子集。 如需查詢的詳細資訊，請參閱 [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md)。  
  
 匿名類型包含一個或多個公用唯讀屬性。 其他類型的類別成員 (例如方法或事件) 則無效。 用於初始化屬性的運算式不可以是 `null`、匿名函式或指標類型。  
  
 最常見的情況是使用其他類型的屬性來初始化匿名類型。 下列範例假設存在一個名為 `Product` 的類別。 `Product` 類別包含 `Color` 和 `Price` 屬性，以及您不感興趣的其他屬性。 變數 `products` 是 `Product` 物件的集合。 匿名類型宣告的開頭為 `new` 關鍵字。 宣告會初始化新類型，只使用 `Product` 中的兩個屬性。 這會使查詢中傳回較小的資料量。  
  
 如果未在匿名類型中指定成員名稱，編譯器會為匿名類型成員指定與用於初始化類型之屬性相同的名稱。 您必須為以運算式初始化的屬性提供一個名稱，如上述範例所示。 在下列範例中，匿名類型的屬性名稱是 `Color` 和 `Price`。  
  
 [!code-csharp[csRef30Features#81](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/anonymous-types_1.cs)]  
  
 一般而言，當您使用匿名型別初始化變數時，您可以使用 [var](../../../csharp/language-reference/keywords/var.md) 將變數宣告為隱含型別區域變數。 由於只有編譯器可以存取匿名類型的基本名稱，因此無法在變數宣告中指定類型名稱。 如需 `var` 的詳細資訊，請參閱[隱含類型區域變數](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)。  
  
 您可以如下列範例所示，合併隱含類型區域變數和隱含類型陣列，以建立匿名類型項目的陣列。  
  
```csharp  
var anonArray = new[] { new { name = "apple", diam = 4 }, new { name = "grape", diam = 1 }};  
```  
  
## <a name="remarks"></a>備註  
 匿名型別是直接衍生自 [object](../../../csharp/language-reference/keywords/object.md)，並且無法轉換成 [object](../../../csharp/language-reference/keywords/object.md) 以外之任何類型的 [class](../../../csharp/language-reference/keywords/class.md) 類型。 編譯器提供每種匿名類型的名稱，不過您的應用程式無法存取此名稱。 對 Common Language Runtime 來說，匿名類型與其他任何參考類型並無不同。  
  
 如果組件中有兩個或多個匿名物件初始設定式，指定了順序相同並具有相同名稱和類型的屬性序列，編譯器會將這些物件視為相同類型的執行個體。 這些物件會共用編譯器產生的相同類型資訊。  
  
 您無法將欄位、屬性、事件或方法的傳回類型，宣告為具有匿名類型。 同樣地，您無法將方法、屬性、建構函式或索引子的型式參數宣告為具有匿名類型。 若要以方法引數的形式來傳遞匿名類型或含有匿名類型的集合，您可以將參數宣告為 object 類型。 但是，這樣做將失去強式類型的目的。 如果您必須在方法界限外儲存或傳遞查詢結果，請考慮使用一般具名結構或類別來取代匿名類型。  
  
 由於匿名類型上的 <xref:System.Object.Equals%2A> 和 <xref:System.Object.GetHashCode%2A> 方法會以屬性的 `Equals` 和 `GetHashCode` 方法來定義，相同匿名類型的兩個執行個體僅在其所有屬性都相等時，這兩個執行個體才相等。  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [物件和集合初始設定式](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
- [開始使用 C# 中的 LINQ](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
- [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md)
