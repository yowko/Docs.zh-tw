---
title: "ref 傳回值和 ref 區域變數 (C# 手冊)"
description: "了解如何定義和使用 ref 傳回值和 ref 區域變數值"
author: rpetrusha
ms.author: ronpet
ms.date: 05/30/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 18cf7a4b-29f0-4b14-85b8-80af754aabd8
ms.translationtype: HT
ms.sourcegitcommit: 4582cb0ee091526423cce3fc1d8243029f34f59c
ms.openlocfilehash: 3f2ee35db5b77efcce629b6315060a723429b19c
ms.contentlocale: zh-tw
ms.lasthandoff: 08/16/2017

---
# <a name="ref-returns-and-ref-locals"></a>ref 傳回值和 ref 區域變數

從 C# 7 開始，C# 支援參考傳回值 (ref 傳回值)。 參考傳回值允許方法將物件參考而非值傳回給呼叫者。 呼叫者接著可以選擇將傳回的物件視為已傳回，就像已以傳值方式或以傳址方式傳回它一樣。 呼叫者處理為參考而非值，並以傳址方式傳回的值，即 ref 區域變數。

## <a name="what-is-a-reference-return-value"></a>何謂參考傳回值？

大部分的開發人員都熟悉「以傳址方式」將引數傳遞給已呼叫方法。 已呼叫方法的引數清單包含以傳址方式傳遞的值，而且已呼叫方法對其值進行的任何變更都會傳回給呼叫者。 「參考傳回值」則相反：

- 已呼叫方法的傳回值 (而非傳遞給它的引數) 是參考。

- 呼叫者 (而非已呼叫方法) 可以修改方法所傳回的值。

- 方法的呼叫者傳回值修改會反映在呼叫其方法之物件的狀態中，而不是反映在呼叫者之物件狀態中的引數修改。

參考傳回值可以產生更精簡的程式碼，以及允許物件只公開個別資料項目，例如呼叫者感興趣的陣列元素。 這可降低呼叫者不小心修改物件狀態的可能性。

方法可傳回為參考傳回值的值有一些限制。 這些活動包括：

- 傳回值不能是 `void`。 嘗試定義具有 `void` 參考傳回值的方法會產生編譯器錯誤 CS1547「在此內容中不可使用關鍵字 'void'」。
 
- 傳回值不能是傳回它之方法中的區域變數；它的範圍必須位在傳回它的方法外部。 它可以是類別的執行個體或靜態欄位，也可以是傳遞給方法的引數。 嘗試傳回區域變數會產生編譯器錯誤 CS8168「無法以傳址方式傳回本機 'obj'，因為其非參考本機」。

- 傳回值不能是 `null`。 嘗試傳回 `null` 會產生編譯器錯誤 CS8156「無法在此內容中使用運算式，因為其可能不會以傳址方式傳回」。

   如果具有 ref 傳回值的方法需要傳回 Null 值，您可以傳回參考型別的 Null (未具現化) 值或實值型別的[可為 Null 的類型](../nullable-types/index.md)。
 
- 傳回值不能是常數、列舉成員，或是 `class` 或 `struct` 的屬性。 嘗試傳回這些會產生編譯器錯誤 CS8156「無法在此內容中使用運算式，因為其可能不會以傳址方式傳回」。

此外，因為非同步方法可能會在完成執行之前傳回，但仍未知其傳回值，所以非同步方法並不允許參考傳回值。
 
## <a name="defining-a-ref-return-value"></a>定義 ref 傳回值

將 [ref](../../language-reference/keywords/ref.md) 關鍵字新增至方法簽章的傳回型別，即可定義 ref 傳回值。 例如，下列簽章指出 `GetContactInformation` 屬性會將 `Person` 物件的參考傳回給呼叫者：

```csharp
public ref Person GetContactInformation(string fname, string lname);
```

此外，方法主體中每個 [return](../../language-reference/keywords/return.md) 陳述式所傳回的物件名稱前面必須加上 [ref](../../language-reference/keywords/ref.md) 關鍵字。 例如，下列 `return` 陳述式會以傳址方式傳回名為 `p` 的 `Person` 物件：

```csharp
return ref p;
```

## <a name="consuming-a-ref-return-value"></a>使用 ref 傳回值

呼叫者可以使用兩種方式之一來處理 ref 傳回值：

- 作為從方法以傳值方式傳回的一般值。 呼叫者可以選擇忽略傳回值是參考傳回值。 在此情況下，對方法呼叫所傳回的值進行的任何變更都不會反映在已呼叫類型的狀態中。 如果傳回值是實值型別，則對方法呼叫所傳回的值進行的任何變更都不會反映在已呼叫類型的狀態中。

- 作為參考傳回值。 呼叫者必須定義將參考傳回值指派為 [ref 區域變數](#ref-local)的變數，而且針對方法呼叫所傳回之值的任何變更都會反映在已呼叫類型的狀態中。 

## <a name="ref-locals"></a>ref 區域變數

若要將參考傳回值處理為參考，呼叫者必須使用 `ref` 關鍵字將值宣告為 *ref 區域變數*。 例如，如果 `Person.GetContactInfomation` 方法所傳回的值是要用作參考，而非值，則方法呼叫會顯示為：

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

請注意，`ref` 關鍵字是用於區域變數宣告的前面「和」方法呼叫的前面。 無法在變數宣告和指派中同時包含 `ref` 關鍵字，會導致編譯器錯誤 CS8172「無法使用值將傳址變數初始化」。 
 
對方法所傳回 `Person` 物件的後續變更會反映在 `contacts` 物件中。

如果未使用 `ref` 關鍵字將 `p` 定義為 ref 區域變數，則呼叫者對 `p` 進行的任何變更都不會反映在 `contacts` 物件中。
 
## <a name="ref-returns-and-ref-locals-an-example"></a>ref 傳回值和 ref 區域變數：範例

下列範例定義 `NumberStore` 類別，以儲存整數值的陣列。 `FindNumber` 方法會以傳址方式傳回第一個數字，而此數字大於或等於傳遞為引數的數字。 如果數字未大於或等於引數，則方法會在索引 0 傳回數字。 

[!CODE-cs[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#1)]

下列範例會呼叫 `NumberStore.FindNumber` 方法來擷取大於或等於 16 的第一個值。 呼叫者接著會將方法所傳回的值加倍。 如範例輸出所示，這項變更會反映在 `NumberStore` 執行個體的陣列元素值中。

[!CODE-cs[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#2)]

如果不支援參考傳回值，則通常是透過傳回陣列元素和其值的索引來執行這類作業。 呼叫者接著可以使用這個索引，來修改不同方法呼叫中的值。 不過，呼叫者也可以修改要存取的索引，也可能修改其他陣列值。  
 
## <a name="see-also"></a>請參閱

[ref 關鍵字](../../language-reference/keywords/ref.md)

