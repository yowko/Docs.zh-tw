---
title: 使用索引子 - C# 程式設計指南
description: '瞭解如何在 c # 中宣告和使用類別、結構或介面的索引子。 本文包含範例程式碼。'
ms.date: 07/15/2020
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: a8a9e05c1d2e44841177a924c6ff51c6c9e6a05a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301862"
---
# <a name="using-indexers-c-programming-guide"></a>使用索引子 (C# 程式設計手冊)

索引子是一種語法便利性，可讓您建立用戶端應用程式可當做陣列存取的[類別](../../language-reference/keywords/class.md)、[結構](../../language-reference/builtin-types/struct.md)或[介面](../../language-reference/keywords/interface.md)。 編譯器會產生 `Item` 屬性（如果存在，則為另一個名稱為的屬性 <xref:System.Runtime.CompilerServices.IndexerNameAttribute> ），以及適當的存取子方法。 索引子最常實作於類型中，而類型的主要用途是封裝內部集合或陣列。 例如，假設您有一個類別，代表在24小時期間內，以 `TempRecord` 10 個不同時間記錄的華氏溫度。 類別包含用 `temps` `float[]` 來儲存溫度值的類型陣列。 透過在此類別中實作索引子，用戶端能以 `TempRecord` 執行個體中 `float temp = tempRecord[4]` 的形式 (而非 `float temp = tempRecord.temps[4]`) 來存取溫度。 索引子標記法不只會簡化用戶端應用程式的語法;它也讓其他開發人員瞭解類別和其用途更直覺化。

若要在類別或結構上宣告索引子，請使用 [this](../../language-reference/keywords/this.md) 關鍵字，如下列範例所示：

```csharp
// Indexer declaration
public int this[int index]
{
    // get and set accessors
}
```

> [!IMPORTANT]
> 宣告索引子將會在物件上自動產生名為的屬性 `Item` 。 `Item`無法直接從實例[成員存取運算式](../../language-reference/operators/member-access-operators.md#member-access-expression-)存取屬性。 此外，如果您 `Item` 使用索引子將自己的屬性新增至物件，將會收到[CS0102 編譯器錯誤](../../misc/cs0102.md)。 若要避免這個錯誤，請使用 <xref:System.Runtime.CompilerServices.IndexerNameAttribute> 重新命名索引子，如下所述。

## <a name="remarks"></a>備註

索引子類型和其參數類型至少必須可以像索引子本身一樣地存取。 如需存取範圍層級的詳細資訊，請參閱[存取修飾詞](../../language-reference/keywords/access-modifiers.md)。

如需如何搭配使用索引子與介面的詳細資訊，請參閱[介面索引子](./indexers-in-interfaces.md)。

索引子的簽章包含其型式參數的數目和類型。 它不包含索引子類型或正式參數的名稱。 如果您在相同的類別中宣告多個索引子，則它們必須具有不同的簽章。

索引子值不會分類為變數；因此，您無法將索引子值傳遞為 [ref](../../language-reference/keywords/ref.md) 或 [out](../../language-reference/keywords/out-parameter-modifier.md) 參數。

若要以其他語言可使用的名稱提供索引子，請使用 <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>，如下列範例所示：

```csharp
// Indexer declaration
[System.Runtime.CompilerServices.IndexerName("TheItem")]
public int this[int index]
{
    // get and set accessors
}
```

此索引子會有名稱 `TheItem` ，因為它是由索引子名稱屬性所覆寫。 根據預設，索引子名稱是 `Item` 。

## <a name="example-1"></a>範例 1

下列範例示範如何宣告私用陣列欄位 `temps` 和索引子。 索引子可讓您直接存取執行個體 `tempRecord[i]`。 使用索引子的替代方式是將陣列宣告為 [public](../../language-reference/keywords/public.md) 成員，並直接存取其成員 `tempRecord.temps[i]`。

:::code language="csharp" source="snippets/Temperatures/TempRecord.cs":::

請注意，評估索引子的存取時 (例如，在 `Console.Write` 陳述式中)，會叫用 [get](../../language-reference/keywords/get.md) 存取子。 因此，如果沒有 `get` 存取子，就會發生編譯時間錯誤。

:::code language="csharp" source="snippets/Temperatures/Program.cs":::

## <a name="indexing-using-other-values"></a>使用其他值編製索引

C# 不會將索引子參數類型限制為整數。 例如，搭配使用字串與索引子可能十分有用。 在集合中搜尋字串，並傳回適當的值，可能會實作這類索引子。 當存取子可以多載時，字串和整數版本可以並存。

## <a name="example-2"></a>範例 2

下列範例宣告的類別會儲存週中的日。 `get` 存取子接受字串 (日的名稱)，並傳回對應的整數。 例如，"Sunday" 會傳回 0，"Monday" 會傳回 1，依此類推。

:::code language="csharp" source="snippets/StringIndexers/DayCollection.cs":::

### <a name="consuming-example-2"></a>使用範例2

:::code language="csharp" source="snippets/StringIndexers/Program.cs":::

## <a name="example-3"></a>範例 3

下列範例會宣告一個類別，它會使用列舉來儲存一周的哪幾天 <xref:System.DayOfWeek?displayProperty=fullName> 。 `get`存取子會接受 `DayOfWeek` ，其值為 day，並傳回對應的整數。 例如，會傳回 `DayOfWeek.Sunday` 0，傳回 `DayOfWeek.Monday` 1，依此類推。

:::code language="csharp" source="snippets/DayOfWeekIndexers/DayOfWeekCollection.cs":::

### <a name="consuming-example-3"></a>使用範例3

:::code language="csharp" source="snippets/DayOfWeekIndexers/Program.cs":::

## <a name="robust-programming"></a>穩固程式設計

有兩種主要的方式可以改善索引子的安全性和可靠性：

- 請務必包含某種類型的錯誤處理策略來處理用戶端程式碼傳入無效索引值的機會。 在本主題稍早的第一個範例中，TempRecord 類別提供 Length 屬性，以讓用戶端程式碼先確認輸入，再將其傳遞給索引子。 您也可以將錯誤處理程式碼放在索引子本身內。 請務必為使用者記載您在索引子存取子內擲回的任何例外狀況。

- 將 [get](../../language-reference/keywords/get.md) 與 [set](../../language-reference/keywords/set.md) 存取子的存取範圍設定為合理限制。 這對 `set` 存取子特別重要。 如需詳細資訊，請參閱[限制存取子的存取範圍](../classes-and-structs/restricting-accessor-accessibility.md)。

## <a name="see-also"></a>另請參閱

- [C # 程式設計指南](../index.md)
- [索引子](./index.md)
- [屬性](../classes-and-structs/properties.md)
