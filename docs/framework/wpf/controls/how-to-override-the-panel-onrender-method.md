---
title: "如何：覆寫 Panel 的 OnRender 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 958595cdfa521b372270d6283c7134ef0ba0ef79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-override-the-panel-onrender-method"></a>如何：覆寫 Panel 的 OnRender 方法
這個範例示範如何覆寫<xref:System.Windows.Controls.Panel.OnRender%2A>方法<xref:System.Windows.Controls.Panel>以便將自訂的圖形效果新增至版面配置項目。  
  
## <a name="example"></a>範例  
 使用<xref:System.Windows.Controls.Panel.OnRender%2A>方法，以將圖形效果加入至轉譯的面板項目。 例如，您可以使用這個方法將自訂框線或背景效果。 A<xref:System.Windows.Media.DrawingContext>物件會傳遞做為引數，提供方法來繪製圖形、 文字、 影像或視訊。 如此一來，這個方法可用於自訂的面板物件。  
  
 [!code-csharp[LightWeightCustomPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Controls.Panel>  
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [自訂放射狀面板範例](http://go.microsoft.com/fwlink/?LinkID=159982)  
 [HOW-TO 主題](../../../../docs/framework/wpf/controls/panel-how-to-topics.md)
