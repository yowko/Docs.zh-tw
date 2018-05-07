---
title: 如何：取得唯讀 Freezable 的可寫入複本
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cloning Freezable objects [WPF]
- Freezable objects [WPF], modifiable clones
ms.assetid: d028de61-bbe9-4d62-b656-8fe3b1b2ca24
ms.openlocfilehash: 894a2e42ca3f5cbb159c3129227f4b03e71fc4ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-obtain-a-writable-copy-of-a-read-only-freezable"></a>如何：取得唯讀 Freezable 的可寫入複本
這個範例示範如何使用<xref:System.Windows.Freezable.Clone%2A>方法來建立唯讀的可寫入副本<xref:System.Windows.Freezable>。  
  
 之後<xref:System.Windows.Freezable>物件標示為唯讀狀態 （「 凍結 」），您不能修改它。 不過，您可以使用<xref:System.Windows.Freezable.Clone%2A>方法建立已凍結物件的可修改複本。  
  
## <a name="example"></a>範例  
 下列範例會建立可修改的凍結複製品<xref:System.Windows.Media.SolidColorBrush>物件。  
  
 [!code-csharp[freezablesample_procedural#CloneExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
 如需有關<xref:System.Windows.Freezable>物件，請參閱[Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.CloneCurrentValue%2A>  
 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
