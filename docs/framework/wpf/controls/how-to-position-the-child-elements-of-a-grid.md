---
title: HOW TO：置放 Grid 的子項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: 90115bc6192a33f4c27eaa75ebfe6a7c9d1458e5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369171"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a><span data-ttu-id="4d01c-102">HOW TO：置放 Grid 的子項目</span><span class="sxs-lookup"><span data-stu-id="4d01c-102">How to: Position the Child Elements of a Grid</span></span>
<span data-ttu-id="4d01c-103">此範例示範如何使用 get 和 set 方法上定義之<xref:System.Windows.Controls.Grid>来放置子項目。</span><span class="sxs-lookup"><span data-stu-id="4d01c-103">This example shows how to use the get and set methods that are defined on <xref:System.Windows.Controls.Grid> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d01c-104">範例</span><span class="sxs-lookup"><span data-stu-id="4d01c-104">Example</span></span>  
 <span data-ttu-id="4d01c-105">下列範例會定義父代<xref:System.Windows.Controls.Grid>項目 (`grid1`)，其具有三個資料行和三個資料列。</span><span class="sxs-lookup"><span data-stu-id="4d01c-105">The following example defines a parent <xref:System.Windows.Controls.Grid> element (`grid1`) that has three columns and three rows.</span></span> <span data-ttu-id="4d01c-106">子系<xref:System.Windows.Shapes.Rectangle>項目 (`rect1`) 新增至<xref:System.Windows.Controls.Grid>中資料行位置為零，資料列位置為零。</span><span class="sxs-lookup"><span data-stu-id="4d01c-106">A child <xref:System.Windows.Shapes.Rectangle> element (`rect1`) is added to the <xref:System.Windows.Controls.Grid> in column position zero, row position zero.</span></span> <span data-ttu-id="4d01c-107"><xref:System.Windows.Controls.Button> 項目代表的方法，可以呼叫重新定位<xref:System.Windows.Shapes.Rectangle>內的項目<xref:System.Windows.Controls.Grid>。</span><span class="sxs-lookup"><span data-stu-id="4d01c-107"><xref:System.Windows.Controls.Button> elements represent methods that can be called to reposition the <xref:System.Windows.Shapes.Rectangle> element within the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="4d01c-108">當使用者按一下按鈕時，相關的方法就會啟動。</span><span class="sxs-lookup"><span data-stu-id="4d01c-108">When a user clicks a button, the related method is activated.</span></span>  
  
 [!code-xaml[gridGetSetMethods](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 <span data-ttu-id="4d01c-109">下列範例中，程式碼後置處理方法的按鈕<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件引發。</span><span class="sxs-lookup"><span data-stu-id="4d01c-109">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> events raise.</span></span> <span data-ttu-id="4d01c-110">該範例會寫入至這些方法呼叫<xref:System.Windows.Controls.TextBlock>使用相關的項目 get 方法，以輸出新的屬性值為字串。</span><span class="sxs-lookup"><span data-stu-id="4d01c-110">The example writes these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridGetSetMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 <span data-ttu-id="4d01c-111">以下是完成的結果 ！</span><span class="sxs-lookup"><span data-stu-id="4d01c-111">Here is the finished result!</span></span>
 
 ![螢幕擷取畫面說明兩個資料行的 WPF 使用者介面，右邊有 3x3 的方格，左邊有之間的資料行和方格資料列移動的彩色的矩形的按鈕](././media/grid-methods-sample.png) 
  
## <a name="see-also"></a><span data-ttu-id="4d01c-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d01c-113">See also</span></span>
- <xref:System.Windows.Controls.Grid>
- [<span data-ttu-id="4d01c-114">面板概觀</span><span class="sxs-lookup"><span data-stu-id="4d01c-114">Panels Overview</span></span>](panels-overview.md)
