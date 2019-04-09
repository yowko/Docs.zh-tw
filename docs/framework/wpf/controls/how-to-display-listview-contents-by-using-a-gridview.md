---
title: HOW TO：使用 GridView 顯示 ListView 內容
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
ms.openlocfilehash: 9b467c95d541c326a41d1ed4bd9eb5c87e25bd5c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112784"
---
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a><span data-ttu-id="f854b-102">HOW TO：使用 GridView 顯示 ListView 內容</span><span class="sxs-lookup"><span data-stu-id="f854b-102">How to: Display ListView Contents by Using a GridView</span></span>
<span data-ttu-id="f854b-103">此範例示範如何定義<xref:System.Windows.Controls.GridView>檢視模式<xref:System.Windows.Controls.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="f854b-103">This example shows how to define a <xref:System.Windows.Controls.GridView> view mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f854b-104">範例</span><span class="sxs-lookup"><span data-stu-id="f854b-104">Example</span></span>  
 <span data-ttu-id="f854b-105">您可以定義的檢視模式<xref:System.Windows.Controls.GridView>藉由指定<xref:System.Windows.Controls.GridViewColumn>物件。</span><span class="sxs-lookup"><span data-stu-id="f854b-105">You can define the view mode of a <xref:System.Windows.Controls.GridView> by specifying <xref:System.Windows.Controls.GridViewColumn> objects.</span></span> <span data-ttu-id="f854b-106">下列範例示範如何定義<xref:System.Windows.Controls.GridViewColumn>繫結至指定的資料內容的物件<xref:System.Windows.Controls.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="f854b-106">The following example shows how to define <xref:System.Windows.Controls.GridViewColumn> objects that bind to the data content that is specified for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="f854b-107">這<xref:System.Windows.Controls.GridView>範例會指定三個<xref:System.Windows.Controls.GridViewColumn>物件會對應至`FirstName`， `LastName`，並`EmployeeNumber`欄位`EmployeeInfoDataSource`設定為<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>的<xref:System.Windows.Controls.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="f854b-107">This <xref:System.Windows.Controls.GridView> example specifies three <xref:System.Windows.Controls.GridViewColumn> objects that map to the `FirstName`, `LastName`, and `EmployeeNumber` fields of the `EmployeeInfoDataSource` that is set as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> of the <xref:System.Windows.Controls.ListView> control.</span></span>  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 <span data-ttu-id="f854b-108">下圖顯示此範例中的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="f854b-108">The following illustration shows how this example appears.</span></span>  
  
 ![螢幕擷取畫面，顯示 ListView 與 GridView 輸出。](./media/gridview-overview/listview-gridview-output.jpg)  
  
## <a name="see-also"></a><span data-ttu-id="f854b-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f854b-110">See also</span></span>

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="f854b-111">ListView 概觀</span><span class="sxs-lookup"><span data-stu-id="f854b-111">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="f854b-112">GridView 概觀</span><span class="sxs-lookup"><span data-stu-id="f854b-112">GridView Overview</span></span>](gridview-overview.md)
- [<span data-ttu-id="f854b-113">HOW TO 主題</span><span class="sxs-lookup"><span data-stu-id="f854b-113">How-to Topics</span></span>](listview-how-to-topics.md)
