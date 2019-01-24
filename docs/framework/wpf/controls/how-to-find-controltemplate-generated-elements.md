---
title: HOW TO：尋找 ControlTemplate 產生的項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ControlTemplates [WPF], finding elements
- finding ControlTemplate elements [WPF]
ms.assetid: d7b25447-ceff-4bb4-9be5-fd7c40ef00af
ms.openlocfilehash: a93ec700bc0782439f98aed48f7094a50a3c0ea4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638375"
---
# <a name="how-to-find-controltemplate-generated-elements"></a>HOW TO：尋找 ControlTemplate 產生的項目
此範例示範如何尋找所產生的項目<xref:System.Windows.Controls.ControlTemplate>。  
  
## <a name="example"></a>範例  
 下列範例示範建立一個簡單的樣式<xref:System.Windows.Controls.ControlTemplate>針對<xref:System.Windows.Controls.Button>類別：  
  
 [!code-xaml[FindGeneratedItems#CT](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#ct)]  
  
 若要套用範本之後，請尋找範本內的項目，您可以呼叫<xref:System.Windows.FrameworkTemplate.FindName%2A>方法的<xref:System.Windows.Controls.Control.Template%2A>。 下列範例會建立一個訊息方塊，顯示的實際寬度值<xref:System.Windows.Controls.Grid>控制項範本內：  
  
 [!code-csharp[FindGeneratedItems#CTFindElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#ctfindelement)]
 [!code-vb[FindGeneratedItems#CTFindElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#ctfindelement)]  
  
## <a name="see-also"></a>另請參閱
- [尋找 DataTemplate 產生的元素](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)
- [樣式設定和範本化](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [WPF XAML 名稱範圍](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)
- [WPF 中的樹狀結構](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)
