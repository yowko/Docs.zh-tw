---
title: "如何：置放 Grid 的子項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0ca385e1aee10fb10ac3e912999aec3a11d03ab4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a>如何：置放 Grid 的子項目
這個範例示範如何使用 get 和 set 方法上定義之<xref:System.Windows.Controls.Grid>来放置子項目。  
  
## <a name="example"></a>範例  
 下列範例會定義父代<xref:System.Windows.Controls.Grid>元素 (`grid1`)，其具有三個資料行和三個資料列。 子系<xref:System.Windows.Shapes.Rectangle>元素 (`rect1`) 加入至<xref:System.Windows.Controls.Grid>中資料行位置為零，資料列位置為零。 <xref:System.Windows.Controls.Button>項目代表的方法，可以呼叫來重新調整位置<xref:System.Windows.Shapes.Rectangle>內的項目<xref:System.Windows.Controls.Grid>。 當使用者按一下按鈕時，就會啟動相關的方法。  
  
 [!code-xaml[gridGetSetMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml#1)]  
  
 下列範例中，程式碼後置處理方法的按鈕<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件引發。 範例會將這些方法呼叫<xref:System.Windows.Controls.TextBlock>使用相關的項目有 get 的方法輸出為字串的新屬性值。  
  
 [!code-csharp[gridGetSetMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Controls.Grid>  
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)
