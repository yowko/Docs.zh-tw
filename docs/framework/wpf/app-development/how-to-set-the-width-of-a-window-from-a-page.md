---
title: 作法：從頁面設定視窗寬度
ms.date: 03/30/2017
helpviewer_keywords:
- width of windows [WPF], setting from a page
- windows [WPF], setting width from a page
- pages [WPF], setting window width from
ms.assetid: 31601c92-7889-472a-b07e-bf675ad21c92
ms.openlocfilehash: 1e16b75ecb85550facdf24a5b9e341cf0c061178
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940768"
---
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a><span data-ttu-id="adbc0-102">HOW TO：從頁面設定視窗寬度</span><span class="sxs-lookup"><span data-stu-id="adbc0-102">How to: Set the Width of a Window from a Page</span></span>
<span data-ttu-id="adbc0-103">這個範例說明如何從<xref:System.Windows.Controls.Page>設定視窗的寬度。</span><span class="sxs-lookup"><span data-stu-id="adbc0-103">This example illustrates how to set the width of the window from a <xref:System.Windows.Controls.Page>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="adbc0-104">範例</span><span class="sxs-lookup"><span data-stu-id="adbc0-104">Example</span></span>  
 <span data-ttu-id="adbc0-105">可以藉由設定<xref:System.Windows.Controls.Page.WindowWidth%2A>來設定其主視窗的寬度。 <xref:System.Windows.Controls.Page></span><span class="sxs-lookup"><span data-stu-id="adbc0-105">A <xref:System.Windows.Controls.Page> can set the width of its host window by setting <xref:System.Windows.Controls.Page.WindowWidth%2A>.</span></span> <span data-ttu-id="adbc0-106">這個屬性可讓<xref:System.Windows.Controls.Page>不明確瞭解主控它的視窗類型。</span><span class="sxs-lookup"><span data-stu-id="adbc0-106">This property allows the <xref:System.Windows.Controls.Page> to not have explicit knowledge of the type of window that hosts it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="adbc0-107">若要使用<xref:System.Windows.Controls.Page.WindowWidth%2A>設定視窗的寬度<xref:System.Windows.Controls.Page> , 必須是視窗的子系。</span><span class="sxs-lookup"><span data-stu-id="adbc0-107">To set the width of a window using <xref:System.Windows.Controls.Page.WindowWidth%2A>, a <xref:System.Windows.Controls.Page> must be the child of a window.</span></span>  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
