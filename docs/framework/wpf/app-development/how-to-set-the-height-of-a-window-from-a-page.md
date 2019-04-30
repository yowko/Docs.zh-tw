---
title: HOW TO：從頁面設定視窗高度
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting height from a page
- pages [WPF], setting window height from
- height of window [WPF], setting from a page
ms.assetid: 4e4488ff-ab5c-4ee9-81a4-e1addb55c5cc
ms.openlocfilehash: c99ea134478635f368b71443f43e4d8f772cb5aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007297"
---
# <a name="how-to-set-the-height-of-a-window-from-a-page"></a><span data-ttu-id="b4546-102">HOW TO：從頁面設定視窗高度</span><span class="sxs-lookup"><span data-stu-id="b4546-102">How to: Set the Height of a Window from a Page</span></span>
<span data-ttu-id="b4546-103">此範例說明如何設定從視窗的高度<xref:System.Windows.Controls.Page>。</span><span class="sxs-lookup"><span data-stu-id="b4546-103">This example illustrates how to set the height of the window from a <xref:System.Windows.Controls.Page>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4546-104">範例</span><span class="sxs-lookup"><span data-stu-id="b4546-104">Example</span></span>  
 <span data-ttu-id="b4546-105">A<xref:System.Windows.Controls.Page>可以設定其裝載視窗的高度，藉由設定<xref:System.Windows.Controls.Page.WindowHeight%2A>。</span><span class="sxs-lookup"><span data-stu-id="b4546-105">A <xref:System.Windows.Controls.Page> can set the height of its host window by setting <xref:System.Windows.Controls.Page.WindowHeight%2A>.</span></span> <span data-ttu-id="b4546-106">這個屬性可讓<xref:System.Windows.Controls.Page>沒有明確的認知的裝載它的視窗類型。</span><span class="sxs-lookup"><span data-stu-id="b4546-106">This property allows the <xref:System.Windows.Controls.Page> to not have explicit knowledge of the type of window that hosts it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4546-107">若要設定的視窗中，使用高度<xref:System.Windows.Controls.Page.WindowHeight%2A>、<xref:System.Windows.Controls.Page>必須是視窗的子系。</span><span class="sxs-lookup"><span data-stu-id="b4546-107">To set the height of a window using <xref:System.Windows.Controls.Page.WindowHeight%2A>, a <xref:System.Windows.Controls.Page> must be the child of a window.</span></span>  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowHeightXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowHeightPage.xaml#setpagewindowheightxaml)]
