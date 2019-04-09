---
title: HOW TO：使用系統參數索引鍵
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
ms.openlocfilehash: 147f65b4bb214c12317309081c345251d7426cd6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147326"
---
# <a name="how-to-use-system-parameters-keys"></a>HOW TO：使用系統參數索引鍵
系統資源會將數個系統度量資訊公開為資源，協助開發人員建立與系統設定一致的視覺效果。 <xref:System.Windows.SystemParameters> 是包含系統參數值以及繫結至值的資源索引鍵的類別，例如<xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A>和<xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>。 系統參數度量資訊可以當成靜態或動態資源使用。 如果您想要在應用程式執行時自動更新參數度量資訊，請使用動態資源；否則請使用靜態資源。  
  
> [!NOTE]
>  動態資源具有關鍵字*金鑰*附加至屬性名稱。  
  
 下列範例示範如何存取及使用系統參數動態資源，以設定或自訂按鈕的樣式。 這[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]範例按鈕大小指派<xref:System.Windows.SystemParameters>按鈕的寬度和高度的值。  
  
## <a name="example"></a>範例  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a>另請參閱

- [使用系統筆刷繪製區域](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [使用 SystemFonts](how-to-use-systemfonts.md)
- [使用 SystemParameters](how-to-use-systemparameters.md)
