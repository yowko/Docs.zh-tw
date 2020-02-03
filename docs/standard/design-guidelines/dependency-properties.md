---
title: 相依性屬性
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
ms.openlocfilehash: e1372b75cb6501f8bc3fec913364e9d80157ad83
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741729"
---
# <a name="dependency-properties"></a>相依性屬性
相依性屬性（DP）是將其值儲存在屬性存放區中的一般屬性，而不是將它儲存在類型變數（欄位）中，例如。

 附加的相依性屬性是一種以靜態 Get 和 Set 方法模型化的相依性屬性，其代表描述物件及其容器之間關聯性的「屬性」（例如，在 `Panel` 容器上 `Button` 物件的位置）。

 如果您需要屬性來支援樣式、觸發程式、資料系結、動畫、動態資源和繼承等 WPF 功能，✔️提供相依性屬性。

## <a name="dependency-property-design"></a>相依性屬性設計
 在執行相依性屬性時，✔️ DO 會繼承自 <xref:System.Windows.DependencyObject>或它的其中一個子類型。 型別提供非常有效率的屬性存放區執行，並自動支援 WPF 資料系結。

 ✔️提供一般 CLR 屬性和公用靜態唯讀欄位，以儲存每個相依性屬性的 <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> 實例。

 ✔️ <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> 和 <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>呼叫實例方法，以執行相依性屬性。

 ✔️執行相依性屬性靜態欄位的命名，方法是使用 "Property" suffixing 屬性的名稱。

 ❌ 不要在程式碼中明確設定相依性屬性的預設值;請改為在中繼資料中設定它們。

 如果您明確地設定屬性預設值，您可能會防止某個隱含的方式設定該屬性，例如樣式。

 ❌ 不會將程式碼放在標準程式碼以外的屬性存取子中，以存取靜態欄位。

 如果屬性是以隱含方式設定（例如樣式），則該程式碼將不會執行，因為樣式會直接使用靜態欄位。

 ❌ 不使用相依性屬性來儲存安全的資料。 甚至可以公開存取私用相依性屬性。

## <a name="attached-dependency-property-design"></a>附加的相依性屬性設計
 上一節所述的相依性屬性代表宣告類型的內建屬性。例如，`Text` 屬性是 `TextButton`的屬性，其會將其宣告。 特殊類型的相依性屬性是附加的相依性屬性。

 附加屬性的典型範例是 <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> 屬性。 屬性代表按鈕的（而不是方格的）資料行位置，但只有在按鈕包含在方格中，而且它是「附加」至按鈕 by 格線時才相關。

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

 附加屬性的定義與一般相依性屬性大致相似，不同之處在于存取子是以靜態 Get 和 Set 方法來表示：

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

 可惜的是，相依性屬性存取子不能包含任意驗證程式代碼。 相反地，在屬性註冊期間，必須指定相依性屬性驗證邏輯。

 ❌ 不要將相依性屬性驗證邏輯放在屬性的存取子中。 相反地，請將驗證回呼傳遞給 `DependencyProperty.Register` 方法。

## <a name="dependency-property-change-notifications"></a>相依性屬性變更通知
 ❌ 不會在相依性屬性存取子中執行變更通知邏輯。 相依性屬性具有內建變更通知功能，必須透過提供 <xref:System.Windows.PropertyMetadata>的變更通知回呼來使用。

## <a name="dependency-property-value-coercion"></a>相依性屬性值強制型轉
 當 setter 在實際修改屬性存放區之前修改了指定給屬性 setter 的值時，就會發生屬性強制型轉。

 ❌ 不會在相依性屬性存取子中執行強制型轉邏輯。

 相依性屬性具有內建強制型轉功能，而且可以藉由提供 `PropertyMetadata`的強制型轉回呼來使用。

 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition[ 節錄。](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)*

## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [一般設計模式](../../../docs/standard/design-guidelines/common-design-patterns.md)
