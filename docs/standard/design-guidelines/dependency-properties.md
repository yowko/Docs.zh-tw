---
title: 相依性屬性
ms.date: 10/22/2008
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
ms.openlocfilehash: ab30da59670c146874defe86b1d048f97eebf449
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734760"
---
# <a name="dependency-properties"></a>相依性屬性

 (DP) 的相依性屬性是一般屬性，它會將其值儲存在屬性存放區，而不是將它儲存在類型變數 (欄位) 中。

 附加的相依性屬性是一種模型化為靜態 Get 和 Set 方法的相依性屬性，其代表描述物件與其容器之間關聯性的「屬性」 (例如， `Button` 容器上物件的位置 `Panel`) 。

 如果您需要屬性來支援樣式、觸發程式、資料系結、動畫、動態資源和繼承等 WPF 功能，✔️提供相依性屬性。

## <a name="dependency-property-design"></a>相依性屬性設計

 ✔️在執行相依性 <xref:System.Windows.DependencyObject> 屬性時，會繼承自或其中一個子類型。 此類型提供非常有效率的屬性存放區執行，並自動支援 WPF 資料系結。

 ✔️確實提供一般 CLR 屬性和公用靜態唯讀欄位，以儲存每個相依性 <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> 屬性的實例。

 ✔️藉由呼叫實例方法和來執行相依性屬性 <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType> 。

 ✔️透過 suffixing 具有 "Property" 的屬性名稱，將相依性屬性靜態欄位命名。

 ❌ 請勿在程式碼中明確設定相依性屬性的預設值;請改為在中繼資料中設定這些專案。

 如果您明確地設定屬性預設值，您可能會防止某個隱含的方法（例如樣式）設定該屬性。

 ❌ 請勿將程式碼放在標準程式碼以外的屬性存取子中，以存取靜態欄位。

 如果屬性是透過隱含方式（例如樣式）設定，則該程式碼不會執行，因為樣式會直接使用靜態欄位。

 ❌ 請勿使用相依性屬性來儲存安全的資料。 甚至可以公開存取私用相依性屬性。

## <a name="attached-dependency-property-design"></a>附加的相依性屬性設計

 上一節所述的相依性屬性代表宣告類型的內建屬性;例如， `Text` 屬性是的屬性 `TextButton` ，它會宣告它。 特殊類型的相依性屬性是附加的相依性屬性。

 附加屬性的典型範例是 <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> 屬性。 屬性代表按鈕的 (不是方格的) 資料行位置，但只有在該按鈕包含在方格中時才有關聯，因此它會依格線「附加」至按鈕。

```xaml
<Grid>
    <Grid.ColumnDefinitions>
        <ColumnDefinition />
        <ColumnDefinition />
    </Grid.ColumnDefinitions>

    <Button Grid.Column="0">Click</Button>
    <Button Grid.Column="1">Clack</Button>
</Grid>
```

 附加屬性的定義與一般相依性屬性的定義大致相同，不同之處在于存取子是以靜態 Get 和 Set 方法表示：

```csharp
public class Grid {

    public static int GetColumn(DependencyObject obj) {
        return (int)obj.GetValue(ColumnProperty);
    }

    public static void SetColumn(DependencyObject obj, int value) {
        obj.SetValue(ColumnProperty,value);
    }

    public static readonly DependencyProperty ColumnProperty =
        DependencyProperty.RegisterAttached(
            "Column",
            typeof(int),
            typeof(Grid)
    );
}
```

## <a name="dependency-property-validation"></a>相依性屬性驗證

 屬性通常會執行所謂的驗證。 當嘗試變更屬性的值時，就會執行驗證邏輯。

 可惜的是，相依性屬性存取子不能包含任意驗證程式代碼。 相反地，必須在屬性註冊期間指定相依性屬性驗證邏輯。

 ❌ 請勿將相依性屬性驗證邏輯放在屬性的存取子中。 相反地，請將驗證回撥傳遞給 `DependencyProperty.Register` 方法。

## <a name="dependency-property-change-notifications"></a>相依性屬性變更通知

 ❌ 請勿在相依性屬性存取子中執行變更通知邏輯。 相依性屬性具有內建的變更通知功能，必須藉由提供變更通知回呼來使用 <xref:System.Windows.PropertyMetadata> 。

## <a name="dependency-property-value-coercion"></a>相依性屬性值強制型轉

 在實際修改屬性存放區之前，setter 會修改指定給屬性 setter 的值時，就會發生屬性強制型轉。

 ❌ 請勿在相依性屬性存取子中執行強制邏輯。

 相依性屬性具有內建的強制功能，可透過提供的強制回呼回呼來使用 `PropertyMetadata` 。

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>另請參閱

- [架構設計指導方針](index.md)
- [常見的設計模式](common-design-patterns.md)
