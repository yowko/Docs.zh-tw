---
title: 如何： 設定頁面的視窗的寬度
ms.date: 03/30/2017
helpviewer_keywords:
- width of windows [WPF], setting from a page
- windows [WPF], setting width from a page
- pages [WPF], setting window width from
ms.assetid: 31601c92-7889-472a-b07e-bf675ad21c92
ms.openlocfilehash: a0ae0e136e0b7f1cd2a2ec56455e14723e8fa306
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545986"
---
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a><span data-ttu-id="b5f49-102">如何： 設定頁面的視窗的寬度</span><span class="sxs-lookup"><span data-stu-id="b5f49-102">How to: Set the Width of a Window from a Page</span></span>
<span data-ttu-id="b5f49-103">此範例說明如何設定從視窗的寬度<xref:System.Windows.Controls.Page>。</span><span class="sxs-lookup"><span data-stu-id="b5f49-103">This example illustrates how to set the width of the window from a <xref:System.Windows.Controls.Page>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5f49-104">範例</span><span class="sxs-lookup"><span data-stu-id="b5f49-104">Example</span></span>  
 <span data-ttu-id="b5f49-105">A<xref:System.Windows.Controls.Page>設定即可設定其裝載視窗的寬度<xref:System.Windows.Controls.Page.WindowWidth%2A>。</span><span class="sxs-lookup"><span data-stu-id="b5f49-105">A <xref:System.Windows.Controls.Page> can set the width of its host window by setting <xref:System.Windows.Controls.Page.WindowWidth%2A>.</span></span> <span data-ttu-id="b5f49-106">這個屬性允許<xref:System.Windows.Controls.Page>沒有明確的認知的視窗針對裝載它的類型。</span><span class="sxs-lookup"><span data-stu-id="b5f49-106">This property allows the <xref:System.Windows.Controls.Page> to not have explicit knowledge of the type of window that hosts it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5f49-107">若要設定的視窗，使用寬度<xref:System.Windows.Controls.Page.WindowWidth%2A>、<xref:System.Windows.Controls.Page>必須是視窗的子系。</span><span class="sxs-lookup"><span data-stu-id="b5f49-107">To set the width of a window using <xref:System.Windows.Controls.Page.WindowWidth%2A>, a <xref:System.Windows.Controls.Page> must be the child of a window.</span></span>  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
