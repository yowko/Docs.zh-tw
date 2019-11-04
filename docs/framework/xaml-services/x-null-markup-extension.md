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
ms.openlocfilehash: ff82b0bfc1983240431e582dbd78778dc4469241
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459940"
---
# <a name="xnull-markup-extension"></a>x:Null 標記延伸
指定 `null` 做為 XAML 成員的值。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a>備註  
 和C# C++中 null 參考的關鍵字是 null。 Null 參考的 Microsoft Visual Basic 關鍵字是 `Nothing`，但無論您與 XAML 建立關聯的程式碼後置語言為何，一律會使用 `{x:Null}` 做為 XAML 用法。  
  
 `x:Null` 標記延伸沒有可設定的屬性。  
  
 Null 用法通常與 CLR <xref:System.Nullable%601> 值的 XAML 成員公開相關聯。  
  
 如同所有的 XAML 標記延伸，`x:Null` 標記延伸都會使用大括弧（`{,}`）來將屬性值的處理，轉義為非常值或事件處理常式參考。 屬性語法是最常搭配此標記延伸使用的語法。 在技術上，`<x:Null />` 物件元素語法，但很少使用，因為 `x:Null` 標記延伸沒有位置參數或結構引數。  
  
 如需標記延伸的詳細資訊，請參閱[標記延伸和 WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
 在 .NET Framework XAML 服務中，此標記延伸模組的處理是由 <xref:System.Windows.Markup.NullExtension> 類別所定義。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 請注意，`null` 不一定是參考型別相依性屬性的初始未設定值。 每個相依性屬性的初始預設值可能有所不同，而且可以根據屬性特定的中繼資料。 許多相依性屬性都不接受 `null` 做為值，因為它是透過標記或程式碼，因為其驗證回呼的執行方式。 如需相依性屬性的詳細資訊，請參閱相依性[屬性總覽](../wpf/advanced/dependency-properties-overview.md)。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [XAML 概觀 (WPF)](../../desktop-wpf/fundamentals/xaml.md)
- [標記延伸和 WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
