---
title: HOW TO：使用 SystemFonts
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- system fonts [WPF]
- fonts [WPF], system fonts
- classes [WPF], SystemFonts
ms.assetid: 3f46a4ec-2225-408a-8123-8838a8f7057a
ms.openlocfilehash: bf99d716c5c41b7604244022d2e58423594a9cf3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674868"
---
# <a name="how-to-use-systemfonts"></a>HOW TO：使用 SystemFonts
此範例示範如何使用的靜態資源<xref:System.Windows.SystemFonts>類別，以便設定或自訂按鈕的樣式。  
  
## <a name="example"></a>範例  
 系統資源會將數個系統判斷的值同時公開為資源和屬性，協助您建立與系統設定一致的視覺效果。 <xref:System.Windows.SystemFonts> 是靜態屬性，以及參考可用來在執行階段以動態方式存取這些值的資源索引鍵的屬性包含這兩個系統字型值的類別。 例如，<xref:System.Windows.SystemFonts.CaptionFontFamily%2A>是<xref:System.Windows.SystemFonts>的值，和<xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>是對應的資源索引鍵。  
  
 在  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，您可以使用的成員<xref:System.Windows.SystemFonts>為靜態屬性或動態資源參考 （以靜態屬性的值，做為索引鍵）。 如果您想要在應用程式執行時自動更新字型度量資訊，請使用動態資源參考；否則請使用靜態值參考。  
  
> [!NOTE]
>  資源索引鍵會將後置字元 "Key" 附加至屬性名稱。  
  
 下列範例示範如何存取和使用的屬性<xref:System.Windows.SystemFonts>作為靜態值，以便設定或自訂按鈕的樣式。 此標記範例會將指派<xref:System.Windows.SystemFonts>至按鈕的值。  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 若要使用的值<xref:System.Windows.SystemFonts>程式碼中，您不需要使用靜態值或動態資源參考。 相反地，使用的非索引鍵屬性<xref:System.Windows.SystemFonts>類別。 雖然非索引鍵屬性已明顯定義為靜態屬性，執行階段行為的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]所裝載，系統會重新評估即時內容，並會適當地將使用者導向的系統值變更為。 下列範例示範如何指定按鈕的字型設定。  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.SystemFonts>
- [使用系統筆刷繪製區域](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [使用 SystemParameters](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)
- [使用系統字型索引鍵](../../../../docs/framework/wpf/advanced/how-to-use-system-fonts-keys.md)
- [HOW-TO 主題](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)
- [x:Static 標記延伸](../../../../docs/framework/xaml-services/x-static-markup-extension.md)
- [XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)
- [DynamicResource 標記延伸](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)
