---
title: "x:Null 標記延伸"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- NullExtension
- x:NullExtension
- x:Null
- Null
- xNull
helpviewer_keywords:
- Null markup extension in XAML [XAML Services]
- x:Null markup extension [XAML Services]
- XAML [XAML Services], x:Null markup extension
ms.assetid: 2e3ccc21-4996-481d-91b5-3910d8b3bfa3
caps.latest.revision: "20"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: a60d74bdf3343d02eaf912ac7700f36a649f659c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="xnull-markup-extension"></a>x:Null 標記延伸
指定`null`做為 XAML 成員的值。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a>備註  
 中的 null 參考的關鍵字[!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)]和[!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)]為 null。 [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)] Null 參考的關鍵字是`Nothing`，但會一直使用`{x:Null}`與 XAML 用法不論關聯的 xaml 程式碼後置語言。  
  
 `x:Null`標記延伸可以沒有可設定的屬性。  
  
 Null 使用量都通常與 CLR 的 XAML 成員公開<xref:System.Nullable%601>值。  
  
 `x:Null`像所有的 XAML 標記延伸的標記延伸使用大括號 (`{,}`) 屬性值而不是常值或參考事件處理常式處理逸出。 屬性語法是最常搭配這個標記延伸使用的語法。 物件項目語法`<x:Null />`可行，但很少使用，因為`x:Null`標記延伸可以沒有位置參數或建構引數。  
  
 如需標記延伸的詳細資訊，請參閱[標記延伸和 WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
 在.NET Framework XAML 服務，此標記延伸處理由定義<xref:System.Windows.Markup.NullExtension>類別。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 請注意，`null`不一定是參考類型的相依性屬性未設定的初始值。 初始預設值為每個相依性屬性可能會不同，可以根據特定屬性的中繼資料。 不接受多個相依性屬性`null`做為值，方法是透過標記或程式碼，因為它們的驗證回呼實作。 如需相依性屬性的詳細資訊，請參閱[相依性屬性概觀](../../../docs/framework/wpf/advanced/dependency-properties-overview.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.DependencyProperty.UnsetValue>  
 [XAML 概觀 (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [標記延伸和 WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
