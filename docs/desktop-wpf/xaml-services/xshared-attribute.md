---
title: x:Shared 屬性
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: e1cd1d9db5c19decd840b433f986e0ba53557a8b
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071371"
---
# <a name="xshared-attribute"></a>x:Shared 屬性

設置為`false`時 ,將修改 WPF 資源檢索行為,以便對屬性化資源的請求為每個請求創建一個新實例,而不是為所有請求共用相同的實例。

## <a name="xaml-attribute-usage"></a>XAML Attribute Usage

```xaml
<ResourceDictionary>
  <object x:Shared="false".../>
</ResourceDictionary>
```

## <a name="remarks"></a>備註

`x:Shared`映射到 XAML 語言 XAML 命名空間,並由 .NET XAML 服務及其 XAML 讀取器識別為有效的 XAML 語言元素。 但是,聲明`x:Shared`的功能僅與 WPF 應用程式和 WPF XAML 解析器相關。 在 WPF`x:Shared`中,僅當屬性應用於存在於<xref:System.Windows.ResourceDictionary>WPF 中的物件時,它才可用作屬性。 其他用法不會引發解析異常或其他錯誤,但它們沒有效果。

在 XAML 語言規範中未`x:Shared`指定 其 含義。 其他 XAML 實現(例如基於 .NET XAML 服務實現)不一定提供資源分享支援。 此類 XAML 實現可以在支援框架中提供類似的行為,`x:Shared`該框架 也使用值。

在 WPF`x:Shared`中,資源的預設`true`條件是 。 此條件表示任何給定的資源請求始終返回同一實例。

修改通過資源 API 傳回的物件(<xref:System.Windows.FrameworkElement.FindResource%2A>如 ,或<xref:System.Windows.ResourceDictionary>直接修改中的物件)會更改原始資源。 如果對該資源的引用是動態資源引用,則該資源的消費者將獲取已更改的資源。

如果對資源的引用是靜態資源引用,則處理時間後[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]對資源的更改不相關。 有關靜態資源引用和動態資源引用的詳細資訊,請參閱[XAML 資源](../fundamentals/xaml-resources-define.md)。

顯式指定`x:Shared="true"`很少完成,因為這已經是預設值。 在 WPF 物件`x:Shared`模型中 沒有直接代碼等效;它只能在 XAML 用法中指定,並且如果使用 .NET XAML 服務及其 XAML 讀取器進行處理,則必須通過預設的 WPF 行為或在負載路徑上的中間 XAML 節點流中進行處理。

的方案`x:Shared="false"`是,如果將<xref:System.Windows.FrameworkElement><xref:System.Windows.FrameworkContentElement>或 派生類定義為資源,然後將元素資源引入內容模型。 `x:Shared="false"`使元素資源在同一集合(如<xref:System.Windows.Controls.UIElementCollection>) 中多次引入。 如果沒有`x:Shared="false"`此選項無效,因為集合會強制其內容的唯一性。 但是,該`x:Shared="false"`行為將創建資源的另一個相同實例,而不是返回相同的實例。

的另一<xref:System.Windows.Freezable>`x:Shared="false"`個 方案是,如果將資源用於動畫值,但希望根據每個動畫修改資源。

的`false`字串處理不區分大小寫。

在 WPF`x:Shared`中,僅在以下條件下有效:

- <xref:System.Windows.ResourceDictionary>必須編譯包含的`x:Shared`項。 <xref:System.Windows.ResourceDictionary>不能在鬆散的 XAML 內或用於主題。

- <xref:System.Windows.ResourceDictionary>包含項的 不能嵌套在另一<xref:System.Windows.ResourceDictionary>個 中。 例如`x:Shared`,不能<xref:System.Windows.ResourceDictionary>用於已<xref:System.Windows.Style><xref:System.Windows.ResourceDictionary>屬於項的中的項。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.ResourceDictionary>
- [XAML 資源](../fundamentals/xaml-resources-define.md)
- [基底項目](../../framework/wpf/advanced/base-elements.md)
