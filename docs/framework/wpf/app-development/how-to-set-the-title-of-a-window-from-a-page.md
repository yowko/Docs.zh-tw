---
title: 作法：從頁面設定視窗標題
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting title from a page
- title of window [WPF], setting from a page
- pages [WPF], setting window title from
ms.assetid: fecf0d19-3eb6-4f8c-a44f-ff1b6f2b34b3
ms.openlocfilehash: 0f618af89965822b0df96a264997dabd9cae7608
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940791"
---
# <a name="how-to-set-the-title-of-a-window-from-a-page"></a><span data-ttu-id="de733-102">作法：從頁面設定視窗標題</span><span class="sxs-lookup"><span data-stu-id="de733-102">How to: Set the Title of a Window from a Page</span></span>
<span data-ttu-id="de733-103">這個範例示範如何設定裝載之<xref:System.Windows.Controls.Page>視窗的標題。</span><span class="sxs-lookup"><span data-stu-id="de733-103">This example shows how to set the title of the window in which a <xref:System.Windows.Controls.Page> is hosted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de733-104">範例</span><span class="sxs-lookup"><span data-stu-id="de733-104">Example</span></span>  
 <span data-ttu-id="de733-105">頁面可以藉由設定<xref:System.Windows.Controls.Page.WindowTitle%2A>屬性來變更裝載它的視窗標題, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="de733-105">A page can change the title of the window that is hosting it by setting the <xref:System.Windows.Controls.Page.WindowTitle%2A> property, like so:</span></span>  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowTitleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowTitlePage.xaml#setpagewindowtitlexaml)]  
  
> [!NOTE]
> <span data-ttu-id="de733-106">設定頁面<xref:System.Windows.Controls.Page.Title%2A>的屬性並不會變更視窗標題的值。</span><span class="sxs-lookup"><span data-stu-id="de733-106">Setting the <xref:System.Windows.Controls.Page.Title%2A> property of a page does not change the value of the window title.</span></span> <span data-ttu-id="de733-107">相反地<xref:System.Windows.Controls.Page.Title%2A> , 會在導覽歷程記錄中指定頁面專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="de733-107">Instead, <xref:System.Windows.Controls.Page.Title%2A> specifies the name of a page entry in navigation history.</span></span>
