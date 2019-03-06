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
# <a name="how-to-display-data-by-using-gridviewrowpresenter"></a>HOW TO：使用 GridViewRowPresenter 顯示資料
此範例示範如何使用<xref:System.Windows.Controls.GridViewRowPresenter>和<xref:System.Windows.Controls.GridViewHeaderRowPresenter>來顯示資料行中資料的物件。  
  
## <a name="example"></a>範例  
 下列範例示範如何指定<xref:System.Windows.Controls.GridViewColumnCollection>會顯示<xref:System.DateTime.DayOfWeek%2A>並<xref:System.DateTime.Year%2A>的<xref:System.DateTime>使用的物件<xref:System.Windows.Controls.GridViewRowPresenter>和<xref:System.Windows.Controls.GridViewHeaderRowPresenter>物件。 此範例也會定義<xref:System.Windows.Style>for<xref:System.Windows.Controls.GridViewColumn.Header%2A>的<xref:System.Windows.Controls.GridViewColumn>。  
  
 [!code-xaml[GridViewRowPresenterSample#GridViewRowPresenter](~/samples/snippets/csharp/VS_Snippets_Wpf/GridViewRowPresenterSample/CS/Window1.xaml#gridviewrowpresenter)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
- <xref:System.Windows.Controls.GridViewRowPresenter>
- <xref:System.Windows.Controls.GridViewColumnCollection>
- [GridView 概觀](gridview-overview.md)
