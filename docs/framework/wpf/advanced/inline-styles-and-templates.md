---
title: 內嵌樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
ms.openlocfilehash: b88ef444283f4e1e85009c59b39f3cc41965d300
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460000"
---
# <a name="inline-styles-and-templates"></a>內嵌樣式和範本
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供 <xref:System.Windows.Style> 物件和樣板物件（<xref:System.Windows.FrameworkTemplate> 子類別）做為在資源中定義元素視覺外觀的方式，讓它們可以多次使用。 基於這個理由，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中採用類型 <xref:System.Windows.Style> 和 <xref:System.Windows.FrameworkTemplate> 的屬性，幾乎一律會對現有的樣式和範本進行資源參考，而不是以內嵌方式定義新的。  
  
## <a name="limitations-of-inline-styles-and-templates"></a>內嵌樣式和範本的限制  
 在 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中，樣式和範本屬性可以透過兩種方式的其中一種來設定。 您可以使用屬性語法來參考資源內所定義的樣式，例如 `<`*物件*`Style="{StaticResource`*myResourceKey*`}" .../>`。 或者，您可以使用屬性專案語法來定義內嵌樣式，例如：  
  
 `<`*物件*`>`  
  
 `<`*物件*`.Style>`  
  
 `<` `Style``.../>`  
  
 `</`*物件*`.Style>`  
  
 `</`*物件*`>`  
  
 屬性使用方式更為常見。 在資源中定義為內嵌且未定義的樣式，必須僅限於包含元素，而且因為沒有資源索引鍵，所以無法重複使用。 一般而言，資源定義的樣式更具彈性且有用，而且更符合一般 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 程式設計模型原則，這是在程式碼中將程式邏輯與標記中的設計分隔開來。  
  
 通常不需要設定樣式或範本內嵌，即使您只想要在該位置使用該樣式或範本也一樣。 大部分可接受樣式或範本的專案也都支援內容屬性和內容模型。 如果您只使用透過樣式設定或範本化所建立的任何邏輯樹狀結構，則只需要在直接標記中使用對等的子項目來填入該內容屬性，會變得更容易。 這會完全略過樣式和範本機制。  
  
 針對樣式和範本，也可能由傳回物件的標記延伸所啟用的其他語法。 具有可能案例的兩個這類延伸模組，包括[TemplateBinding](templatebinding-markup-extension.md)和 <xref:System.Windows.Data.Binding>。  
  
## <a name="see-also"></a>請參閱

- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
