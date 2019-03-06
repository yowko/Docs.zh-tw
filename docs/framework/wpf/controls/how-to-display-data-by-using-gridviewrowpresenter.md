---
title: HOW TO：使用 GridViewRowPresenter 顯示資料
ms.date: 03/30/2017
helpviewer_keywords:
- displaying data with GridViewRowPresenter [WPF]
- GridViewRowPresenter [WPF]
ms.assetid: bdb785a5-a262-44d5-a517-ea14383e5f70
ms.openlocfilehash: f05e1bd67d37d21a010562c7be5db5ca594f36db
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369574"
---
# <a name="how-to-display-data-by-using-gridviewrowpresenter"></a><span data-ttu-id="8ec35-102">HOW TO：使用 GridViewRowPresenter 顯示資料</span><span class="sxs-lookup"><span data-stu-id="8ec35-102">How to: Display Data by Using GridViewRowPresenter</span></span>
<span data-ttu-id="8ec35-103">此範例示範如何使用<xref:System.Windows.Controls.GridViewRowPresenter>和<xref:System.Windows.Controls.GridViewHeaderRowPresenter>來顯示資料行中資料的物件。</span><span class="sxs-lookup"><span data-stu-id="8ec35-103">This example shows how to use the <xref:System.Windows.Controls.GridViewRowPresenter> and <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objects to display data in columns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ec35-104">範例</span><span class="sxs-lookup"><span data-stu-id="8ec35-104">Example</span></span>  
 <span data-ttu-id="8ec35-105">下列範例示範如何指定<xref:System.Windows.Controls.GridViewColumnCollection>會顯示<xref:System.DateTime.DayOfWeek%2A>並<xref:System.DateTime.Year%2A>的<xref:System.DateTime>使用的物件<xref:System.Windows.Controls.GridViewRowPresenter>和<xref:System.Windows.Controls.GridViewHeaderRowPresenter>物件。</span><span class="sxs-lookup"><span data-stu-id="8ec35-105">The following example shows how to specify a <xref:System.Windows.Controls.GridViewColumnCollection> that displays the <xref:System.DateTime.DayOfWeek%2A> and <xref:System.DateTime.Year%2A> of a <xref:System.DateTime> object by using <xref:System.Windows.Controls.GridViewRowPresenter> and <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objects.</span></span> <span data-ttu-id="8ec35-106">此範例也會定義<xref:System.Windows.Style>for<xref:System.Windows.Controls.GridViewColumn.Header%2A>的<xref:System.Windows.Controls.GridViewColumn>。</span><span class="sxs-lookup"><span data-stu-id="8ec35-106">The example also defines a <xref:System.Windows.Style> for the <xref:System.Windows.Controls.GridViewColumn.Header%2A> of a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[GridViewRowPresenterSample#GridViewRowPresenter](~/samples/snippets/csharp/VS_Snippets_Wpf/GridViewRowPresenterSample/CS/Window1.xaml#gridviewrowpresenter)]  
  
## <a name="see-also"></a><span data-ttu-id="8ec35-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ec35-107">See also</span></span>
- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
- <xref:System.Windows.Controls.GridViewRowPresenter>
- <xref:System.Windows.Controls.GridViewColumnCollection>
- [<span data-ttu-id="8ec35-108">GridView 概觀</span><span class="sxs-lookup"><span data-stu-id="8ec35-108">GridView Overview</span></span>](gridview-overview.md)
