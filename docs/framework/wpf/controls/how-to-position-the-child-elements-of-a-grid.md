---
title: HOW TO：置放 Grid 的子項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: a1b567356588d6798bae5d73d3d410882d087986
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538670"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a>HOW TO：置放 Grid 的子項目
此範例示範如何使用 get 和 set 方法上定義之<xref:System.Windows.Controls.Grid>来放置子項目。  
  
## <a name="example"></a>範例  
 下列範例會定義父代<xref:System.Windows.Controls.Grid>項目 (`grid1`)，其具有三個資料行和三個資料列。 子系<xref:System.Windows.Shapes.Rectangle>項目 (`rect1`) 新增至<xref:System.Windows.Controls.Grid>中資料行位置為零，資料列位置為零。 <xref:System.Windows.Controls.Button> 項目代表的方法，可以呼叫重新定位<xref:System.Windows.Shapes.Rectangle>內的項目<xref:System.Windows.Controls.Grid>。 當使用者按一下按鈕時，相關的方法就會啟動。  
  
 [!code-xaml[gridGetSetMethods](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 下列範例中，程式碼後置處理方法的按鈕<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件引發。 該範例會寫入至這些方法呼叫<xref:System.Windows.Controls.TextBlock>使用相關的項目 get 方法，以輸出新的屬性值為字串。  
  
 [!code-csharp[gridGetSetMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 以下是完成的結果 ！
 
 ![螢幕擷取畫面說明兩個資料行的 WPF 使用者介面，右邊有 3x3 的方格，左邊有之間的資料行和方格資料列移動的彩色的矩形的按鈕](./media/grid-methods-sample.png) 
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Controls.Grid>
- [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)
