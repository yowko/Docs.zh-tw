---
title: x:Null 標記延伸
ms.date: 03/30/2017
f1_keywords:
- NullExtension
- x:NullExtension
- x:Null
- "Null"
- xNull
helpviewer_keywords:
- Null markup extension in XAML [XAML Services]
- x:Null markup extension [XAML Services]
- XAML [XAML Services], x:Null markup extension
ms.assetid: 2e3ccc21-4996-481d-91b5-3910d8b3bfa3
ms.openlocfilehash: 34a2de71bec9b0929070aa908741de38b5904643
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2019
ms.locfileid: "58029370"
---
# <a name="xnull-markup-extension"></a>x:Null 標記延伸
指定`null`做為 XAML 成員的值。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a>備註  
 為 null 參考中的關鍵字C#並[!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)]為 null。 是 null 參考的 Microsoft Visual Basic 關鍵字`Nothing`，但您一律使用`{x:Null}`視為 XAML 使用量不論哪一種程式碼後置的語言與相關聯的 XAML。  
  
 `x:Null`標記延伸模組沒有任何可設定的屬性。  
  
 Null 的使用方式通常是相關聯的 CLR 的 XAML 成員公開<xref:System.Nullable%601>值。  
  
 `x:Null`標記延伸模組，所有 XAML 標記延伸模組，例如使用大括號 (`{,}`) 的逸出為常值或事件處理常式的參考以外的屬性值的處理。 屬性語法是最常搭配這個標記延伸語法。 物件元素語法`<x:Null />`技術上可行，但很少使用，因為`x:Null`標記延伸模組沒有任何位置參數 」 或 「 建構引數。  
  
 如需標記延伸的詳細資訊，請參閱[標記延伸和 WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
 在.NET Framework XAML 服務中，這個標記延伸的處理由定義<xref:System.Windows.Markup.NullExtension>類別。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 請注意，`null`不一定是參考型別相依性屬性未設定的初始值。 初始預設值為每個相依性屬性而有所不同，並可根據特定屬性的中繼資料。 許多相依性屬性不接受`null`為值時，透過標記或程式碼，因為它們的驗證回呼實作。 如需有關相依性屬性的詳細資訊，請參閱 <<c0> [ 相依性屬性概觀](../wpf/advanced/dependency-properties-overview.md)。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.DependencyProperty.UnsetValue>
- [XAML 概觀 (WPF)](../wpf/advanced/xaml-overview-wpf.md)
- [標記延伸和 WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
