---
title: 作法：裝飾 Panel 的子系
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], binding to children of Panels
- Panel control [WPF], binding adorners to children
ms.assetid: 4cc9b972-b472-4e5c-bdf3-3702d7fbb1f5
ms.openlocfilehash: 739ccaa0273e66c4650c35217a1156d64336dbbb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923518"
---
# <a name="how-to-adorn-the-children-of-a-panel"></a>HOW TO：裝飾 Panel 的子系
這個範例會示範如何以程式設計方式, 將裝飾項系結<xref:System.Windows.Controls.Panel>至指定之的子系。  
  
## <a name="example"></a>範例  
 若要將裝飾項<xref:System.Windows.Controls.Panel>系結至的子系, 請遵循下列步驟:  
  
1. 宣告新<xref:System.Windows.Documents.AdornerLayer>的物件, 並`static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>呼叫方法, 以尋找要裝飾其子系之專案的裝飾項層。  
  
2. 列舉父元素的子系, 並呼叫<xref:System.Windows.Documents.AdornerLayer.Add%2A>方法, 將裝飾項系結至每個子專案。  
  
 下列範例會將 SimpleCircleAdorner (如上所示) 系結至<xref:System.Windows.Controls.StackPanel>名為*myStackPanel*的子系。  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
> [!NOTE]
> 使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 將裝飾項繫結至另一個目前不支援的項目。  
  
## <a name="see-also"></a>另請參閱

- [裝飾項概觀](adorners-overview.md)
