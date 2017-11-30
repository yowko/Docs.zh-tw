---
title: "如何： 設定視窗的標題，從頁面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- windows [WPF], setting title from a page
- title of window [WPF], setting from a page
- pages [WPF], setting window title from
ms.assetid: fecf0d19-3eb6-4f8c-a44f-ff1b6f2b34b3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 412771e3f43bc3755bdf9236743310ac8060165c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-set-the-title-of-a-window-from-a-page"></a><span data-ttu-id="b10e4-102">如何： 設定視窗的標題，從頁面</span><span class="sxs-lookup"><span data-stu-id="b10e4-102">How to: Set the Title of a Window from a Page</span></span>
<span data-ttu-id="b10e4-103">這個範例示範如何在其中設定視窗的標題<xref:System.Windows.Controls.Page>裝載。</span><span class="sxs-lookup"><span data-stu-id="b10e4-103">This example shows how to set the title of the window in which a <xref:System.Windows.Controls.Page> is hosted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b10e4-104">範例</span><span class="sxs-lookup"><span data-stu-id="b10e4-104">Example</span></span>  
 <span data-ttu-id="b10e4-105">頁面上可以變更會藉由設定其裝載視窗的標題<xref:System.Windows.Controls.Page.WindowTitle%2A>屬性，就像這樣：</span><span class="sxs-lookup"><span data-stu-id="b10e4-105">A page can change the title of the window that is hosting it by setting the <xref:System.Windows.Controls.Page.WindowTitle%2A> property, like so:</span></span>  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowTitleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowTitlePage.xaml#setpagewindowtitlexaml)]  
  
> [!NOTE]
>  <span data-ttu-id="b10e4-106">設定<xref:System.Windows.Controls.Page.Title%2A>屬性時，頁面不會變更視窗標題的值。</span><span class="sxs-lookup"><span data-stu-id="b10e4-106">Setting the <xref:System.Windows.Controls.Page.Title%2A> property of a page does not change the value of the window title.</span></span> <span data-ttu-id="b10e4-107">相反地，<xref:System.Windows.Controls.Page.Title%2A>巡覽記錄中指定頁面項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="b10e4-107">Instead, <xref:System.Windows.Controls.Page.Title%2A> specifies the name of a page entry in navigation history.</span></span>
