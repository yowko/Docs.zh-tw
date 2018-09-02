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
ms.openlocfilehash: 8f3b65bdfe96efdc57c6b8d30991439d3bdb0bc5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404432"
---
# <a name="how-to-override-the-panel-onrender-method"></a>如何：覆寫 Panel 的 OnRender 方法
此範例示範如何覆寫<xref:System.Windows.Controls.Panel.OnRender%2A>方法的<xref:System.Windows.Controls.Panel>才能將自訂的圖形效果加入至版面配置項目。  
  
## <a name="example"></a>範例  
 使用<xref:System.Windows.Controls.Panel.OnRender%2A>方法，以新增至呈現的面板元素的圖形化的效果。 例如，您可以使用這個方法將自訂的框線或背景效果。 A<xref:System.Windows.Media.DrawingContext>物件會傳遞做為引數會提供方法來繪製圖形、 文字、 影像或影片。 如此一來，這個方法可用於自訂的面板物件。  
  
 [!code-csharp[LightWeightCustomPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.Panel>  
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [自訂放射狀面板範例](https://go.microsoft.com/fwlink/?LinkID=159982)  
 [HOW-TO 主題](../../../../docs/framework/wpf/controls/panel-how-to-topics.md)
