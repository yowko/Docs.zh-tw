---
title: 如何：使用系統字型索引鍵
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: c68f197daebd7423aa4ad2e7fdfb6e7f89c74ed0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-system-fonts-keys"></a>如何：使用系統字型索引鍵
系統資源會將數個系統度量資訊公開為資源，協助開發人員建立與系統設定一致的視覺效果。 <xref:System.Windows.SystemFonts> 是包含系統字型值和系統字型資源的值繫結的類別，例如<xref:System.Windows.SystemFonts.CaptionFontFamily%2A>和<xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>。  
  
 系統字型度量資訊可以當成靜態或動態資源使用。 如果您想要在應用程式執行時自動更新字型度量資訊，請使用動態資源；否則請使用靜態資源。  
  
> [!NOTE]
>  動態資源有關鍵字*金鑰*附加至屬性名稱。  
  
 下列範例示範如何存取及使用系統字型動態資源，以設定或自訂按鈕的樣式。 這[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]範例會建立指派按鈕樣式<xref:System.Windows.SystemFonts>按鈕的值。  
  
## <a name="example"></a>範例  
 [!code-xaml[SystemRes_snip#FontDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a>另請參閱  
 [使用系統筆刷繪製區域](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [使用 SystemParameters](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)  
 [使用 SystemFonts](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)
