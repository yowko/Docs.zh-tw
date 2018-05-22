---
title: 屬性
description: 了解 C# 屬性，其中包含驗證、計算值、延遲評估和屬性變更通知的功能。
ms.date: 04/25/2018
ms.openlocfilehash: d4fa7b6117bec63c41318dd4bcc3850ce55a5907
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="properties"></a>屬性

屬性是 C# 中的頭等成員。 該語言所定義的語法，可讓開發人員撰寫正確表示其設計意圖的程式碼。

屬性在存取時的行為與欄位一樣。
不過不同於欄位，屬性是透過存取子來實作，這些存取子會定義存取或指派屬性時所執行的陳述式。

## <a name="property-syntax"></a>屬性語法

屬性的語法是欄位的自然延伸。 欄位可定義儲存位置：

[!code-csharp[Person class with public fields](../../samples/snippets/csharp/properties/Person.cs#1)]

屬性定義包含 `get` 和 `set` 存取子的宣告，以擷取和指派該屬性的值：

[!code-csharp[Person class with public properties](../../samples/snippets/csharp/properties/Person.cs#2)]

以上所示的語法為「Auto 屬性」語法。 編譯器會為欄位產生儲存位置，以備份此屬性。 編譯器也會實作 `get` 和 `set` 存取子的主體。

有時候，您需要將屬性初始化為其類型的預設值以外的值。  C# 可讓您在屬性的右括弧之後設定一個值，以執行上述作業。 您可能偏好將 `FirstName` 屬性的初始值設為空字串而非 `null`。 您可依下列方式來進行上述設定：

[!code-csharp[Person class with properties and initializer](../../samples/snippets/csharp/properties/Person.cs#3)]

如您在本文稍後所見，特定的初始化最適合用於唯讀屬性。

您也可以自行定義儲存體，如下所示：

[!code-csharp[Person class with properties and backing field](../../samples/snippets/csharp/properties/Person.cs#4)]

當屬性實作為單一運算式時，您可以針對 getter 或 setter 使用「運算式主體成員」：

[!code-csharp[Person class with properties and expression bodied getters and setters](../../samples/snippets/csharp/properties/Person.cs#5)]

本文會在適用的所有情況下使用這種簡化語法。

以上所示的屬性定義為讀寫屬性。 請注意 set 存取子中的關鍵字 `value`。 `set` 存取子一定會有一個名為 `value` 的參數。 `get` 存取子必須傳回可轉換成屬性類型 (在此範例中為 `string`) 的值。

這是此語法的基本概念。 還有許多不同的變化，可支援各種不同的設計慣例。 讓我們探索並了解各自的語法選項。

## <a name="scenarios"></a>案例

上述範例顯示屬性定義的一個最簡單案例，那就是不具驗證的讀/寫屬性。 藉由在 `get` 和 `set` 存取子中撰寫您所需的程式碼，您就可以建立許多不同的案例。

### <a name="validation"></a>驗證

您可以在 `set` 存取子中撰寫程式碼，以確保由屬性所表示的值一定有效。 例如，假設 `Person` 類別的一項規則是名稱不可為空白或空白字元。 您可以撰寫如下：

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#6)]

使用 `throw` 運算式作為屬性 setter 驗證的一部分，即可簡化上述範例：

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#7)]

上述範例會強制執行第一個名稱不得為空白或空白字元的規則。 如果開發人員撰寫

```csharp
hero.FirstName = "";
```

該指派會擲回 `ArgumentException`。 由於屬性的 set 存取子必須有無效的傳回型別，因此您擲回一個例外狀況來回報 set 存取子中發生錯誤。

您可以將同一個語法擴充為案例所需的任何語法。 您可以檢查不同屬性之間的關聯性，或針對任何外部條件進行驗證。 任何有效的 C# 陳述式在屬性存取子中都是有效的。

### <a name="read-only"></a>唯讀

到目前為止，您所看到的所有屬性定義都是具有 public 存取子的讀取/寫入屬性。 這不是屬性唯一有效的存取範圍。
您可以建立唯讀屬性，或是為 set 和 get 存取子提供不同的存取範圍。 假設您的 `Person` 類別只能允許從該類別中的其他方法變更 `FirstName` 屬性的值。 您可以為 set 存取子提供 `private` 存取範圍，而不是 `public`：

[!code-csharp[Using a private setter for a publicly readonly property](../../samples/snippets/csharp/properties/Person.cs#8)]

現在，`FirstName` 屬性可從任何程式碼存取，但只能從 `Person` 類別中的其他程式碼指派。

您可以將任何嚴格的存取修飾詞新增至 set 或 get 存取子。 您放在個別存取子上的任何存取修飾詞，必須比屬性定義上的存取修飾詞具有更多限制。 由於 `FirstName` 屬性為 `public`，但 set 存取子為 `private`，因此上述範例合法。 您無法使用 `public` 存取子宣告 `private` 屬性。 屬性宣告也可以宣告為 `protected`、`internal`、`protected internal`，甚至是 `private`。

您也可以將更嚴格的修飾詞放在 `get` 存取子上。 例如，您可能會有 `public` 屬性，但將 `get` 存取子限制為 `private`。 這種情況在實務上很罕見。

您也可以限制屬性的修改，只在建構函式或屬性的初始設定式中加以設定。 您可以修改 `Person` 類別，如下所示：

[!code-csharp[A readonly auto implemented property](../../samples/snippets/csharp/properties/Person.cs#9)]

這項功能最常用於初始化會公開為唯讀屬性的集合：

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a>計算屬性

屬性不需要直接傳回成員欄位的值。 您可以建立傳回計算值的屬性。 讓我們展開 `Person` 物件，以傳回串連名字和姓氏計算得到的完整名稱：

[!code-csharp[A computed property](../../samples/snippets/csharp/properties/Person.cs#10)]

上述範例使用[字串內插補點](../csharp/language-reference/tokens/interpolated.md)功能，來建立完整名稱的格式化字串。

您也可以使用「運算式主體成員」，以提供更簡潔的方法來建立計算的 `FullName` 屬性：

[!code-csharp[A computed property using an expression bodied member](../../samples/snippets/csharp/properties/Person.cs#11)]

「運算式主體成員」使用「Lambda 運算式」語法來定義包含單一運算式的方法。 在這裡，該運算式會傳回 person 物件的完整名稱。

### <a name="cached-evaluated-properties"></a>快取的評估屬性

您可以混合計算屬性與儲存體的概念，然後建立「快取的評估屬性」。  例如，您可以更新 `FullName` 屬性，只在第一次存取時設定字串格式：

[!code-csharp[Caching the value of a computed property](../../samples/snippets/csharp/properties/Person.cs#12)]

不過，上述程式碼含有 Bug。 如果程式碼更新 `FirstName` 或 `LastName` 屬性的值，先前評估的 `fullName` 欄位會無效。 您可以修改 `FirstName` 和 `LastName` 屬性的 `set` 存取子，以便重新計算 `fullName` 欄位：

[!code-csharp[Invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#13)]

這個最終版本只會在必要時評估 `FullName` 屬性。
如果先前計算的版本有效，則會使用該版本。 如果另一個狀態變更使得先前計算的版本失效，則會重新計算。 使用此類別的開發人員不需要知道實作的細節。 這些內部變更不會影響 Person 物件的使用。 這是使用屬性來公開物件之資料成員的主要原因。

### <a name="attaching-attributes-to-auto-implemented-properties"></a>將屬性 (attribute) 附加至自動實作屬性 (property)

從 C# 7.3 開始，可以將欄位屬性 (attribute) 附加至自動實作屬性 (property) 中編譯器產生的支援欄位。 例如，考慮要修訂可新增唯一整數 `Id` 屬性的 `Person` 類別。
您可以使用自動實作屬性撰寫 `Id` 屬性，但是您的設計不會要求保存 `Id` 屬性。 <xref:System.NonSerializedAttribute> 只能附加至欄位，而不是屬性。 您可以藉由在屬性 (attribute) 上使用 `field:` 指定名稱，將 <xref:System.NonSerializedAttribute> 附加至 `Id` 屬性 (property) 的支援欄位，如下列範例所示：

[!code-csharp[Attaching attributes to a backing field](../../samples/snippets/csharp/properties/Person.cs#14)]

此技術適用於任何您附加至自動實作屬性 (property) 支援欄位的屬性 (attribute)。

### <a name="implementing-inotifypropertychanged"></a>實作 INotifyPropertyChanged

您必須在屬性存取子中撰寫程式碼的最後一個案例是為了支援 <xref:System.ComponentModel.INotifyPropertyChanged> 介面，該介面可用來通知資料繫結用戶端已有值變更。 當屬性的值變更時，物件會引發 <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged?displayProperty=nameWithType> 事件以指出此變更。 資料繫結程式庫會接著根據該項變更來更新顯示項目。 下列程式碼示範如何針對此 person 類別的 `FirstName` 屬性實作 `INotifyPropertyChanged`。

[!code-csharp[invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#15)]

`?.` 運算子稱為「null 條件運算子」。 它會檢查是否有 null 參考，再評估運算子的右邊。 最後結果是，如果沒有 `PropertyChanged` 事件的訂閱者，則不會執行引發事件的程式碼。 在此情況下，它會擲回 `NullReferenceException` 而不進行這項檢查。 如需詳細資訊，請參閱 [`events`](delegates-events.md)。 此範例也會使用新的 `nameof` 運算子，從屬性名稱符號轉換成其文字表示。
使用 `nameof` 可減少鍵入錯誤屬性名稱時所發生的錯誤。

同樣地，實作 <xref:System.ComponentModel.INotifyPropertyChanged> 是您可以在存取子中撰寫程式碼來支援所需案例的範例。

## <a name="summing-up"></a>總結

屬性是類別或物件中的一種智慧型欄位。 從物件外部來看，屬性就像是物件中的欄位。 不過，您可以使用完整的 C# 功能選擇區來實作屬性。
您可以提供驗證、不同的存取範圍、延遲評估，或是您的案例所需的任何需求。
