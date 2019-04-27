---
title: HOW TO：使用 WebBrowser 控制項巡覽至 URL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- WebBrowser.Navigate
helpviewer_keywords:
- WebBrowser control [Windows Forms], examples
- URLs [Windows Forms], navigating to
- WebBrowser control [Windows Forms], navigating to URLs
- examples [Windows Forms], WebBrowser control
ms.assetid: b3ec38cb-f509-4d0b-bd79-9f3611259c62
ms.openlocfilehash: a174b6ae60f87e91e6f97e8fa7f8ad3892ef017a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913467"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a><span data-ttu-id="e93a6-102">HOW TO：使用 WebBrowser 控制項巡覽至 URL</span><span class="sxs-lookup"><span data-stu-id="e93a6-102">How to: Navigate to a URL with the WebBrowser Control</span></span>
<span data-ttu-id="e93a6-103">下列程式碼範例示範如何瀏覽<xref:System.Windows.Forms.WebBrowser>至特定 URL 的控制項。</span><span class="sxs-lookup"><span data-stu-id="e93a6-103">The following code example demonstrates how to navigate the <xref:System.Windows.Forms.WebBrowser> control to a specific URL.</span></span>  
  
 <span data-ttu-id="e93a6-104">若要判斷新的文件是完全載入時，處理<xref:System.Windows.Forms.WebBrowser.DocumentCompleted>事件。</span><span class="sxs-lookup"><span data-stu-id="e93a6-104">To determine when the new document is fully loaded, handle the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="e93a6-105">如需示範此事件，請參閱[How to:使用 WebBrowser 控制項列印](how-to-print-with-a-webbrowser-control.md)。</span><span class="sxs-lookup"><span data-stu-id="e93a6-105">For a demonstration of this event, see [How to: Print with a WebBrowser Control](how-to-print-with-a-webbrowser-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e93a6-106">範例</span><span class="sxs-lookup"><span data-stu-id="e93a6-106">Example</span></span>  
  
```vb  
Me.webBrowser1.Navigate("http://www.microsoft.com")  
```  
  
```csharp  
this.webBrowser1.Navigate("http://www.microsoft.com");  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e93a6-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="e93a6-107">Compiling the Code</span></span>  
 <span data-ttu-id="e93a6-108">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="e93a6-108">This example requires:</span></span>  
  
-   <span data-ttu-id="e93a6-109">名為 `webBrowser1` 的 <xref:System.Windows.Forms.WebBrowser> 控制項。</span><span class="sxs-lookup"><span data-stu-id="e93a6-109">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>  
  
-   <span data-ttu-id="e93a6-110">`System` 和 `System.Windows.Forms` 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="e93a6-110">References to the `System` and `System.Windows.Forms` assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e93a6-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e93a6-111">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [<span data-ttu-id="e93a6-112">WebBrowser 控制項</span><span class="sxs-lookup"><span data-stu-id="e93a6-112">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
- [<span data-ttu-id="e93a6-113">如何：使用 WebBrowser 控制項列印</span><span class="sxs-lookup"><span data-stu-id="e93a6-113">How to: Print with a WebBrowser Control</span></span>](how-to-print-with-a-webbrowser-control.md)
