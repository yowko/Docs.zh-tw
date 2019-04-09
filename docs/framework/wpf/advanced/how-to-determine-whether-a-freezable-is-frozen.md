---
title: HOW TO：決定 Freezable 是否凍結
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], determining if frozen
ms.assetid: 92e58baa-ee12-4a9e-ac3a-ca458807a8b2
ms.openlocfilehash: 6a63862d35f2c40289ea6445eb3dab8a2abe4a61
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197057"
---
# <a name="how-to-determine-whether-a-freezable-is-frozen"></a>HOW TO：決定 Freezable 是否凍結
此範例示範如何判斷是否<xref:System.Windows.Freezable>物件已凍結。 如果您嘗試修改凍結<xref:System.Windows.Freezable>物件，則會擲回<xref:System.InvalidOperationException>。 若要避免擲回這個例外狀況，請使用<xref:System.Windows.Freezable.IsFrozen%2A>屬性<xref:System.Windows.Freezable>物件，以判斷是否已凍結。  
  
## <a name="example"></a>範例  
 下列範例會凍結<xref:System.Windows.Media.SolidColorBrush>，然後使用測試<xref:System.Windows.Freezable.IsFrozen%2A>屬性來判斷是否已凍結。  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 如需詳細資訊<xref:System.Windows.Freezable>物件，請參閱[Freezable 物件概觀](freezable-objects-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.IsFrozen%2A>
- [Freezable 物件概觀](freezable-objects-overview.md)
- [HOW TO 主題](base-elements-how-to-topics.md)
