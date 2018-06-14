---
title: 如何：決定 Freezable 是否凍結
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], determining if frozen
ms.assetid: 92e58baa-ee12-4a9e-ac3a-ca458807a8b2
ms.openlocfilehash: f6d20025d59a702357b12da9f5dc0f5887968143
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542749"
---
# <a name="how-to-determine-whether-a-freezable-is-frozen"></a>如何：決定 Freezable 是否凍結
這個範例示範如何判斷是否<xref:System.Windows.Freezable>物件已凍結。 如果您嘗試修改凍結<xref:System.Windows.Freezable>物件，就會擲回<xref:System.InvalidOperationException>。 若要避免擲回這個例外狀況，請使用<xref:System.Windows.Freezable.IsFrozen%2A>屬性<xref:System.Windows.Freezable>物件，以判斷是否已凍結。  
  
## <a name="example"></a>範例  
 下列範例會凍結<xref:System.Windows.Media.SolidColorBrush>，然後使用測試<xref:System.Windows.Freezable.IsFrozen%2A>屬性來判斷是否已凍結。  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 如需有關<xref:System.Windows.Freezable>物件，請參閱[Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.IsFrozen%2A>  
 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
