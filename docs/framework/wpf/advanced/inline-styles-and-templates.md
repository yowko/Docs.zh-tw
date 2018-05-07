---
title: 內嵌樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
ms.openlocfilehash: 9c06f61bce1e17770fa0a9b9ed7a0e20625a79ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="inline-styles-and-templates"></a>內嵌樣式和範本
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供<xref:System.Windows.Style>物件和範本物件 (<xref:System.Windows.FrameworkTemplate>子類別) 做為在資源定義元素的視覺外觀的方式，以便它們可以用於多次。 基於這個理由中的屬性[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]可接受型別<xref:System.Windows.Style>和<xref:System.Windows.FrameworkTemplate>幾乎資源參考現有的樣式和範本，而非定義新的內嵌。  
  
## <a name="limitations-of-inline-styles-and-templates"></a>內嵌樣式和範本的限制  
 在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]、 樣式和樣板屬性技術上可以設定在兩種方式之一。 您可以使用屬性語法來參考已定義內的資源，例如樣式`<`*物件*`Style="{StaticResource`*myResourceKey*`}" .../>`。 或者，您可以使用屬性項目語法來定義內嵌樣式，例如：  
  
 `<` *物件* `>`  
  
 `<` *物件* `.Style>`  
  
 `<` `Style`  `.../>`  
  
 `</` *物件* `.Style>`  
  
 `</` *物件* `>`  
  
 屬性使用方式是更加普遍。 為內嵌定義和資源中沒有定義的樣式一定範圍內包含的項目，並不容易重複使用，因為它有沒有資源索引鍵。 一般情況下的資源定義樣式是更具彈性的且有用的而且比較為了保持一般[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]程式設計模型原則的程式碼邏輯分離標記中的設計。  
  
 通常沒有理由將樣式或範本的內嵌，即使您只想要使用該樣式或範本的位置。 可以採用樣式或範本的大部分項目也支援內容的屬性和內容模型。 如果您只使用任何邏輯樹狀結構中一次透過樣式或範本建立，就更容易只 equivalent 子系中的項目直接標記填滿該內容的屬性。 這會完全略過的樣式和範本機制。  
  
 傳回物件的標記延伸模組所啟用的其他語法是樣式和範本允許的。 有可能的案例的兩個這類延伸包括[TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)和<xref:System.Windows.Data.Binding>。  
  
## <a name="see-also"></a>另請參閱  
 [樣式設定和範本化](../../../../docs/framework/wpf/controls/styling-and-templating.md)
