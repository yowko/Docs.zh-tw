---
title: HOW TO：在實作 GridView 的 ListView 中設定資料列的樣式
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: 9af8d10c7db2d3bbe8b9443402cbb1cfeaa7edb3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052010"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a><span data-ttu-id="03180-102">HOW TO：在實作 GridView 的 ListView 中設定資料列的樣式</span><span class="sxs-lookup"><span data-stu-id="03180-102">How to: Style a Row in a ListView That Implements a GridView</span></span>
<span data-ttu-id="03180-103">此範例示範如何在資料列的樣式<xref:System.Windows.Controls.ListView>控制項，可實作<xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ListView.View%2A>模式。</span><span class="sxs-lookup"><span data-stu-id="03180-103">This example shows how to style a row in a <xref:System.Windows.Controls.ListView> control that implements a <xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ListView.View%2A> mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03180-104">範例</span><span class="sxs-lookup"><span data-stu-id="03180-104">Example</span></span>  
 <span data-ttu-id="03180-105">您可以在資料列的樣式<xref:System.Windows.Controls.ListView>控制項，藉由設定<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>上<xref:System.Windows.Controls.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="03180-105">You can style a row in a <xref:System.Windows.Controls.ListView> control by setting an <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> on the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="03180-106">設定以其項目的樣式<xref:System.Windows.Controls.ListViewItem>物件。</span><span class="sxs-lookup"><span data-stu-id="03180-106">Set the style for its items that are represented as <xref:System.Windows.Controls.ListViewItem> objects.</span></span> <span data-ttu-id="03180-107"><xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>參考<xref:System.Windows.Controls.ControlTemplate>用來顯示資料列內容的物件。</span><span class="sxs-lookup"><span data-stu-id="03180-107">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references the <xref:System.Windows.Controls.ControlTemplate> objects that are used to display the row content.</span></span>  
  
 <span data-ttu-id="03180-108">完整範例 (下列範例的擷取來源) 會顯示一個儲存在 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料庫中歌曲資訊的集合。</span><span class="sxs-lookup"><span data-stu-id="03180-108">The complete sample, which the following examples are extracted from, displays a collection of song information that is stored in an [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] database.</span></span> <span data-ttu-id="03180-109">資料庫中的每一首歌都有一個評等欄位，而此欄位的值會指定歌曲資訊資料列的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="03180-109">Each song in the database has a rating field and the value of this field specifies how to display a row of song information.</span></span>  
  
 <span data-ttu-id="03180-110">下列範例示範如何定義<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>針對<xref:System.Windows.Controls.ListViewItem>代表歌曲集合中的歌曲的物件。</span><span class="sxs-lookup"><span data-stu-id="03180-110">The following example shows how to define <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> for the <xref:System.Windows.Controls.ListViewItem> objects that represent the songs in the song collection.</span></span> <span data-ttu-id="03180-111"><xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>參考<xref:System.Windows.Controls.ControlTemplate>物件，以指定如何顯示歌曲資訊資料列。</span><span class="sxs-lookup"><span data-stu-id="03180-111">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references <xref:System.Windows.Controls.ControlTemplate> objects that specify how to display a row of song information.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 <span data-ttu-id="03180-112">下列範例所示<xref:System.Windows.Controls.ControlTemplate>，將文字字串加入`"Strongly Recommended"`資料列。</span><span class="sxs-lookup"><span data-stu-id="03180-112">The following example shows a <xref:System.Windows.Controls.ControlTemplate> that adds the text string `"Strongly Recommended"` to the row.</span></span> <span data-ttu-id="03180-113">此範本中參考<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>，並且在歌曲的評等的值為 5 （五） 時顯示。</span><span class="sxs-lookup"><span data-stu-id="03180-113">This template is referenced in the <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> and displays when the song's rating has a value of 5 (five).</span></span> <span data-ttu-id="03180-114"><xref:System.Windows.Controls.ControlTemplate>包含<xref:System.Windows.Controls.GridViewRowPresenter>配置的資料行中的資料列的內容所定義的物件<xref:System.Windows.Controls.GridView>檢視模式。</span><span class="sxs-lookup"><span data-stu-id="03180-114">The <xref:System.Windows.Controls.ControlTemplate> includes a <xref:System.Windows.Controls.GridViewRowPresenter> object that lays out the contents of the row in columns as defined by the <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 <span data-ttu-id="03180-115">下列範例會定義<xref:System.Windows.Controls.GridView>。</span><span class="sxs-lookup"><span data-stu-id="03180-115">The following example defines <xref:System.Windows.Controls.GridView>.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a><span data-ttu-id="03180-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03180-116">See also</span></span>

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="03180-117">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="03180-117">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="03180-118">ListView 概觀</span><span class="sxs-lookup"><span data-stu-id="03180-118">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="03180-119">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="03180-119">Styling and Templating</span></span>](styling-and-templating.md)
