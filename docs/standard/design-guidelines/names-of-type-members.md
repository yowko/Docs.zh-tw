---
title: 類型成員名稱
description: 瞭解如何在 .NET 中命名類型成員的指導方針，例如方法、屬性、事件和欄位。
ms.date: 10/22/2008
helpviewer_keywords:
- events [.NET Framework], names
- methods [.NET Framework], names
- type members
- properties [.NET Framework], names
- fields, names
- field names
- names [.NET Framework], type members
- members [.NET Framework], type
ms.assetid: af5a0903-36af-4c2a-b848-cf959affeaa5
ms.openlocfilehash: 409e881198a359fa28356e22ea73d5b724742a0d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706472"
---
# <a name="names-of-type-members"></a>類型成員名稱

類型由成員組成：方法、屬性、事件、建構函式及欄位。 下列各節會描述為類型成員命名的方針。

## <a name="names-of-methods"></a>方法的名稱

 因為方法是採取動作的手段，所以設計方針會要求方法名稱為動詞或動詞片語。 遵循此方針也能用來區別方法名稱與屬性和類型名稱，後兩者為名詞或形容詞。

 ✔️確實提供的方法名稱為動詞或動詞片語。

```csharp
public class String {
    public int CompareTo(...);
    public string[] Split(...);
    public string Trim();
}
```

## <a name="names-of-properties"></a>屬性的名稱

 不同於其他成員，屬性應有名詞片語或形容詞名稱。 這是因為屬性會參考資料，而屬性的名稱則會反映這點。 PascalCasing 總是會用作屬性名稱。

 ✔️使用名詞、名詞片語或形容詞來命名屬性。

 ❌ 沒有符合 "Get" 方法名稱的屬性，如下列範例所示：

 `public string TextWriter { get {...} set {...} }` `public string GetTextWriter(int value) { ... }`

 此模式通常表示屬性應該真的是方法。

 ✔️使用複數片語來命名集合屬性，以描述集合中的專案，而不是使用後面接著 "List" 或 "Collection" 的單數片語。

 ✔️使用肯定片語來命名布林值屬性， (`CanSeek` 而不是 `CantSeek`) 。 （選擇性）您也可以在布林值屬性的前面加上「是」、「可以」或「有」，但只在其新增值的位置。

 ✔️請考慮為屬性提供與其類型相同的名稱。

 例如，下列屬性正確地取得並設定了名為 `Color` 的數值，所以屬性名稱即為 `Color`：

```csharp
public enum Color {...}
public class Control {
    public Color Color { get {...} set {...} }
}
```

## <a name="names-of-events"></a>事件的名稱

 事件一律會參考某些動作，不論該動作正在發生或已發生。 因此，如同方法一般，事件應以動詞為名，且應使用動詞時態來指出事件發生的時間。

 ✔️使用動詞或動詞片語來命名事件。

 範例包括 `Clicked`、`Painting`、`DroppedDown` 等等。

 ✔️會使用目前和過去的時態，為事件名稱提供之前和之後的概念。

 例如，在視窗關閉前發生的關閉事件會稱作 `Closing`，而在視窗關閉後發生的事件則稱作 `Closed`。

 ❌ 請勿使用 "Before" 或 "After" 前置詞或 postfixes 來表示前置和後置事件。 使用如同敘述的現在與過去時態。

 ✔️使用 "EventHandler" 後置詞 (委派做為事件種類) 的委派，如下列範例所示：

 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`

 ✔️ `sender` `e` 在事件處理常式中使用兩個名為和的參數。

 傳送者參數代表引發事件的物件。 傳送者參數的類型通常為 `object`，即使可採用更明確的類型時也一樣。

 ✔️使用 "EventArgs" 尾碼來命名事件引數類別。

## <a name="names-of-fields"></a>欄位的名稱

 欄位命名方針適用於靜態公開和保護的欄位。 方針並未涵蓋內部與私人的欄位，且[成員設計方針](member.md)並不允許公開或保護的執行個體欄位。

 ✔️在功能變數名稱中使用 PascalCasing。

 ✔️使用名詞、名詞片語或形容詞來命名欄位。

 ❌ 請勿在功能變數名稱中使用前置詞。

 例如，不要使用 "g_" 或 "s_" 來表示靜態欄位。

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>另請參閱

- [架構設計指導方針](index.md)
- [命名指導方針](naming-guidelines.md)
