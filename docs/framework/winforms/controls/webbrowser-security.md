---
title: WebBrowser 安全性
ms.date: 03/30/2017
helpviewer_keywords:
- WebBrowser control [Windows Forms], security
- security [Windows Forms], WebBrowser control
ms.assetid: 0968846e-48ee-485a-9797-65b5b9a622f8
ms.openlocfilehash: 1e658c25ea19f966ac67402c6f3c7693c784d029
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214010"
---
# <a name="webbrowser-security"></a><span data-ttu-id="269ff-102">WebBrowser 安全性</span><span class="sxs-lookup"><span data-stu-id="269ff-102">WebBrowser Security</span></span>
<span data-ttu-id="269ff-103"><xref:System.Windows.Forms.WebBrowser>控制項用來在僅限完全信任中運作。</span><span class="sxs-lookup"><span data-stu-id="269ff-103">The <xref:System.Windows.Forms.WebBrowser> control is designed to work in full trust only.</span></span> <span data-ttu-id="269ff-104">控制項中顯示的 HTML 內容可以來自外部的 Web 伺服器，而且可能包含在指令碼或 Web 控制項的表單中的 unmanaged 程式碼。</span><span class="sxs-lookup"><span data-stu-id="269ff-104">The HTML content displayed in the control can come from external Web servers and may contain unmanaged code in the form of scripts or Web controls.</span></span> <span data-ttu-id="269ff-105">如果您使用<xref:System.Windows.Forms.WebBrowser>在此情況下，控制項的控制項是不較不安全，比光用到 Internet Explorer，但 managed<xref:System.Windows.Forms.WebBrowser>控制項不會防止執行這類未受管理的程式碼。</span><span class="sxs-lookup"><span data-stu-id="269ff-105">If you use the <xref:System.Windows.Forms.WebBrowser> control in this situation, the control is no less secure than Internet Explorer would be, but the managed <xref:System.Windows.Forms.WebBrowser> control does not prevent such unmanaged code from running.</span></span>  
  
 <span data-ttu-id="269ff-106">如需有關安全性問題與基礎 ActiveX`WebBrowser`控制項，請參閱[WebBrowser 控制項](https://go.microsoft.com/fwlink/?LinkId=198812)。</span><span class="sxs-lookup"><span data-stu-id="269ff-106">For more information about security issues relating to the underlying ActiveX `WebBrowser` control, see [WebBrowser Control](https://go.microsoft.com/fwlink/?LinkId=198812).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="269ff-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="269ff-107">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- [<span data-ttu-id="269ff-108">WebBrowser 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="269ff-108">WebBrowser Control Overview</span></span>](webbrowser-control-overview.md)
- [<span data-ttu-id="269ff-109">WebBrowser 控制項</span><span class="sxs-lookup"><span data-stu-id="269ff-109">WebBrowser Control</span></span>](https://go.microsoft.com/fwlink/?LinkId=198812)
