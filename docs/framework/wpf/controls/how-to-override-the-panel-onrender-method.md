---
title: 如何：覆寫 Panel 的 OnRender 方法
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- overriding OnRender method
- Panel control, overriding OnRender method
- OnRender method
- controls, Panel, overriding OnRender method
helpviewer_keywords:
- overriding OnRender method of Panel control [WPF]
- OnRender method [WPF], overriding
- Panel control [WPF], overriding OnRender method
ms.assetid: 57397834-a085-4e36-90ab-416fad98f341
ms.openlocfilehash: e591bc195d3b0ba58002bda42ddb3e9ed35d312e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-override-the-panel-onrender-method"></a>如何：覆寫 Panel 的 OnRender 方法
這個範例示範如何覆寫<xref:System.Windows.Controls.Panel.OnRender%2A>方法<xref:System.Windows.Controls.Panel>以便將自訂的圖形效果新增至版面配置項目。  
  
## <a name="example"></a>範例  
 使用<xref:System.Windows.Controls.Panel.OnRender%2A>方法，以將圖形效果加入至轉譯的面板項目。 例如，您可以使用這個方法將自訂框線或背景效果。 A<xref:System.Windows.Media.DrawingContext>物件會傳遞做為引數，提供方法來繪製圖形、 文字、 影像或視訊。 如此一來，這個方法可用於自訂的面板物件。  
  
 [!code-csharp[LightWeightCustomPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.Panel>  
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [自訂放射狀面板範例](http://go.microsoft.com/fwlink/?LinkID=159982)  
 [HOW-TO 主題](../../../../docs/framework/wpf/controls/panel-how-to-topics.md)
