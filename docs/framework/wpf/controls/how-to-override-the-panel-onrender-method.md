---
title: HOW TO：覆寫 Panel 的 OnRender 方法
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
ms.openlocfilehash: 23c3353e130585ed83726816a467ca73f6aa9152
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666708"
---
# <a name="how-to-override-the-panel-onrender-method"></a>作法：覆寫 Panel 的 OnRender 方法
這個範例會示範如何覆寫<xref:System.Windows.Controls.Panel.OnRender%2A>的<xref:System.Windows.Controls.Panel>方法, 以便將自訂圖形效果加入至版面配置元素。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Controls.Panel.OnRender%2A>使用方法, 即可將圖形效果加入至呈現的面板專案。 例如, 您可以使用這個方法來新增自訂框線或背景效果。 <xref:System.Windows.Media.DrawingContext>物件會當做引數傳遞, 以提供繪製圖形、文字、影像或影片的方法。 因此, 這個方法對於面板物件的自訂很有用。  
  
 [!code-csharp[LightWeightCustomPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.Panel>
- [面板概觀](panels-overview.md)
- [HOW-TO 主題](panel-how-to-topics.md)
