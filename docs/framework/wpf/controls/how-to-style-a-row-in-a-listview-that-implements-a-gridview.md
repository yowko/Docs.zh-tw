---
title: 如何：在使用 GridView 的 ListView 中為數據列建立樣式
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: 4b8b8e2f1b2d7207a37205d981bf2dab3f65122e
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271941"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a><span data-ttu-id="9a3ee-102">操作說明：為實作 GridView 之 ListView 中的資料列設定樣式</span><span class="sxs-lookup"><span data-stu-id="9a3ee-102">How to: Style a Row in a ListView That Implements a GridView</span></span>
<span data-ttu-id="9a3ee-103">這個範例示範如何在使用模式的控制項中為數據列建立樣式 <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView.View%2A> 。</span><span class="sxs-lookup"><span data-stu-id="9a3ee-103">This example shows how to style a row in a <xref:System.Windows.Controls.ListView> control that uses a <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView.View%2A> mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a3ee-104">範例</span><span class="sxs-lookup"><span data-stu-id="9a3ee-104">Example</span></span>  
 <span data-ttu-id="9a3ee-105">您可以設定控制項的來設定控制項的資料列樣式 <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> <xref:System.Windows.Controls.ListView> 。</span><span class="sxs-lookup"><span data-stu-id="9a3ee-105">You can style a row in a <xref:System.Windows.Controls.ListView> control by setting an <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> on the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="9a3ee-106">針對以物件表示的專案設定樣式 <xref:System.Windows.Controls.ListViewItem> 。</span><span class="sxs-lookup"><span data-stu-id="9a3ee-106">Set the style for its items that are represented as <xref:System.Windows.Controls.ListViewItem> objects.</span></span> <span data-ttu-id="9a3ee-107"><xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> <xref:System.Windows.Controls.ControlTemplate> 會參考用來顯示資料列內容的物件。</span><span class="sxs-lookup"><span data-stu-id="9a3ee-107">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references the <xref:System.Windows.Controls.ControlTemplate> objects that are used to display the row content.</span></span>  
  
 <span data-ttu-id="9a3ee-108">從下列範例解壓縮的完整範例，會顯示儲存在 XML 資料庫中的一組歌曲資訊。</span><span class="sxs-lookup"><span data-stu-id="9a3ee-108">The complete sample, which the following examples are extracted from, displays a collection of song information that is stored in an XML database.</span></span> <span data-ttu-id="9a3ee-109">資料庫中的每一首歌都有一個評等欄位，而此欄位的值會指定歌曲資訊資料列的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="9a3ee-109">Each song in the database has a rating field and the value of this field specifies how to display a row of song information.</span></span>  
  
 <span data-ttu-id="9a3ee-110">下列範例示範如何定義 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> <xref:System.Windows.Controls.ListViewItem> 代表 song 集合中之歌曲的物件。</span><span class="sxs-lookup"><span data-stu-id="9a3ee-110">The following example shows how to define <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> for the <xref:System.Windows.Controls.ListViewItem> objects that represent the songs in the song collection.</span></span> <span data-ttu-id="9a3ee-111"><xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>參考 <xref:System.Windows.Controls.ControlTemplate> 物件，這些物件會指定如何顯示歌曲資訊的資料列。</span><span class="sxs-lookup"><span data-stu-id="9a3ee-111">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references <xref:System.Windows.Controls.ControlTemplate> objects that specify how to display a row of song information.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 <span data-ttu-id="9a3ee-112">下列範例顯示 <xref:System.Windows.Controls.ControlTemplate> 將文字字串加入 `"Strongly Recommended"` 至資料列的。</span><span class="sxs-lookup"><span data-stu-id="9a3ee-112">The following example shows a <xref:System.Windows.Controls.ControlTemplate> that adds the text string `"Strongly Recommended"` to the row.</span></span> <span data-ttu-id="9a3ee-113">此範本會在中參考 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> ，並且會在歌曲的評等值為 5 (五) 時顯示。</span><span class="sxs-lookup"><span data-stu-id="9a3ee-113">This template is referenced in the <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> and displays when the song's rating has a value of 5 (five).</span></span> <span data-ttu-id="9a3ee-114"><xref:System.Windows.Controls.ControlTemplate>包含 <xref:System.Windows.Controls.GridViewRowPresenter> 物件，該物件會根據 view 模式所定義，在資料行中配置資料列的內容 <xref:System.Windows.Controls.GridView> 。</span><span class="sxs-lookup"><span data-stu-id="9a3ee-114">The <xref:System.Windows.Controls.ControlTemplate> includes a <xref:System.Windows.Controls.GridViewRowPresenter> object that lays out the contents of the row in columns as defined by the <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 <span data-ttu-id="9a3ee-115">下列範例會定義 <xref:System.Windows.Controls.GridView> 。</span><span class="sxs-lookup"><span data-stu-id="9a3ee-115">The following example defines <xref:System.Windows.Controls.GridView>.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a><span data-ttu-id="9a3ee-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a3ee-116">See also</span></span>

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="9a3ee-117">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="9a3ee-117">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="9a3ee-118">ListView 概觀</span><span class="sxs-lookup"><span data-stu-id="9a3ee-118">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="9a3ee-119">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="9a3ee-119">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
