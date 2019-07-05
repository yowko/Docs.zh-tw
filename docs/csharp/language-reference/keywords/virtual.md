---
title: virtual - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 2568eed5a889f6c03e237875194b8adcb9334ef7
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2019
ms.locfileid: "67401817"
---
# <a name="virtual-c-reference"></a>virtual (C# 參考)

`virtual` 關鍵字可用來修改方法、屬性、索引子或事件宣告，並可在衍生類別中受到覆寫。 例如，繼承這個方法的任何類別均可將其覆寫：

```csharp
public virtual double Area() 
{
    return x * y;
}
```

衍生類別中的[覆寫成員](override.md)可以變更虛擬成員的實作。 如需如何使用 `virtual` 關鍵字的詳細資訊，請參閱[使用 Override 和 New 關鍵字進行版本控制](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)以及[了解使用 Override 和 New 關鍵字的時機](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)。

## <a name="remarks"></a>備註

叫用虛擬方法時，系統會檢查覆寫成員的物件執行階段類型。 系統會呼叫最多衍生類別中的覆寫成員，且該成員可能是原始的成員 (若沒有任何衍生的類別已覆寫該成員的話)。

此方法預設為非虛擬的方法。 您無法覆寫非虛擬的方法。

您不能搭配使用 `virtual` 修飾詞和 `static`、`abstract`、`private` 或 `override` 修飾詞。 下列範例說明虛擬屬性：

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

除了宣告和引動過程語法的差異之外，虛擬屬性的行為類似抽象方法。

- 在靜態屬性上使用 `virtual` 修飾詞是錯誤的。

- 您可以納入使用 `override` 修飾詞的屬性宣告，以覆寫衍生類別中的虛擬繼承屬性。

## <a name="example"></a>範例

在此範例中，`Shape` 類別包含 `x` 和 `y` 這兩個座標，以及 `Area()` 虛擬方法。 `Circle`、`Cylinder` 和 `Sphere` 這類不同圖形類別會繼承 `Shape` 類別，而系統會進行每一個圖形的介面區計算。 每個衍生類別有其各自的 `Area()` 覆寫實作。

請注意，`Circle`、`Sphere` 和 `Cylinder` 繼承類別都會使用建構函式來初始化基底類別，如下列宣告所示。

```csharp
public Cylinder(double r, double h): base(r, h) {}
```

下列程式會叫用適當的 `Area()` 方法實作，根據與方法相關聯的物件，計算並顯示每一個圖形的適當區域。

[!code-csharp[csrefKeywordsModifiers#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#23)]

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [修飾詞](modifiers.md)
- [C# 關鍵字](index.md)
- [多型](../../programming-guide/classes-and-structs/polymorphism.md)
- [abstract](abstract.md)
- [override](override.md)
- [new (修飾詞)](new-modifier.md)
