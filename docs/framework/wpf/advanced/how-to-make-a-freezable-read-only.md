---
title: 如何：建立 Freezable 唯讀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
ms.openlocfilehash: 4185966d864be425bc631953461f6f27ab983bee
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460065"
---
# <a name="how-to-make-a-freezable-read-only"></a>如何：建立 Freezable 唯讀
這個範例示範如何藉由呼叫其 <xref:System.Windows.Freezable.Freeze%2A> 方法，讓 <xref:System.Windows.Freezable> 唯讀。  
  
 如果 `true` 關於物件的下列任何一種情況，您就無法凍結 <xref:System.Windows.Freezable> 物件：  
  
- 它具有動畫或資料系結屬性。  
  
- 它具有動態資源所設定的屬性。 如需動態資源的詳細資訊，請參閱[XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。  
  
- 它包含無法凍結的 <xref:System.Windows.Freezable> 子物件。  
  
 如果您的 <xref:System.Windows.Freezable> 物件 `false` 這些條件，而您不想要修改它，請考慮將其凍結以獲得效能優勢。  
  
## <a name="example"></a>範例  
 下列範例會凍結 <xref:System.Windows.Media.SolidColorBrush>，這是 <xref:System.Windows.Freezable> 物件的一種類型。  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 如需 <xref:System.Windows.Freezable> 物件的詳細資訊，請參閱可[凍結物件的總覽](freezable-objects-overview.md)。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CanFreeze%2A>
- <xref:System.Windows.Freezable.Freeze%2A>
- [Freezable 物件概觀](freezable-objects-overview.md)
- [「如何」主題](base-elements-how-to-topics.md)
