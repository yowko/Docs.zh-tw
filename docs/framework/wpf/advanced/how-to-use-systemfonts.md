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
ms.openlocfilehash: 7438705a82faee464649b5f6f577627a379e9a8c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918355"
---
# <a name="how-to-use-systemfonts"></a>作法：使用 SystemFonts
這個範例示範如何使用<xref:System.Windows.SystemFonts>類別的靜態資源, 以樣式或自訂按鈕。  
  
## <a name="example"></a>範例  
 系統資源會將數個系統判斷的值同時公開為資源和屬性，協助您建立與系統設定一致的視覺效果。 <xref:System.Windows.SystemFonts>是一個類別, 其中同時包含系統字型值做為靜態屬性, 以及參考資源索引鍵的屬性, 可在執行時間以動態方式存取這些值。 例如, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> <xref:System.Windows.SystemFonts>是值, 而<xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>是對應的資源索引鍵。  
  
 在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]中, 您可以使用的<xref:System.Windows.SystemFonts>成員做為靜態屬性或動態資源參考 (具有靜態屬性值做為索引鍵)。 如果您想要在應用程式執行時自動更新字型度量資訊，請使用動態資源參考；否則請使用靜態值參考。  
  
> [!NOTE]
> 資源索引鍵會將後置字元 "Key" 附加至屬性名稱。  
  
 下列範例示範如何存取和使用的屬性<xref:System.Windows.SystemFonts>做為靜態值, 以進行樣式或自訂按鈕。 此標記範例會<xref:System.Windows.SystemFonts>將值指派給按鈕。  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 若要<xref:System.Windows.SystemFonts>在程式碼中使用的值, 您不需要使用靜態值或動態資源參考。 相反地, 請使用<xref:System.Windows.SystemFonts>類別的非索引鍵屬性。 雖然非索引鍵屬性已明顯定義為靜態屬性, 但由系統裝載之[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的執行時間行為會即時重新評估屬性, 並適當地將使用者驅動的系統值變更加以考慮。 下列範例示範如何指定按鈕的字型設定。  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.SystemFonts>
- [使用系統筆刷繪製區域](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [使用 SystemParameters](how-to-use-systemparameters.md)
- [使用系統字型索引鍵](how-to-use-system-fonts-keys.md)
- [HOW-TO 主題](resources-how-to-topics.md)
- [x:Static 標記延伸](../../xaml-services/x-static-markup-extension.md)
- [XAML 資源](xaml-resources.md)
- [DynamicResource 標記延伸](dynamicresource-markup-extension.md)
