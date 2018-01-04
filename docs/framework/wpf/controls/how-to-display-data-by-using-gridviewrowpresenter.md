---
title: "如何：使用 GridViewRowPresenter 顯示資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- displaying data with GridViewRowPresenter [WPF]
- GridViewRowPresenter [WPF]
ms.assetid: bdb785a5-a262-44d5-a517-ea14383e5f70
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f540ad92c69219a2c22763403ce4ecc734c8e5cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-data-by-using-gridviewrowpresenter"></a><span data-ttu-id="700bc-102">如何：使用 GridViewRowPresenter 顯示資料</span><span class="sxs-lookup"><span data-stu-id="700bc-102">How to: Display Data by Using GridViewRowPresenter</span></span>
<span data-ttu-id="700bc-103">這個範例示範如何使用<xref:System.Windows.Controls.GridViewRowPresenter>和<xref:System.Windows.Controls.GridViewHeaderRowPresenter>來顯示資料行中資料的物件。</span><span class="sxs-lookup"><span data-stu-id="700bc-103">This example shows how to use the <xref:System.Windows.Controls.GridViewRowPresenter> and <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objects to display data in columns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="700bc-104">範例</span><span class="sxs-lookup"><span data-stu-id="700bc-104">Example</span></span>  
 <span data-ttu-id="700bc-105">下列範例示範如何指定<xref:System.Windows.Controls.GridViewColumnCollection>顯示<xref:System.DateTime.DayOfWeek%2A>和<xref:System.DateTime.Year%2A>的<xref:System.DateTime>物件使用<xref:System.Windows.Controls.GridViewRowPresenter>和<xref:System.Windows.Controls.GridViewHeaderRowPresenter>物件。</span><span class="sxs-lookup"><span data-stu-id="700bc-105">The following example shows how to specify a <xref:System.Windows.Controls.GridViewColumnCollection> that displays the <xref:System.DateTime.DayOfWeek%2A> and <xref:System.DateTime.Year%2A> of a <xref:System.DateTime> object by using <xref:System.Windows.Controls.GridViewRowPresenter> and <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objects.</span></span> <span data-ttu-id="700bc-106">此範例也會定義<xref:System.Windows.Style>如<xref:System.Windows.Controls.GridViewColumn.Header%2A>的<xref:System.Windows.Controls.GridViewColumn>。</span><span class="sxs-lookup"><span data-stu-id="700bc-106">The example also defines a <xref:System.Windows.Style> for the <xref:System.Windows.Controls.GridViewColumn.Header%2A> of a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[GridViewRowPresenterSample#GridViewRowPresenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewRowPresenterSample/CS/Window1.xaml#gridviewrowpresenter)]  
  
## <a name="see-also"></a><span data-ttu-id="700bc-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="700bc-107">See Also</span></span>  
 <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
 <xref:System.Windows.Controls.GridViewRowPresenter>  
 <xref:System.Windows.Controls.GridViewColumnCollection>  
 [<span data-ttu-id="700bc-108">GridView 概觀</span><span class="sxs-lookup"><span data-stu-id="700bc-108">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
