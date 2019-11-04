---
title: 操作說明：為實作 GridView 之 ListView 中的資料列設定樣式
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: 150988aab368e3ffef0107d29bea5ebc53163946
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459317"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a><span data-ttu-id="60d23-102">操作說明：為實作 GridView 之 ListView 中的資料列設定樣式</span><span class="sxs-lookup"><span data-stu-id="60d23-102">How to: Style a Row in a ListView That Implements a GridView</span></span>
<span data-ttu-id="60d23-103">這個範例示範如何在 <xref:System.Windows.Controls.ListView> 控制項中，將執行 <xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ListView.View%2A> 模式的資料列樣式。</span><span class="sxs-lookup"><span data-stu-id="60d23-103">This example shows how to style a row in a <xref:System.Windows.Controls.ListView> control that implements a <xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ListView.View%2A> mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60d23-104">範例</span><span class="sxs-lookup"><span data-stu-id="60d23-104">Example</span></span>  
 <span data-ttu-id="60d23-105">您可以藉由在 [<xref:System.Windows.Controls.ListView>] 控制項上設定 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>，將 <xref:System.Windows.Controls.ListView> 控制項中的資料列樣式。</span><span class="sxs-lookup"><span data-stu-id="60d23-105">You can style a row in a <xref:System.Windows.Controls.ListView> control by setting an <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> on the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="60d23-106">針對以 <xref:System.Windows.Controls.ListViewItem> 物件表示的專案，設定其樣式。</span><span class="sxs-lookup"><span data-stu-id="60d23-106">Set the style for its items that are represented as <xref:System.Windows.Controls.ListViewItem> objects.</span></span> <span data-ttu-id="60d23-107"><xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 會參考用來顯示資料列內容的 <xref:System.Windows.Controls.ControlTemplate> 物件。</span><span class="sxs-lookup"><span data-stu-id="60d23-107">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references the <xref:System.Windows.Controls.ControlTemplate> objects that are used to display the row content.</span></span>  
  
 <span data-ttu-id="60d23-108">完整範例 (下列範例的擷取來源) 會顯示一個儲存在 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料庫中歌曲資訊的集合。</span><span class="sxs-lookup"><span data-stu-id="60d23-108">The complete sample, which the following examples are extracted from, displays a collection of song information that is stored in an [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] database.</span></span> <span data-ttu-id="60d23-109">資料庫中的每一首歌都有一個評等欄位，而此欄位的值會指定歌曲資訊資料列的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="60d23-109">Each song in the database has a rating field and the value of this field specifies how to display a row of song information.</span></span>  
  
 <span data-ttu-id="60d23-110">下列範例示範如何定義代表歌曲集合中歌曲的 <xref:System.Windows.Controls.ListViewItem> 物件 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>。</span><span class="sxs-lookup"><span data-stu-id="60d23-110">The following example shows how to define <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> for the <xref:System.Windows.Controls.ListViewItem> objects that represent the songs in the song collection.</span></span> <span data-ttu-id="60d23-111"><xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 會參考 <xref:System.Windows.Controls.ControlTemplate> 物件，以指定如何顯示歌曲資訊的資料列。</span><span class="sxs-lookup"><span data-stu-id="60d23-111">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references <xref:System.Windows.Controls.ControlTemplate> objects that specify how to display a row of song information.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 <span data-ttu-id="60d23-112">下列範例顯示將文字字串 `"Strongly Recommended"` 加入資料列的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="60d23-112">The following example shows a <xref:System.Windows.Controls.ControlTemplate> that adds the text string `"Strongly Recommended"` to the row.</span></span> <span data-ttu-id="60d23-113">此範本會在 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 中參照，並會在歌曲的評等值為5（5）時顯示。</span><span class="sxs-lookup"><span data-stu-id="60d23-113">This template is referenced in the <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> and displays when the song's rating has a value of 5 (five).</span></span> <span data-ttu-id="60d23-114"><xref:System.Windows.Controls.ControlTemplate> 包含 <xref:System.Windows.Controls.GridViewRowPresenter> 物件，它會在資料行中配置資料列的內容，如 <xref:System.Windows.Controls.GridView> 視圖模式所定義。</span><span class="sxs-lookup"><span data-stu-id="60d23-114">The <xref:System.Windows.Controls.ControlTemplate> includes a <xref:System.Windows.Controls.GridViewRowPresenter> object that lays out the contents of the row in columns as defined by the <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 <span data-ttu-id="60d23-115">下列範例會定義 <xref:System.Windows.Controls.GridView>。</span><span class="sxs-lookup"><span data-stu-id="60d23-115">The following example defines <xref:System.Windows.Controls.GridView>.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a><span data-ttu-id="60d23-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="60d23-116">See also</span></span>

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="60d23-117">「如何」主題</span><span class="sxs-lookup"><span data-stu-id="60d23-117">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="60d23-118">ListView 概觀</span><span class="sxs-lookup"><span data-stu-id="60d23-118">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="60d23-119">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="60d23-119">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
