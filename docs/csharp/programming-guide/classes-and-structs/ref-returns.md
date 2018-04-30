---
title: ref 傳回值和 ref 區域變數 (C# 手冊)
description: 了解如何定義和使用 ref 傳回值和 ref 區域變數值
author: rpetrusha
ms.author: ronpet
ms.date: 04/04/2018
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: 57fa8f52320b30a1cb228b41e3f5e6655c235561
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ref-returns-and-ref-locals"></a>ref 傳回值和 ref 區域變數

從 C# 7 開始，C# 支援參考傳回值 (ref 傳回值)。 參考傳回值允許方法將變數參考 (而非值) 傳回給呼叫者。 呼叫者接著可以選擇將傳回的變數視為以傳值方式或以傳址方式傳回。 呼叫者可建立本身為參考傳回值的新變數，稱為 ref 區域變數。

## <a name="what-is-a-reference-return-value"></a>何謂參考傳回值？

大部分的開發人員都熟悉「以傳址方式」將引數傳遞給已呼叫方法。 所呼叫方法的引數清單包含以傳址方式傳遞的變數。 呼叫者會觀察到所呼叫方法對其值進行的任何變更。 「參考傳回值」表示方法會將「參考」 (或別名) 傳回給某個變數。 該變數的範圍必須包含方法。 該變數的存留期必須延伸到傳回方法。 呼叫者對方法的傳回值所進行的修改，是針對方法傳回的變數進行。

宣告方法傳回「參考傳回值」，表示方法會將別名傳回給變數。 此設計通常用於呼叫的程式碼應可透過別名來存取該變數 (包括進行修改) 時。 這樣一來，以傳址方式傳回的方法就不能有傳回型別 `void`。

方法可傳回為參考傳回值的運算式有一些限制。 限制包含：

- 傳回值必須有超過方法執行期間的存留期。 換句話說，它不能是將它傳回之方法中的區域變數。 它可以是類別的執行個體或靜態欄位，也可以是傳遞給方法的引數。 嘗試傳回區域變數會產生編譯器錯誤 CS8168「無法以傳址方式傳回本機 'obj'，因為其非參考本機」。

- 傳回值不能是常值 `null`。 傳回 `null` 會產生編譯器錯誤 CS8156「無法在此內容中使用運算式，因為其可能不會以傳址方式傳回」。

   使用 ref 傳回值的方法，可以將別名傳回給目前值為 Null (未具現化) 的變數，或是[可為 Null 的型別](../nullable-types/index.md)的實值型別。
 
- 傳回值不能是常數、列舉成員、屬性的以傳值方式傳回值，或是 `class` 或 `struct` 的方法。 違反此規則會產生編譯器錯誤 CS8156「無法在此內容中使用運算式，因為其可能不會以傳址方式傳回」。

此外，非同步方法上不允許參考傳回值。 在非同步方法完成執行之前，可能會傳回非同步方法，但其傳回值仍然為未知。
 
## <a name="defining-a-ref-return-value"></a>定義 ref 傳回值

將 [ref](../../language-reference/keywords/ref.md) 關鍵字新增至方法簽章的傳回型別，即可定義 ref 傳回值。 例如，下列簽章指出 `GetContactInformation` 屬性會將 `Person` 物件的參考傳回給呼叫者：

```csharp
public ref Person GetContactInformation(string fname, string lname);
```

此外，方法主體中每個 [return](../../language-reference/keywords/return.md) 陳述式所傳回的物件名稱前面必須加上 [ref](../../language-reference/keywords/ref.md) 關鍵字。 例如，下列 `return` 陳述式會傳回對名為 `p` 之 `Person` 物件的參考：

```csharp
return ref p;
```

## <a name="consuming-a-ref-return-value"></a>使用 ref 傳回值

ref 傳回值是在已呼叫方法的範圍中，另一個變數的別名。 您可以將任何使用 ref 傳回值的用法，解譯為使用別名所代表的變數：

- 當您指派其值時，是將值指派給別名的變數。
- 當您讀取其值時，是讀取別名的變數值。
- 如果您以「傳址」方式傳回它，就是將別名傳回至同一個變數。
- 如果您以「傳址」方式將它傳遞到另一個方法，就是將參考傳遞至別名的變數。
- 當您建立 [ref 區域變數](#ref-local)別名時，就是對相同變數建立新的別名。


## <a name="ref-locals"></a>ref 區域變數

假設 `GetContactInformation` 方法是宣告為 ref 傳回值：

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

傳值方式指派會讀取變數值，並將它指派給新的變數：

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

上述的指派將 `p` 宣告為區域變數。 其初始值的複製來源，是讀取 `GetContactInformation` 所傳回的值。 對 `p` 的任何後續指派將不會變更 `GetContactInformation` 傳回的變數值。 變數 `p` 不再是所傳回之變數的別名。

您宣告「ref 區域變數」以將別名複製到原始的值。 在下列指派中，`p` 是 `GetContactInformation` 所傳回之變數的別名。

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

後續 `p` 的使用方式與使用 `GetContactInformation` 傳回的變數相同，因為 `p` 是該變數的別名。 變更 `p` 也會變更 `GetContactInformation` 傳回的變數。

`ref` 關鍵字是用於區域變數宣告的前面「和」方法呼叫的前面。 

您可透過相同方式以參考存取值。 在某些情況下，以參考存取值會避免潛在過度浪費資源的複製作業，進而增加效能。 例如，下列陳述式示範了如何定義用於參考值的區域變數值。

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

區域變數宣告的前面「和」第二個範例中值的前面都會使用 `ref` 關鍵字。 無法在這兩個範例內的變數宣告和指派中同時包含 `ref` 關鍵字，會導致編譯器錯誤 CS8172「無法使用值將傳址變數初始化」。 

在 C# 7.3 之前，無法重新指派 ref 區域變數，以在初始化之後參照不同的儲存體。 已移除該限制。 下列範例示範重新指派：

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 ref 區域變數在宣告後仍然必須予以初始化。

## <a name="ref-returns-and-ref-locals-an-example"></a>ref 傳回值和 ref 區域變數：範例

下列範例定義 `NumberStore` 類別，以儲存整數值的陣列。 `FindNumber` 方法會以傳址方式傳回第一個數字，而此數字大於或等於傳遞為引數的數字。 如果數字未大於或等於引數，則方法會在索引 0 傳回數字。 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

下列範例會呼叫 `NumberStore.FindNumber` 方法來擷取大於或等於 16 的第一個值。 呼叫者接著會將方法所傳回的值加倍。 範例輸出顯示 `NumberStore` 執行個體之陣列項目值中所反映的變更。

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

如果不支援參考傳回值，則是透過傳回陣列項目和其值的索引來執行這類作業。 呼叫者接著可以使用這個索引，來修改不同方法呼叫中的值。 不過，呼叫者也可以修改要存取的索引，也可能修改其他陣列值。  

下列範例示範在 C# 7.3 之後如何重寫 `FindNumber` 方法以使用 ref 本機重新指派：

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

如果搜尋數目較接近陣列結尾，則這個第二個版本對較長的序列更具效率。

## <a name="see-also"></a>另請參閱

[ref 關鍵字](../../language-reference/keywords/ref.md)  
[具備實值型別的參考語意](../../../csharp/reference-semantics-with-value-types.md)
