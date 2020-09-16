---
title: x:Shared 屬性
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: d5000b51d83066ec2d529db2033d8ac54f7ad329
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557784"
---
# <a name="xshared-attribute"></a>x:Shared 屬性

當設定為時 `false` ，會修改 WPF 資源抓取行為，如此一來，屬性化資源的要求就會為每個要求建立新的實例，而不是針對所有要求共用相同的實例。

## <a name="xaml-attribute-usage"></a>XAML Attribute Usage

```xaml
<ResourceDictionary>
  <object x:Shared="false".../>
</ResourceDictionary>
```

## <a name="remarks"></a>備註

`x:Shared` 會對應至 XAML 語言 XAML 命名空間，並由 .NET XAML 服務及其 XAML 讀取器辨識為有效的 XAML 語言元素。 不過，所述的功能 `x:Shared` 只適用于 wpf 應用程式和 WPF XAML 剖析器。 在 WPF 中， `x:Shared` 只有當屬性套用至存在於 wpf 中的物件時，才會用來做為屬性 <xref:System.Windows.ResourceDictionary> 。 其他使用方式不會擲回 parse 例外狀況或其他錯誤，但它們沒有任何作用。

`x:Shared`XAML 語言規格中未指定的意義。 其他 XAML 執行（例如在 .NET XAML 服務上建立的）不一定會提供資源分享支援。 這類 XAML 實值可能會在支援的架構中提供同樣使用值的類似行為 `x:Shared` 。

在 WPF 中，資源的預設 `x:Shared` 條件為 `true` 。 這種情況表示任何指定的資源要求一律會傳回相同的實例。

修改透過資源 API 傳回的物件（例如 <xref:System.Windows.FrameworkElement.FindResource%2A> ，或直接在中修改物件 <xref:System.Windows.ResourceDictionary> ），會變更原始資源。 如果該資源的參考是動態資源參考，則該資源的取用者會取得變更的資源。

如果資源的參考是靜態資源參考，則在處理時間之後變更資源 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] 將不相關。 如需有關靜態與動態資源參考的詳細資訊，請參閱 [XAML 資源](../fundamentals/xaml-resources-define.md)。

明確指定很 `x:Shared="true"` 少會完成，因為這已經是預設值。 WPF 物件模型中沒有對等的直接程式碼， `x:Shared` 它只能以 XAML 使用方式指定，且必須由預設 WPF 行為或在載入路徑上的中繼 XAML 節點資料流程中進行處理（如果使用 .NET XAML 服務及其 XAML 讀取器來處理的話）。

的案例 `x:Shared="false"` 是，如果您將 <xref:System.Windows.FrameworkElement> 或衍生的類別定義 <xref:System.Windows.FrameworkContentElement> 為資源，然後將元素資源引入內容模型中。 `x:Shared="false"` 可讓元素資源在相同的集合中多次導入 (例如 <xref:System.Windows.Controls.UIElementCollection>) 。 沒有 `x:Shared="false"` 此項是不正確，因為集合會強制執行其內容的唯一性。 不過，此 `x:Shared="false"` 行為會建立另一個相同的資源實例，而不會傳回相同的實例。

另一種情況 `x:Shared="false"` 是，如果您將 <xref:System.Windows.Freezable> 資源用於動畫值，但想要以每個動畫為基礎修改資源。

的字串處理 `false` 不區分大小寫。

在 WPF 中， `x:Shared` 只有在下列情況下才有效：

- <xref:System.Windows.ResourceDictionary>包含 `x:Shared` 必須編譯之專案的。 <xref:System.Windows.ResourceDictionary>不能在鬆散的 XAML 內或用於主題。

- <xref:System.Windows.ResourceDictionary>包含專案的不能在另一個中嵌套 <xref:System.Windows.ResourceDictionary> 。 例如，您無法將 `x:Shared` 中的專案用於已經是專案的內的專案 <xref:System.Windows.ResourceDictionary> <xref:System.Windows.Style> <xref:System.Windows.ResourceDictionary> 。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.ResourceDictionary>
- [XAML 資源](../fundamentals/xaml-resources-define.md)
- [基底項目](/dotnet/desktop/wpf/advanced/base-elements)
