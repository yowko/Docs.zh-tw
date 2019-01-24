---
title: WebBrowser 安全性
ms.date: 03/30/2017
helpviewer_keywords:
- WebBrowser control [Windows Forms], security
- security [Windows Forms], WebBrowser control
ms.assetid: 0968846e-48ee-485a-9797-65b5b9a622f8
ms.openlocfilehash: 4c69f1c39d3a22db361fef1ffb65f21aa9d75128
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54736269"
---
# <a name="webbrowser-security"></a><span data-ttu-id="1e511-102">WebBrowser 安全性</span><span class="sxs-lookup"><span data-stu-id="1e511-102">WebBrowser Security</span></span>
<span data-ttu-id="1e511-103"><xref:System.Windows.Forms.WebBrowser>控制項用來在僅限完全信任中運作。</span><span class="sxs-lookup"><span data-stu-id="1e511-103">The <xref:System.Windows.Forms.WebBrowser> control is designed to work in full trust only.</span></span> <span data-ttu-id="1e511-104">控制項中顯示的 HTML 內容可以來自外部的 Web 伺服器，而且可能包含在指令碼或 Web 控制項的表單中的 unmanaged 程式碼。</span><span class="sxs-lookup"><span data-stu-id="1e511-104">The HTML content displayed in the control can come from external Web servers and may contain unmanaged code in the form of scripts or Web controls.</span></span> <span data-ttu-id="1e511-105">如果您使用<xref:System.Windows.Forms.WebBrowser>在此情況下，控制項的控制項是不較不安全，比光用到 Internet Explorer，但 managed<xref:System.Windows.Forms.WebBrowser>控制項不會防止執行這類未受管理的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1e511-105">If you use the <xref:System.Windows.Forms.WebBrowser> control in this situation, the control is no less secure than Internet Explorer would be, but the managed <xref:System.Windows.Forms.WebBrowser> control does not prevent such unmanaged code from running.</span></span>  
  
 <span data-ttu-id="1e511-106">如需有關安全性問題與基礎 ActiveX`WebBrowser`控制項，請參閱[WebBrowser 控制項](https://go.microsoft.com/fwlink/?LinkId=198812)。</span><span class="sxs-lookup"><span data-stu-id="1e511-106">For more information about security issues relating to the underlying ActiveX `WebBrowser` control, see [WebBrowser Control](https://go.microsoft.com/fwlink/?LinkId=198812).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e511-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e511-107">See also</span></span>
- <xref:System.Windows.Forms.WebBrowser>
- [<span data-ttu-id="1e511-108">WebBrowser 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="1e511-108">WebBrowser Control Overview</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)
- [<span data-ttu-id="1e511-109">WebBrowser 控制項</span><span class="sxs-lookup"><span data-stu-id="1e511-109">WebBrowser Control</span></span>](https://go.microsoft.com/fwlink/?LinkId=198812)
