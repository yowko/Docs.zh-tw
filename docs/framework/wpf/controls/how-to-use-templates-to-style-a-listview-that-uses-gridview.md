---
title: "如何：使用範本為使用 GridView 的 ListView 設定樣式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ListView controls [WPF], styling
ms.assetid: 94bf964b-96c8-4bdf-a0c3-f5271b7cb565
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 246c144a18d7c1014096a6e37ad09b6eec5ad932
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-templates-to-style-a-listview-that-uses-gridview"></a><span data-ttu-id="8ba24-102">如何：使用範本為使用 GridView 的 ListView 設定樣式</span><span class="sxs-lookup"><span data-stu-id="8ba24-102">How to: Use Templates to Style a ListView That Uses GridView</span></span>
<span data-ttu-id="8ba24-103">這個範例示範如何使用<xref:System.Windows.DataTemplate>和<xref:System.Windows.Style>物件，指定的外觀<xref:System.Windows.Controls.ListView>使用控制項<xref:System.Windows.Controls.GridView>檢視模式。</span><span class="sxs-lookup"><span data-stu-id="8ba24-103">This example shows how to use the <xref:System.Windows.DataTemplate> and <xref:System.Windows.Style> objects to specify the appearance of a <xref:System.Windows.Controls.ListView> control that uses a <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ba24-104">範例</span><span class="sxs-lookup"><span data-stu-id="8ba24-104">Example</span></span>  
 <span data-ttu-id="8ba24-105">下列範例會顯示<xref:System.Windows.Style>和<xref:System.Windows.DataTemplate>物件可自訂的資料行標頭的外觀<xref:System.Windows.Controls.GridViewColumn>。</span><span class="sxs-lookup"><span data-stu-id="8ba24-105">The following examples show <xref:System.Windows.Style> and <xref:System.Windows.DataTemplate> objects that customize the appearance of a column header for a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheaderstyle)]  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheadertemplate)]  
  
 <span data-ttu-id="8ba24-106">下列範例示範如何使用這些<xref:System.Windows.Style>和<xref:System.Windows.DataTemplate>物件來設定<xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>和<xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A>屬性<xref:System.Windows.Controls.GridViewColumn>。</span><span class="sxs-lookup"><span data-stu-id="8ba24-106">The following example shows how to use these <xref:System.Windows.Style> and <xref:System.Windows.DataTemplate> objects to set the <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> and <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> properties of a <xref:System.Windows.Controls.GridViewColumn>.</span></span> <span data-ttu-id="8ba24-107"><xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>屬性定義的資料行儲存格的內容。</span><span class="sxs-lookup"><span data-stu-id="8ba24-107">The <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property defines the content of the column cells.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewColumnTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcolumntemplate)]  
  
 <span data-ttu-id="8ba24-108"><xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>和<xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A>只有兩種數個屬性，您可以用來自訂資料行的標頭外觀<xref:System.Windows.Controls.GridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="8ba24-108">The <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> and <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> are only two of several properties that you can use to customize column header appearance for a <xref:System.Windows.Controls.GridView> control.</span></span> <span data-ttu-id="8ba24-109">如需詳細資訊，請參閱 [GridView 資料行標頭樣式和範本概觀](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="8ba24-109">For more information, see [GridView Column Header Styles and Templates Overview](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md).</span></span>  
  
 <span data-ttu-id="8ba24-110">下列範例示範如何定義<xref:System.Windows.DataTemplate>之自訂中的資料格的外觀<xref:System.Windows.Controls.GridViewColumn>。</span><span class="sxs-lookup"><span data-stu-id="8ba24-110">The following example shows how to define a <xref:System.Windows.DataTemplate> that customizes the appearance of the cells in a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 <span data-ttu-id="8ba24-111">下列範例會示範如何使用這個<xref:System.Windows.DataTemplate>來定義的內容<xref:System.Windows.Controls.GridViewColumn>儲存格。</span><span class="sxs-lookup"><span data-stu-id="8ba24-111">The following example shows how to use this <xref:System.Windows.DataTemplate> to define the content of a <xref:System.Windows.Controls.GridViewColumn> cell.</span></span> <span data-ttu-id="8ba24-112">而不是使用此範本<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>屬性顯示在舊版<xref:System.Windows.Controls.GridViewColumn>範例。</span><span class="sxs-lookup"><span data-stu-id="8ba24-112">This template is used instead of the <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property that is shown in the previous <xref:System.Windows.Controls.GridViewColumn> example.</span></span>  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="8ba24-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ba24-113">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="8ba24-114">GridView 概觀</span><span class="sxs-lookup"><span data-stu-id="8ba24-114">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [<span data-ttu-id="8ba24-115">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="8ba24-115">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="8ba24-116">ListView 概觀</span><span class="sxs-lookup"><span data-stu-id="8ba24-116">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)
