---
title: 如何：使用 WebBrowser 控制項巡覽至 URL
description: 瞭解如何使用 Windows Forms WebBrowser. 導覽控制項來流覽至特定的 URL。 同時瞭解如何判斷新檔的載入時間。
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
ms.openlocfilehash: e6ad360cc73a84ca040869832bb59d354cb78bd5
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325574"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a><span data-ttu-id="576d5-104">如何：使用 WebBrowser 控制項巡覽至 URL</span><span class="sxs-lookup"><span data-stu-id="576d5-104">How to: Navigate to a URL with the WebBrowser Control</span></span>
<span data-ttu-id="576d5-105">下列程式碼範例示範如何將控制項導覽 <xref:System.Windows.Forms.WebBrowser> 至特定的 URL。</span><span class="sxs-lookup"><span data-stu-id="576d5-105">The following code example demonstrates how to navigate the <xref:System.Windows.Forms.WebBrowser> control to a specific URL.</span></span>

 <span data-ttu-id="576d5-106">若要判斷新檔的完整載入時間，請處理 <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> 事件。</span><span class="sxs-lookup"><span data-stu-id="576d5-106">To determine when the new document is fully loaded, handle the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="576d5-107">如需此事件的示範，請參閱[如何：使用 WebBrowser 控制項進行列印](how-to-print-with-a-webbrowser-control.md)。</span><span class="sxs-lookup"><span data-stu-id="576d5-107">For a demonstration of this event, see [How to: Print with a WebBrowser Control](how-to-print-with-a-webbrowser-control.md).</span></span>

## <a name="example"></a><span data-ttu-id="576d5-108">範例</span><span class="sxs-lookup"><span data-stu-id="576d5-108">Example</span></span>

```vb
Me.webBrowser1.Navigate("https://www.microsoft.com")
```

```csharp
this.webBrowser1.Navigate("https://www.microsoft.com");
```

## <a name="compiling-the-code"></a><span data-ttu-id="576d5-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="576d5-109">Compiling the Code</span></span>
 <span data-ttu-id="576d5-110">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="576d5-110">This example requires:</span></span>

- <span data-ttu-id="576d5-111">名為 `webBrowser1` 的 <xref:System.Windows.Forms.WebBrowser> 控制項。</span><span class="sxs-lookup"><span data-stu-id="576d5-111">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>

- <span data-ttu-id="576d5-112">`System` 和 `System.Windows.Forms` 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="576d5-112">References to the `System` and `System.Windows.Forms` assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="576d5-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="576d5-113">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [<span data-ttu-id="576d5-114">WebBrowser 控制項</span><span class="sxs-lookup"><span data-stu-id="576d5-114">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
- [<span data-ttu-id="576d5-115">操作說明：使用 WebBrowser 控制項列印</span><span class="sxs-lookup"><span data-stu-id="576d5-115">How to: Print with a WebBrowser Control</span></span>](how-to-print-with-a-webbrowser-control.md)
