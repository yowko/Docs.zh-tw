---
title: 內嵌樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
ms.openlocfilehash: b566e157e2d4a9e9be21a678541bf5d5341a898c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051004"
---
# <a name="inline-styles-and-templates"></a>內嵌樣式和範本
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供<xref:System.Windows.Style>物件和範本物件 (<xref:System.Windows.FrameworkTemplate>子類別) 來定義資源中的視覺外觀的項目，以便他們可以使用多次。 基於這個理由中的屬性[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]會採用型別<xref:System.Windows.Style>和<xref:System.Windows.FrameworkTemplate>幾乎一律讓現有的樣式和範本的資源參考而不是定義新的內嵌。  
  
## <a name="limitations-of-inline-styles-and-templates"></a>內嵌樣式和範本的限制  
 在  [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，技術上可以在下列其中一種設定樣式和範本屬性。 您可以使用屬性語法來參考定義內的資源，例如樣式`<`*物件*`Style="{StaticResource`*myResourceKey*`}" .../>`。 或者，您可以使用屬性元素語法來定義內嵌樣式，例如：  
  
 `<` *object* `>`  
  
 `<` *object* `.Style>`  
  
 `<` `Style`  `.../>`  
  
 `</` *object* `.Style>`  
  
 `</` *object* `>`  
  
 屬性使用方式是更為普遍。 是內嵌定義和資源中沒有定義的樣式一定範圍是包含的項目，而且不能容易重複使用，因為它有沒有資源索引鍵。 一般資源所定義的樣式更具彈性且實用，且是基於一般[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]程式設計模型的程式碼中的程式邏輯區分開來標記中的設計的原則。  
  
 通常沒有理由將樣式或範本的內嵌，即使您只想要使用該樣式或範本，在該位置。 大部分的項目，可能需要樣式或範本也支援內容的屬性和內容模型。 如果您只使用任何邏輯樹狀結構一次透過樣式或範本建立，它會更輕鬆地只將該內容屬性填入 equivalent 子系中的項目直接的標記。 這會完全略過的樣式和範本機制。  
  
 傳回物件的標記延伸模組啟用其他語法也會讓樣式和範本。 包含兩個這類有可能的案例的延伸模組[TemplateBinding](templatebinding-markup-extension.md)和<xref:System.Windows.Data.Binding>。  
  
## <a name="see-also"></a>另請參閱

- [樣式設定和範本化](../controls/styling-and-templating.md)
