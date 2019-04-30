---
title: HOW TO：取得唯讀 Freezable 的可寫入複本
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cloning Freezable objects [WPF]
- Freezable objects [WPF], modifiable clones
ms.assetid: d028de61-bbe9-4d62-b656-8fe3b1b2ca24
ms.openlocfilehash: 910c5dada6ca82f68992722e4df6b35f9f7497c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942788"
---
# <a name="how-to-obtain-a-writable-copy-of-a-read-only-freezable"></a>HOW TO：取得唯讀 Freezable 的可寫入複本
此範例示範如何使用<xref:System.Windows.Freezable.Clone%2A>方法用來建立唯讀的可寫入複本<xref:System.Windows.Freezable>。  
  
 之後<xref:System.Windows.Freezable>物件標示為唯讀狀態 （「 凍結 」），您無法修改它。 不過，您可以使用<xref:System.Windows.Freezable.Clone%2A>方法用來建立凍結物件的可修改複製品。  
  
## <a name="example"></a>範例  
 下列範例會建立凍結的可修改複製品<xref:System.Windows.Media.SolidColorBrush>物件。  
  
 [!code-csharp[freezablesample_procedural#CloneExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
 如需詳細資訊<xref:System.Windows.Freezable>物件，請參閱[Freezable 物件概觀](freezable-objects-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CloneCurrentValue%2A>
- [Freezable 物件概觀](freezable-objects-overview.md)
- [HOW-TO 主題](base-elements-how-to-topics.md)
