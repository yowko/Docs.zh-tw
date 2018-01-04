---
title: "Windows Forms 應用程式中的說明系統"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help [Windows Forms], adding to Windows applications
- Windows applications [Windows Forms], providing Help systems
- What's This? Help
- Help [Windows Forms], Windows Forms
- HelpProvider component [Windows Forms], providing Help in Windows applications
ms.assetid: 2a96a278-432c-41fc-9e3c-5bfedf5e1267
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1b2f5d067d487bbd5b91576927aee21a9a44fde0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="help-systems-in-windows-forms-applications"></a><span data-ttu-id="27bc2-102">Windows Forms 應用程式中的說明系統</span><span class="sxs-lookup"><span data-stu-id="27bc2-102">Help Systems in Windows Forms Applications</span></span>
<span data-ttu-id="27bc2-103">其中一個最重要的優待的就如的應用程式，開發人員可以提供您的使用者，是一流的說明系統。</span><span class="sxs-lookup"><span data-stu-id="27bc2-103">One of the most important courtesies you, as a developer of applications, can furnish your users with is a competent Help system.</span></span> <span data-ttu-id="27bc2-104">這是他們將會開啟時產生混淆或求助對象。</span><span class="sxs-lookup"><span data-stu-id="27bc2-104">This is where they will turn when they become confused or disoriented.</span></span> <span data-ttu-id="27bc2-105">提供說明系統的 Windows 型應用程式中輕鬆方式是使用[HelpProvider 元件](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="27bc2-105">Providing a Help system in a Windows-based application is easily done by using the [HelpProvider Component](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md).</span></span>  
  
## <a name="different-types-of-help"></a><span data-ttu-id="27bc2-106">不同類型的說明</span><span class="sxs-lookup"><span data-stu-id="27bc2-106">Different Types of Help</span></span>  
 <span data-ttu-id="27bc2-107">Windows Form <xref:System.Windows.Forms.HelpProvider> 元件用來將 HTML 說明 1.x 說明檔 (以 HTML Help Workshop 產生的 .chm 檔案，或 .htm 檔) 與 Windows 架構應用程式產生關聯。</span><span class="sxs-lookup"><span data-stu-id="27bc2-107">The Windows Forms <xref:System.Windows.Forms.HelpProvider> component is used to associate an HTML Help 1.x Help file (either a .chm file, produced with the HTML Help Workshop, or an .htm file) with your Windows-based application.</span></span> <span data-ttu-id="27bc2-108"><xref:System.Windows.Forms.HelpProvider>元件可以用來為 Windows Form 上的控制項或特定的控制項提供即時線上說明。</span><span class="sxs-lookup"><span data-stu-id="27bc2-108">The <xref:System.Windows.Forms.HelpProvider> component can be used to provide context-sensitive Help for controls on Windows Forms or specific controls.</span></span> <span data-ttu-id="27bc2-109">此外，<xref:System.Windows.Forms.HelpProvider>元件可以開啟特定區域，例如目錄、 索引或搜尋函式的資料表的主頁面的說明檔。</span><span class="sxs-lookup"><span data-stu-id="27bc2-109">Additionally, the <xref:System.Windows.Forms.HelpProvider> component can open a Help file to specific areas, such as the main page of a table of contents, an index, or a search function.</span></span> <span data-ttu-id="27bc2-110">如需一般資訊<xref:System.Windows.Forms.HelpProvider>元件，請參閱[HelpProvider 元件概觀](../../../../docs/framework/winforms/controls/helpprovider-component-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="27bc2-110">For general information about the <xref:System.Windows.Forms.HelpProvider> component, see [HelpProvider Component Overview](../../../../docs/framework/winforms/controls/helpprovider-component-overview-windows-forms.md).</span></span> <span data-ttu-id="27bc2-111">如需有關如何使用資訊<xref:System.Windows.Forms.HelpProvider>元件在 Windows Form 上顯示快顯說明請參閱[如何： 顯示快顯說明](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)。</span><span class="sxs-lookup"><span data-stu-id="27bc2-111">For information on how to use the <xref:System.Windows.Forms.HelpProvider> component to show pop-up Help on Windows Forms, see [How to: Display Pop-up Help](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md).</span></span> <span data-ttu-id="27bc2-112">如需使用<xref:System.Windows.Forms.ToolTip>元件來顯示控制項特定的說明，請參閱[控制項協助使用工具提示](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)。</span><span class="sxs-lookup"><span data-stu-id="27bc2-112">For information on using the <xref:System.Windows.Forms.ToolTip> component to show control-specific Help, see [Control Help Using ToolTips](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md).</span></span>  
  
 <span data-ttu-id="27bc2-113">您可以產生以 HTML Help Workshop HTML 說明 1.x 檔。</span><span class="sxs-lookup"><span data-stu-id="27bc2-113">You can generate HTML Help 1.x files with the HTML Help Workshop.</span></span> <span data-ttu-id="27bc2-114">如需有關 HTML 說明的詳細資訊，請參閱 「 HTML Help Workshop"或 MSDN 中的其他 「 HTML 說明 」 主題。</span><span class="sxs-lookup"><span data-stu-id="27bc2-114">For more information on HTML Help, see the "HTML Help Workshop" or the other "HTML Help" topics in MSDN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27bc2-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="27bc2-115">See Also</span></span>  
 [<span data-ttu-id="27bc2-116">整合 Windows Forms 中的使用者說明</span><span class="sxs-lookup"><span data-stu-id="27bc2-116">Integrating User Help in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [<span data-ttu-id="27bc2-117">HelpProvider 元件</span><span class="sxs-lookup"><span data-stu-id="27bc2-117">HelpProvider Component</span></span>](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md)  
 [<span data-ttu-id="27bc2-118">ToolTip 元件</span><span class="sxs-lookup"><span data-stu-id="27bc2-118">ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)  
 [<span data-ttu-id="27bc2-119">Windows Forms 概觀</span><span class="sxs-lookup"><span data-stu-id="27bc2-119">Windows Forms Overview</span></span>](../../../../docs/framework/winforms/windows-forms-overview.md)  
 [<span data-ttu-id="27bc2-120">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="27bc2-120">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)
