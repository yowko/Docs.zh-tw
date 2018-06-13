---
title: 如何：將搜尋能力加入至 ListView 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- lists [Windows Forms], enabling searching
- list views [Windows Forms], enabling searching
- ListView control [Windows Forms], adding search capabilities
- searching [Windows Forms], adding search capabilities to ListView control
ms.assetid: 557782d9-b705-4bab-b496-9938afddac82
ms.openlocfilehash: 2049638998f7a8d099e14fab9c95384a49c67833
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528270"
---
# <a name="how-to-add-search-capabilities-to-a-listview-control"></a><span data-ttu-id="9b264-102">如何：將搜尋能力加入至 ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="9b264-102">How to: Add Search Capabilities to a ListView Control</span></span>
<span data-ttu-id="9b264-103">有時候當使用大型清單中的項目時，才<xref:System.Windows.Forms.ListView>控制項，您想要提供給使用者的搜尋能力。</span><span class="sxs-lookup"><span data-stu-id="9b264-103">Oftentimes when working with a large list of items in a <xref:System.Windows.Forms.ListView> control, you want to offer search capabilities to the user.</span></span> <span data-ttu-id="9b264-104"><xref:System.Windows.Forms.ListView>控制兩個不同的方式提供這項功能： 文字比對和搜尋的位置。</span><span class="sxs-lookup"><span data-stu-id="9b264-104">The <xref:System.Windows.Forms.ListView> control offers this capability in two different ways: text matching and location searching.</span></span>  
  
 <span data-ttu-id="9b264-105"><xref:System.Windows.Forms.ListView.FindItemWithText%2A>方法可讓您執行的文字搜尋<xref:System.Windows.Forms.ListView>在清單或詳細資料檢視中，指定搜尋字串和選擇性的開始和結束索引。</span><span class="sxs-lookup"><span data-stu-id="9b264-105">The <xref:System.Windows.Forms.ListView.FindItemWithText%2A> method allows you to perform a text search on a <xref:System.Windows.Forms.ListView> in list or details view, given a search string and an optional starting and ending index.</span></span> <span data-ttu-id="9b264-106">相反地，<xref:System.Windows.Forms.ListView.FindNearestItem%2A>方法可讓您尋找中的項目<xref:System.Windows.Forms.ListView>在圖示或並排顯示檢視中，提供一組 x 和 y 座標和搜尋方向。</span><span class="sxs-lookup"><span data-stu-id="9b264-106">In contrast, the <xref:System.Windows.Forms.ListView.FindNearestItem%2A> method allows you to find an item in a <xref:System.Windows.Forms.ListView> in icon or tile view, given a set of x- and y-coordinates and a direction to search.</span></span>  
  
### <a name="to-find-an-item-using-text"></a><span data-ttu-id="9b264-107">若要尋找的項目，使用文字</span><span class="sxs-lookup"><span data-stu-id="9b264-107">To find an item using text</span></span>  
  
1.  <span data-ttu-id="9b264-108">建立<xref:System.Windows.Forms.ListView>與<xref:System.Windows.Forms.ListView.View%2A>屬性設定為<xref:System.Windows.Forms.View.Details>或<xref:System.Windows.Forms.View.List>，並於其中填入<xref:System.Windows.Forms.ListView>與項目。</span><span class="sxs-lookup"><span data-stu-id="9b264-108">Create a <xref:System.Windows.Forms.ListView> with the <xref:System.Windows.Forms.ListView.View%2A> property set to <xref:System.Windows.Forms.View.Details> or <xref:System.Windows.Forms.View.List>, and then populate the <xref:System.Windows.Forms.ListView> with items.</span></span>  
  
2.  <span data-ttu-id="9b264-109">呼叫<xref:System.Windows.Forms.ListView.FindItemWithText%2A>方法，傳遞您想要尋找之項目的文字。</span><span class="sxs-lookup"><span data-stu-id="9b264-109">Call the <xref:System.Windows.Forms.ListView.FindItemWithText%2A> method, passing the text of the item you would like to find.</span></span>  
  
3.  <span data-ttu-id="9b264-110">下列程式碼範例示範如何建立基本<xref:System.Windows.Forms.ListView>，填入項目，並使用使用者的文字輸入清單中尋找項目。</span><span class="sxs-lookup"><span data-stu-id="9b264-110">The following code example demonstrates how to create a basic <xref:System.Windows.Forms.ListView>, populate it with items, and use text input from the user to find an item in the list.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#1)]  
  
### <a name="to-find-an-item-using-x--and-y-coordinates"></a><span data-ttu-id="9b264-111">若要尋找使用 x 和 y 座標的項目</span><span class="sxs-lookup"><span data-stu-id="9b264-111">To find an item using x- and y-coordinates</span></span>  
  
1.  <span data-ttu-id="9b264-112">建立<xref:System.Windows.Forms.ListView>與<xref:System.Windows.Forms.View>屬性設定為<xref:System.Windows.Forms.View.SmallIcon>或<xref:System.Windows.Forms.View.LargeIcon>，並於其中填入<xref:System.Windows.Forms.ListView>與項目。</span><span class="sxs-lookup"><span data-stu-id="9b264-112">Create a <xref:System.Windows.Forms.ListView> with the <xref:System.Windows.Forms.View> property set to <xref:System.Windows.Forms.View.SmallIcon> or <xref:System.Windows.Forms.View.LargeIcon>, and then populate the <xref:System.Windows.Forms.ListView> with items.</span></span>  
  
2.  <span data-ttu-id="9b264-113">呼叫<xref:System.Windows.Forms.ListView.FindNearestItem%2A>方法，傳遞所需 x 和 y 座標和您想要搜尋的方向。</span><span class="sxs-lookup"><span data-stu-id="9b264-113">Call the <xref:System.Windows.Forms.ListView.FindNearestItem%2A> method, passing the desired x- and y-coordinates and the direction you would like to search.</span></span>  
  
3.  <span data-ttu-id="9b264-114">下列程式碼範例示範如何建立基本的圖示<xref:System.Windows.Forms.ListView>，填入項目和擷取<xref:System.Windows.Forms.Control.MouseDown>事件，以尋找最新的方向中最接近的項目。</span><span class="sxs-lookup"><span data-stu-id="9b264-114">The following code example demonstrates how to create a basic icon <xref:System.Windows.Forms.ListView>, populate it with items, and capture the <xref:System.Windows.Forms.Control.MouseDown> event to find the nearest item in the up direction.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#2)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#2)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="9b264-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b264-115">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.FindItemWithText%2A>  
 <xref:System.Windows.Forms.ListView.FindNearestItem%2A>  
 [<span data-ttu-id="9b264-116">ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="9b264-116">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="9b264-117">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="9b264-117">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="9b264-118">操作說明：使用 Windows Forms ListView 控制項加入和移除項目</span><span class="sxs-lookup"><span data-stu-id="9b264-118">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
