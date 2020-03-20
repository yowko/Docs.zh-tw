---
title: 如何：置放 Grid 的子項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: 44268c32732a9409ea30f028adaa8a2631a06c5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186712"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a><span data-ttu-id="dd492-102">如何：置放 Grid 的子項目</span><span class="sxs-lookup"><span data-stu-id="dd492-102">How to: Position the Child Elements of a Grid</span></span>
<span data-ttu-id="dd492-103">此示例演示如何使用定義 get<xref:System.Windows.Controls.Grid>和設置方法來定位子項目。</span><span class="sxs-lookup"><span data-stu-id="dd492-103">This example shows how to use the get and set methods that are defined on <xref:System.Windows.Controls.Grid> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd492-104">範例</span><span class="sxs-lookup"><span data-stu-id="dd492-104">Example</span></span>  
 <span data-ttu-id="dd492-105">下面的示例定義具有三列和<xref:System.Windows.Controls.Grid>三行`grid1`的父元素 （ ）。</span><span class="sxs-lookup"><span data-stu-id="dd492-105">The following example defines a parent <xref:System.Windows.Controls.Grid> element (`grid1`) that has three columns and three rows.</span></span> <span data-ttu-id="dd492-106">子<xref:System.Windows.Shapes.Rectangle>元素 （`rect1`） 添加到列<xref:System.Windows.Controls.Grid>位置零，行位置零。</span><span class="sxs-lookup"><span data-stu-id="dd492-106">A child <xref:System.Windows.Shapes.Rectangle> element (`rect1`) is added to the <xref:System.Windows.Controls.Grid> in column position zero, row position zero.</span></span> <span data-ttu-id="dd492-107"><xref:System.Windows.Controls.Button>元素表示可以調用以重新置放<xref:System.Windows.Shapes.Rectangle>元素的方法。 <xref:System.Windows.Controls.Grid></span><span class="sxs-lookup"><span data-stu-id="dd492-107"><xref:System.Windows.Controls.Button> elements represent methods that can be called to reposition the <xref:System.Windows.Shapes.Rectangle> element within the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="dd492-108">當使用者按一下按鈕時，將啟動相關方法。</span><span class="sxs-lookup"><span data-stu-id="dd492-108">When a user clicks a button, the related method is activated.</span></span>  
  
 [!code-xaml[gridGetSetMethods](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 <span data-ttu-id="dd492-109">下面的代碼後面示例處理按鈕<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件引發的方法。</span><span class="sxs-lookup"><span data-stu-id="dd492-109">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> events raise.</span></span> <span data-ttu-id="dd492-110">該示例將這些方法調用寫入<xref:System.Windows.Controls.TextBlock>使用相關 get 方法將新屬性值輸出為字串的元素。</span><span class="sxs-lookup"><span data-stu-id="dd492-110">The example writes these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridGetSetMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 <span data-ttu-id="dd492-111">這是完成的結果！</span><span class="sxs-lookup"><span data-stu-id="dd492-111">Here is the finished result!</span></span>

 ![螢幕截圖描繪了包含兩列的 WPF 使用者介面，右側有一個 3 x 3 網格，左側有按鈕在網格的列和行之間移動彩色矩形](././media/grid-methods-sample.png)
  
## <a name="see-also"></a><span data-ttu-id="dd492-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd492-113">See also</span></span>

- <xref:System.Windows.Controls.Grid>
- [<span data-ttu-id="dd492-114">面板概觀</span><span class="sxs-lookup"><span data-stu-id="dd492-114">Panels Overview</span></span>](panels-overview.md)
