---
title: 如何：尋找 ControlTemplate 產生的項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ControlTemplates [WPF], finding elements
- finding ControlTemplate elements [WPF]
ms.assetid: d7b25447-ceff-4bb4-9be5-fd7c40ef00af
ms.openlocfilehash: 232ee7d2859059591c9beff753f45781598a8127
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460713"
---
# <a name="how-to-find-controltemplate-generated-elements"></a>如何：尋找 ControlTemplate 產生的項目
這個範例會示範如何尋找 <xref:System.Windows.Controls.ControlTemplate>所產生的元素。  
  
## <a name="example"></a>範例  
 下列範例顯示的樣式會建立 <xref:System.Windows.Controls.Button> 類別的簡單 <xref:System.Windows.Controls.ControlTemplate>：  
  
 [!code-xaml[FindGeneratedItems#CT](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#ct)]  
  
 若要在套用範本之後尋找範本中的元素，您可以呼叫 <xref:System.Windows.Controls.Control.Template%2A>的 <xref:System.Windows.FrameworkTemplate.FindName%2A> 方法。 下列範例會建立訊息方塊，顯示控制項範本中 <xref:System.Windows.Controls.Grid> 的實際寬度值：  
  
 [!code-csharp[FindGeneratedItems#CTFindElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#ctfindelement)]
 [!code-vb[FindGeneratedItems#CTFindElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#ctfindelement)]  
  
## <a name="see-also"></a>請參閱

- [尋找 DataTemplate 產生的元素](../data/how-to-find-datatemplate-generated-elements.md)
- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [WPF XAML 名稱範圍](../advanced/wpf-xaml-namescopes.md)
- [WPF 中的樹狀結構](../advanced/trees-in-wpf.md)
