---
title: 如何：建立 Freezable 唯讀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
ms.openlocfilehash: be3abd74a71fc711cd9f4bf6796b7d55017355ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-make-a-freezable-read-only"></a>如何：建立 Freezable 唯讀
這個範例示範如何讓<xref:System.Windows.Freezable>唯讀藉由呼叫其<xref:System.Windows.Freezable.Freeze%2A>方法。  
  
 無法凍結<xref:System.Windows.Freezable>物件時如果下列情形的任一`true`之物件的相關：  
  
-   它具有動畫或資料繫結屬性。  
  
-   它的動態資源所設定的屬性。 如需動態資源的詳細資訊，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
-   它包含<xref:System.Windows.Freezable>無法凍結的子物件。  
  
 如果這些條件都`false`如您<xref:System.Windows.Freezable>物件，而且您不想要修改它，請考慮凍結它取得效能優勢。  
  
## <a name="example"></a>範例  
 下列範例會凍結<xref:System.Windows.Media.SolidColorBrush>，這是一種<xref:System.Windows.Freezable>物件。  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 如需有關<xref:System.Windows.Freezable>物件，請參閱[Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.CanFreeze%2A>  
 <xref:System.Windows.Freezable.Freeze%2A>  
 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
