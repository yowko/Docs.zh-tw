---
title: "GridView 資料行行首樣式和範本概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- column headers [WPF], customizing
- ListView controls [WPF], GridView column header styles
- controls [WPF], ListView
- headers [WPF], customizing
- GridView view mode [WPF], customizing column headers
ms.assetid: 74835674-a39e-4ab5-9418-ad7f6ab7b956
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 996d6d5f531a866d4fc80acc3848cdf264901032
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="gridview-column-header-styles-and-templates-overview"></a><span data-ttu-id="e2581-102">GridView 資料行行首樣式和範本概觀</span><span class="sxs-lookup"><span data-stu-id="e2581-102">GridView Column Header Styles and Templates Overview</span></span>
<span data-ttu-id="e2581-103">這個概觀討論的屬性，用來自訂中的資料行標頭的優先順序<xref:System.Windows.Controls.GridView>檢視模式<xref:System.Windows.Controls.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="e2581-103">This overview discusses the order of precedence for properties that you use to customize a column header in the <xref:System.Windows.Controls.GridView> view mode of a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="customizing-a-column-header-in-a-gridview"></a><span data-ttu-id="e2581-104">自訂在 GridView 的資料行標頭</span><span class="sxs-lookup"><span data-stu-id="e2581-104">Customizing a Column Header in a GridView</span></span>  
 <span data-ttu-id="e2581-105">定義內容、 配置和樣式中的資料行標頭的屬性，<xref:System.Windows.Controls.GridView>找到許多相關的類別上。</span><span class="sxs-lookup"><span data-stu-id="e2581-105">The properties that define the content, layout, and style of a column header in a <xref:System.Windows.Controls.GridView> are found on many related classes.</span></span> <span data-ttu-id="e2581-106">其中某些屬性具有功能類似或相同。</span><span class="sxs-lookup"><span data-stu-id="e2581-106">Some of these properties have functionality that is similar or the same.</span></span>  
  
 <span data-ttu-id="e2581-107">下表中的資料列顯示一組執行相同的函式的內容。</span><span class="sxs-lookup"><span data-stu-id="e2581-107">The rows in the following table show groups of properties that perform the same function.</span></span> <span data-ttu-id="e2581-108">您可以使用這些屬性來自訂資料行標頭中的<xref:System.Windows.Controls.GridView>。</span><span class="sxs-lookup"><span data-stu-id="e2581-108">You can use these properties to customize the column headers in a <xref:System.Windows.Controls.GridView>.</span></span> <span data-ttu-id="e2581-109">相關屬性的優先順序是由右至左右欄中的屬性具有最高優先順序的位置。</span><span class="sxs-lookup"><span data-stu-id="e2581-109">The order of precedence for related properties is from right to left where the property in the farthest right column has the highest precedence.</span></span> <span data-ttu-id="e2581-110">例如，如果<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>上設定<xref:System.Windows.Controls.GridViewColumnHeader>物件和<xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>就會在相關聯集<xref:System.Windows.Controls.GridViewColumn>、<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>優先。</span><span class="sxs-lookup"><span data-stu-id="e2581-110">For example, if a <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> is set on the <xref:System.Windows.Controls.GridViewColumnHeader> object and the <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> is set on the associated <xref:System.Windows.Controls.GridViewColumn>, the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> takes precedence.</span></span> <span data-ttu-id="e2581-111">在此案例中，<xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="e2581-111">In this scenario, the <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> has no effect.</span></span>  
  
 <span data-ttu-id="e2581-112">**在 GridView 的資料行標頭的相關的屬性**</span><span class="sxs-lookup"><span data-stu-id="e2581-112">**Related properties for column headers in a GridView**</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="e2581-113">**類別**</span><span class="sxs-lookup"><span data-stu-id="e2581-113">**Classes**</span></span>|<xref:System.Windows.Controls.GridView>|<xref:System.Windows.Controls.GridViewColumn>|<xref:System.Windows.Controls.GridViewColumnHeader>|  
|<span data-ttu-id="e2581-114">**內容功能表屬性**</span><span class="sxs-lookup"><span data-stu-id="e2581-114">**Context Menu Properties**</span></span>|<xref:System.Windows.Controls.GridView.ColumnHeaderContextMenu%2A>|<span data-ttu-id="e2581-115">不適用</span><span class="sxs-lookup"><span data-stu-id="e2581-115">Not applicable</span></span>|<xref:System.Windows.FrameworkElement.ContextMenu%2A>|  
|<span data-ttu-id="e2581-116">**ToolTip**</span><span class="sxs-lookup"><span data-stu-id="e2581-116">**ToolTip**</span></span><br /><br /> <span data-ttu-id="e2581-117">**屬性**</span><span class="sxs-lookup"><span data-stu-id="e2581-117">**Properties**</span></span>|<xref:System.Windows.Controls.GridView.ColumnHeaderToolTip%2A>|<span data-ttu-id="e2581-118">不適用</span><span class="sxs-lookup"><span data-stu-id="e2581-118">Not applicable</span></span>|<xref:System.Windows.FrameworkElement.ToolTip%2A>|  
|<span data-ttu-id="e2581-119">**標頭範本**</span><span class="sxs-lookup"><span data-stu-id="e2581-119">**Header Template**</span></span><br /><br /> <span data-ttu-id="e2581-120">**屬性**</span><span class="sxs-lookup"><span data-stu-id="e2581-120">**Properties**</span></span>|<span data-ttu-id="e2581-121"><xref:System.Windows.Controls.GridView.ColumnHeaderTemplate%2A> <sup>1</sup>/</span><span class="sxs-lookup"><span data-stu-id="e2581-121"><xref:System.Windows.Controls.GridView.ColumnHeaderTemplate%2A> <sup>1</sup>/</span></span><br /><br /> <xref:System.Windows.Controls.GridView.ColumnHeaderTemplateSelector%2A>|<span data-ttu-id="e2581-122"><xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> <sup>1</sup>/</span><span class="sxs-lookup"><span data-stu-id="e2581-122"><xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> <sup>1</sup>/</span></span><br /><br /> <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>|<span data-ttu-id="e2581-123"><xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <sup>1</sup>/</span><span class="sxs-lookup"><span data-stu-id="e2581-123"><xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <sup>1</sup>/</span></span><br /><br /> <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>|  
|<span data-ttu-id="e2581-124">**樣式屬性**</span><span class="sxs-lookup"><span data-stu-id="e2581-124">**Style Properties**</span></span>|<xref:System.Windows.Controls.GridView.ColumnHeaderContainerStyle%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>|<xref:System.Windows.FrameworkElement.Style%2A>|  
  
 <span data-ttu-id="e2581-125"><sup>1</sup>如**標頭範本內容**，如果您設定範本及範本選擇器內容、 範本屬性會優先採用。</span><span class="sxs-lookup"><span data-stu-id="e2581-125"><sup>1</sup>For **Header Template Properties**, if you set both the template and template selector properties, the template property takes precedence.</span></span> <span data-ttu-id="e2581-126">例如，如果您同時設定<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>和<xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>屬性<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>屬性會優先。</span><span class="sxs-lookup"><span data-stu-id="e2581-126">For example, if you set both the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> and <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> properties, the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> property takes precedence.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2581-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="e2581-127">See Also</span></span>  
 [<span data-ttu-id="e2581-128">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="e2581-128">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="e2581-129">ListView 概觀</span><span class="sxs-lookup"><span data-stu-id="e2581-129">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="e2581-130">GridView 概觀</span><span class="sxs-lookup"><span data-stu-id="e2581-130">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
