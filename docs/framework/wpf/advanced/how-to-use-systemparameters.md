---
title: HOW TO：使用 SystemParameters
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], SystemParameters
ms.assetid: 02e7a5de-94eb-4953-b91c-52e6c872ad5b
ms.openlocfilehash: 00afc5c12ea9b83759361e9a3f175e91b4cbb10d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541660"
---
# <a name="how-to-use-systemparameters"></a>HOW TO：使用 SystemParameters
此範例示範如何存取和使用的屬性<xref:System.Windows.SystemParameters>以便設定或自訂按鈕的樣式。  
  
## <a name="example"></a>範例  
 系統資源會將數個系統設定公開為資源，協助您建立與系統設定一致的視覺效果。 <xref:System.Windows.SystemParameters> 是包含系統參數值屬性，以及繫結至值的資源索引鍵的類別。 例如，<xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A>已<xref:System.Windows.SystemParameters>屬性值和<xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>是對應的資源索引鍵。  
  
 在  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，您可以使用的成員<xref:System.Windows.SystemParameters>為靜態屬性使用方式或動態資源參考 （以靜態屬性值做為索引鍵）。 如果您想要在應用程式執行時自動更新系統值，請使用動態資源參考；否則請使用靜態參考。 資源索引鍵後置字元`Key`附加至屬性名稱。  
  
 下列範例示範如何存取和使用的靜態值<xref:System.Windows.SystemParameters>以設定或自訂按鈕的樣式。 此標記範例按鈕大小套用<xref:System.Windows.SystemParameters>至按鈕的值。  
  
 [!code-xaml[SystemRes_snip#ParameterStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#parameterstaticresources)]  
  
 若要使用的值<xref:System.Windows.SystemParameters>程式碼中，您不需要使用靜態參考或動態資源參考。 相反地，使用的值<xref:System.Windows.SystemParameters>類別。 雖然非索引鍵屬性已明顯定義為靜態屬性，執行階段行為[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]託管系統會重新評估即時中的屬性，並適當地將使用者導向的系統值變更的帳戶。 下列範例示範如何使用設定按鈕的高度與寬度<xref:System.Windows.SystemParameters>值。  
  
 [!code-csharp[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#parameterresourcescode)]
 [!code-vb[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#parameterresourcescode)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.SystemParameters>
- [使用系統筆刷繪製區域](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [使用 SystemFonts](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)
- [使用系統參數索引鍵](../../../../docs/framework/wpf/advanced/how-to-use-system-parameters-keys.md)
- [HOW-TO 主題](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)
