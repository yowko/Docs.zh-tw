---
title: WebBrowser 安全性
ms.date: 03/30/2017
helpviewer_keywords:
- WebBrowser control [Windows Forms], security
- security [Windows Forms], WebBrowser control
ms.assetid: 0968846e-48ee-485a-9797-65b5b9a622f8
ms.openlocfilehash: b25cabca050d06dbfe97c563eb56622d1f21be54
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095251"
---
# <a name="webbrowser-security"></a><span data-ttu-id="d43b5-102">WebBrowser 安全性</span><span class="sxs-lookup"><span data-stu-id="d43b5-102">WebBrowser Security</span></span>
<span data-ttu-id="d43b5-103"><xref:System.Windows.Forms.WebBrowser> 控制項的設計目的是要在完全信任的情況中工作。</span><span class="sxs-lookup"><span data-stu-id="d43b5-103">The <xref:System.Windows.Forms.WebBrowser> control is designed to work in full trust only.</span></span> <span data-ttu-id="d43b5-104">控制項中顯示的 HTML 內容可以來自外部 Web 服務器，而且可能包含以腳本或 Web 控制項形式呈現的非受控碼。</span><span class="sxs-lookup"><span data-stu-id="d43b5-104">The HTML content displayed in the control can come from external Web servers and may contain unmanaged code in the form of scripts or Web controls.</span></span> <span data-ttu-id="d43b5-105">如果您在這種情況下使用 <xref:System.Windows.Forms.WebBrowser> 控制項，控制項的安全性就不如 Internet Explorer，但 managed <xref:System.Windows.Forms.WebBrowser> 控制項不會阻止這類的非受控碼執行。</span><span class="sxs-lookup"><span data-stu-id="d43b5-105">If you use the <xref:System.Windows.Forms.WebBrowser> control in this situation, the control is no less secure than Internet Explorer would be, but the managed <xref:System.Windows.Forms.WebBrowser> control does not prevent such unmanaged code from running.</span></span>  
  
 <span data-ttu-id="d43b5-106">如需有關與基礎 ActiveX `WebBrowser` 控制項相關之安全性問題的詳細資訊，請參閱[WebBrowser 控制項](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="d43b5-106">For more information about security issues relating to the underlying ActiveX `WebBrowser` control, see [WebBrowser Control](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d43b5-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d43b5-107">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- [<span data-ttu-id="d43b5-108">WebBrowser 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="d43b5-108">WebBrowser Control Overview</span></span>](webbrowser-control-overview.md)
- <span data-ttu-id="d43b5-109">[WebBrowser 控制項](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="d43b5-109">[WebBrowser Control](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85))</span></span>
