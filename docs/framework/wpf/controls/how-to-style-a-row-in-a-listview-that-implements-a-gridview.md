---
title: "操作說明：為實作 GridView 之 ListView 中的資料列設定樣式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1e37d70fe1cb6aefb1404424c1a8f5339e0badf7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a><span data-ttu-id="f70f2-102">操作說明：為實作 GridView 之 ListView 中的資料列設定樣式</span><span class="sxs-lookup"><span data-stu-id="f70f2-102">How to: Style a Row in a ListView That Implements a GridView</span></span>
<span data-ttu-id="f70f2-103">這個範例示範如何設定樣式中的資料列<xref:System.Windows.Controls.ListView>實作控制項<xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ListView.View%2A>模式。</span><span class="sxs-lookup"><span data-stu-id="f70f2-103">This example shows how to style a row in a <xref:System.Windows.Controls.ListView> control that implements a <xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ListView.View%2A> mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f70f2-104">範例</span><span class="sxs-lookup"><span data-stu-id="f70f2-104">Example</span></span>  
 <span data-ttu-id="f70f2-105">您可以設定樣式中的資料列<xref:System.Windows.Controls.ListView>藉由設定控制<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>上<xref:System.Windows.Controls.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="f70f2-105">You can style a row in a <xref:System.Windows.Controls.ListView> control by setting an <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> on the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="f70f2-106">將會以表示其項目的樣式設定<xref:System.Windows.Controls.ListViewItem>物件。</span><span class="sxs-lookup"><span data-stu-id="f70f2-106">Set the style for its items that are represented as <xref:System.Windows.Controls.ListViewItem> objects.</span></span> <span data-ttu-id="f70f2-107"><xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>參考<xref:System.Windows.Controls.ControlTemplate>用來顯示資料列內容的物件。</span><span class="sxs-lookup"><span data-stu-id="f70f2-107">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references the <xref:System.Windows.Controls.ControlTemplate> objects that are used to display the row content.</span></span>  
  
 <span data-ttu-id="f70f2-108">完整範例 (下列範例的擷取來源) 會顯示一個儲存在 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料庫中歌曲資訊的集合。</span><span class="sxs-lookup"><span data-stu-id="f70f2-108">The complete sample, which the following examples are extracted from, displays a collection of song information that is stored in an [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] database.</span></span> <span data-ttu-id="f70f2-109">資料庫中的每一首歌都有一個評等欄位，而此欄位的值會指定歌曲資訊資料列的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="f70f2-109">Each song in the database has a rating field and the value of this field specifies how to display a row of song information.</span></span>  
  
 <span data-ttu-id="f70f2-110">下列範例示範如何定義<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>如<xref:System.Windows.Controls.ListViewItem>代表歌曲集合中的歌曲的物件。</span><span class="sxs-lookup"><span data-stu-id="f70f2-110">The following example shows how to define <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> for the <xref:System.Windows.Controls.ListViewItem> objects that represent the songs in the song collection.</span></span> <span data-ttu-id="f70f2-111"><xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>參考<xref:System.Windows.Controls.ControlTemplate>指定如何顯示歌曲資訊的資料列的物件。</span><span class="sxs-lookup"><span data-stu-id="f70f2-111">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references <xref:System.Windows.Controls.ControlTemplate> objects that specify how to display a row of song information.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 <span data-ttu-id="f70f2-112">下列範例所示<xref:System.Windows.Controls.ControlTemplate>，將文字字串加入`"Strongly Recommended"`資料列。</span><span class="sxs-lookup"><span data-stu-id="f70f2-112">The following example shows a <xref:System.Windows.Controls.ControlTemplate> that adds the text string `"Strongly Recommended"` to the row.</span></span> <span data-ttu-id="f70f2-113">此範本會參考<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>並顯示當歌曲的評等的值為 5 （五個）。</span><span class="sxs-lookup"><span data-stu-id="f70f2-113">This template is referenced in the <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> and displays when the song's rating has a value of 5 (five).</span></span> <span data-ttu-id="f70f2-114"><xref:System.Windows.Controls.ControlTemplate>包含<xref:System.Windows.Controls.GridViewRowPresenter>配置所定義的資料行中的資料列內容的物件<xref:System.Windows.Controls.GridView>檢視模式。</span><span class="sxs-lookup"><span data-stu-id="f70f2-114">The <xref:System.Windows.Controls.ControlTemplate> includes a <xref:System.Windows.Controls.GridViewRowPresenter> object that lays out the contents of the row in columns as defined by the <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 <span data-ttu-id="f70f2-115">下列範例會定義<xref:System.Windows.Controls.GridView>。</span><span class="sxs-lookup"><span data-stu-id="f70f2-115">The following example defines <xref:System.Windows.Controls.GridView>.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a><span data-ttu-id="f70f2-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="f70f2-116">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="f70f2-117">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="f70f2-117">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="f70f2-118">ListView 概觀</span><span class="sxs-lookup"><span data-stu-id="f70f2-118">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="f70f2-119">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="f70f2-119">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
