---
title: 如何：裝飾 Panel 的子系
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], binding to children of Panels
- Panel control [WPF], binding adorners to children
ms.assetid: 4cc9b972-b472-4e5c-bdf3-3702d7fbb1f5
ms.openlocfilehash: 4babbf1df57f340a3f6be218f213ad1c868ec9f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-adorn-the-children-of-a-panel"></a>如何：裝飾 Panel 的子系
這個範例示範如何以程式設計方式將裝飾項繫結至指定的子系<xref:System.Windows.Controls.Panel>。  
  
## <a name="example"></a>範例  
 若要繫結的項目子系的裝飾項<xref:System.Windows.Controls.Panel>，請遵循下列步驟：  
  
1.  宣告新<xref:System.Windows.Documents.AdornerLayer>物件並呼叫`static`<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>方法來尋找其裝飾項層，其子系要被裝飾項目。  
  
2.  列舉的子系的父項目並呼叫<xref:System.Windows.Documents.AdornerLayer.Add%2A>方法，以將裝飾項繫結至每個子項目。  
  
 下列範例會將繫結 （如上所示） 的項目子系 SimpleCircleAdorner<xref:System.Windows.Controls.StackPanel>名為*myStackPanel*。  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
> [!NOTE]
>  使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 將裝飾項繫結至另一個目前不支援的項目。  
  
## <a name="see-also"></a>另請參閱  
 [裝飾項概觀](../../../../docs/framework/wpf/controls/adorners-overview.md)
