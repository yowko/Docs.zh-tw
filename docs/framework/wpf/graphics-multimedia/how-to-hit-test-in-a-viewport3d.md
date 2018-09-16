---
title: 如何：Viewport3D 中的點擊測試
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3-D visuals [WPF], hit-testing for
- hit tests [WPF], for 3-D visuals
- Viewport3D [WPF]
ms.assetid: 42bfbd99-c7c6-43f1-940b-90448faa412e
ms.openlocfilehash: 297fe17b8844f7542255afcfe442fbf9b7a0d59d
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45677475"
---
# <a name="how-to-hit-test-in-a-viewport3d"></a>如何：Viewport3D 中的點擊測試
此範例示範如何進行點擊測試中的 3D 視覺效果<xref:System.Windows.Controls.Viewport3D>。  
  
 因為<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>2D 和 3D 的資訊，會傳回可逐一查看測試結果，以讀取只 3D 的結果。  
  
 [!code-csharp[HitTest3D#HitTest3D3DN4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn4)]
 [!code-vb[HitTest3D#HitTest3D3DN4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn4)]  
  
 <xref:System.Windows.Media.HitTestResultBehavior>在下列程式碼會決定點擊的測試結果的處理方式。  `UpdateResultInfo` 和`UpdateMaterial`本機定義的方法。  
  
 [!code-csharp[HitTest3D#HitTest3D3DN5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn5)]
 [!code-vb[HitTest3D#HitTest3D3DN5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn5)]  
  
## <a name="see-also"></a>另請參閱  
 [3d 點擊測試範例](https://go.microsoft.com/fwlink/?LinkID=159959)
