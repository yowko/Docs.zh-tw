---
title: HOW TO：處理 Loaded 事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XAML [WPF], Loaded events
- events [WPF], Loaded
- Loaded events [WPF]
ms.assetid: 0cf8d003-8441-4df4-807a-6db09347e829
ms.openlocfilehash: a4916d3cfd20d082a8466f61fc74e16db2f0f346
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353344"
---
# <a name="how-to-handle-a-loaded-event"></a>HOW TO：處理 Loaded 事件
此範例示範如何處理<xref:System.Windows.FrameworkElement.Loaded?displayProperty=nameWithType>事件，並處理該事件之適當情節。 處理常式會建立<xref:System.Windows.Controls.Button>當頁面載入。  
  
## <a name="example"></a>範例  
 下列範例會使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]以及程式碼後置檔案。  
  
 [!code-xaml[FELoaded#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FELoaded#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml.cs#handler)]
 [!code-vb[FELoaded#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FELoaded/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.FrameworkElement>
- [物件存留期事件](object-lifetime-events.md)
- [路由事件概觀](routed-events-overview.md)
- [HOW-TO 主題](base-elements-how-to-topics.md)
