---
title: "如何：使用 WebBrowser 控制項巡覽至 URL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
f1_keywords: WebBrowser.Navigate
helpviewer_keywords:
- WebBrowser control [Windows Forms], examples
- URLs [Windows Forms], navigating to
- WebBrowser control [Windows Forms], navigating to URLs
- examples [Windows Forms], WebBrowser control
ms.assetid: b3ec38cb-f509-4d0b-bd79-9f3611259c62
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a447d69eb6dafbff75ddd9d161abd4f78c607cdd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a><span data-ttu-id="7c959-102">如何：使用 WebBrowser 控制項巡覽至 URL</span><span class="sxs-lookup"><span data-stu-id="7c959-102">How to: Navigate to a URL with the WebBrowser Control</span></span>
<span data-ttu-id="7c959-103">下列程式碼範例將示範如何巡覽<xref:System.Windows.Forms.WebBrowser>至特定 URL 的控制項。</span><span class="sxs-lookup"><span data-stu-id="7c959-103">The following code example demonstrates how to navigate the <xref:System.Windows.Forms.WebBrowser> control to a specific URL.</span></span>  
  
 <span data-ttu-id="7c959-104">若要判斷完全載入新文件時，處理<xref:System.Windows.Forms.WebBrowser.DocumentCompleted>事件。</span><span class="sxs-lookup"><span data-stu-id="7c959-104">To determine when the new document is fully loaded, handle the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="7c959-105">如需示範此事件，請參閱[How to： 使用 WebBrowser 控制項列印](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)。</span><span class="sxs-lookup"><span data-stu-id="7c959-105">For a demonstration of this event, see [How to: Print with a WebBrowser Control](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c959-106">範例</span><span class="sxs-lookup"><span data-stu-id="7c959-106">Example</span></span>  
  
```vb  
Me.webBrowser1.Navigate("http://www.microsoft.com")  
```  
  
```csharp  
this.webBrowser1.Navigate("http://www.microsoft.com");  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7c959-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="7c959-107">Compiling the Code</span></span>  
 <span data-ttu-id="7c959-108">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="7c959-108">This example requires:</span></span>  
  
-   <span data-ttu-id="7c959-109">名為 `webBrowser1` 的 <xref:System.Windows.Forms.WebBrowser> 控制項。</span><span class="sxs-lookup"><span data-stu-id="7c959-109">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>  
  
-   <span data-ttu-id="7c959-110">`System` 和 `System.Windows.Forms` 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="7c959-110">References to the `System` and `System.Windows.Forms` assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c959-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="7c959-111">See Also</span></span>  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>  
 [<span data-ttu-id="7c959-112">WebBrowser 控制項</span><span class="sxs-lookup"><span data-stu-id="7c959-112">WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)  
 [<span data-ttu-id="7c959-113">操作說明：使用 WebBrowser 控制項列印</span><span class="sxs-lookup"><span data-stu-id="7c959-113">How to: Print with a WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)
