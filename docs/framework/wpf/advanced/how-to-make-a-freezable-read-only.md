---
title: HOW TO：將 Freezable 設為唯讀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
ms.openlocfilehash: 5748b7929db18578bbe00e3217b1578ac5fbc0f4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614595"
---
# <a name="how-to-make-a-freezable-read-only"></a>HOW TO：將 Freezable 設為唯讀
此範例示範如何製作<xref:System.Windows.Freezable>唯讀，藉由呼叫其<xref:System.Windows.Freezable.Freeze%2A>方法。  
  
 您不能凍結<xref:System.Windows.Freezable>物件的下列條件的任何一個是否`true`關於物件：  
  
- 它具有動畫，或資料繫結屬性。  
  
- 它的動態資源所設定的屬性。 如需有關動態資源的詳細資訊，請參閱[XAML 資源](xaml-resources.md)。  
  
- 它包含<xref:System.Windows.Freezable>無法凍結的子物件。  
  
 如果這些條件都`false`針對您<xref:System.Windows.Freezable>物件，而且您不想要修改它，請考慮以獲得效能優勢進行凍結。  
  
## <a name="example"></a>範例  
 下列範例會凍結<xref:System.Windows.Media.SolidColorBrush>，這是一種<xref:System.Windows.Freezable>物件。  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 如需詳細資訊<xref:System.Windows.Freezable>物件，請參閱[Freezable 物件概觀](freezable-objects-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CanFreeze%2A>
- <xref:System.Windows.Freezable.Freeze%2A>
- [Freezable 物件概觀](freezable-objects-overview.md)
- [HOW-TO 主題](base-elements-how-to-topics.md)
