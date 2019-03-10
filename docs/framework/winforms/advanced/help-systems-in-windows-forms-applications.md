---
title: Windows Form 應用程式中的說明系統
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], adding to Windows applications
- Windows applications [Windows Forms], providing Help systems
- What's This? Help
- Help [Windows Forms], Windows Forms
- HelpProvider component [Windows Forms], providing Help in Windows applications
ms.assetid: 2a96a278-432c-41fc-9e3c-5bfedf5e1267
ms.openlocfilehash: 22c07490d0d3b54be96f32d67c9b4aee70306c1d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718307"
---
# <a name="help-systems-in-windows-forms-applications"></a><span data-ttu-id="c9ffe-102">Windows Form 應用程式中的說明系統</span><span class="sxs-lookup"><span data-stu-id="c9ffe-102">Help Systems in Windows Forms Applications</span></span>
<span data-ttu-id="c9ffe-103">其中一個最重要的優待的您的應用程式，開發人員可以提供您的使用者是裁判的 [說明] 系統。</span><span class="sxs-lookup"><span data-stu-id="c9ffe-103">One of the most important courtesies you, as a developer of applications, can furnish your users with is a competent Help system.</span></span> <span data-ttu-id="c9ffe-104">這是他們將會在其中開啟時使用者感到混淆、 求助對象。</span><span class="sxs-lookup"><span data-stu-id="c9ffe-104">This is where they will turn when they become confused or disoriented.</span></span> <span data-ttu-id="c9ffe-105">提供以 Windows 為基礎的應用程式中的 [說明] 系統很容易，利用[HelpProvider 元件](../controls/helpprovider-component-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="c9ffe-105">Providing a Help system in a Windows-based application is easily done by using the [HelpProvider Component](../controls/helpprovider-component-windows-forms.md).</span></span>  
  
## <a name="different-types-of-help"></a><span data-ttu-id="c9ffe-106">不同類型的說明</span><span class="sxs-lookup"><span data-stu-id="c9ffe-106">Different Types of Help</span></span>  
 <span data-ttu-id="c9ffe-107">Windows Form <xref:System.Windows.Forms.HelpProvider> 元件用來將 HTML 說明 1.x 說明檔 (以 HTML Help Workshop 產生的 .chm 檔案，或 .htm 檔) 與 Windows 架構應用程式產生關聯。</span><span class="sxs-lookup"><span data-stu-id="c9ffe-107">The Windows Forms <xref:System.Windows.Forms.HelpProvider> component is used to associate an HTML Help 1.x Help file (either a .chm file, produced with the HTML Help Workshop, or an .htm file) with your Windows-based application.</span></span> <span data-ttu-id="c9ffe-108"><xref:System.Windows.Forms.HelpProvider>元件可用來提供即時線上說明 Windows Forms 上的控制項或特定的控制項。</span><span class="sxs-lookup"><span data-stu-id="c9ffe-108">The <xref:System.Windows.Forms.HelpProvider> component can be used to provide context-sensitive Help for controls on Windows Forms or specific controls.</span></span> <span data-ttu-id="c9ffe-109">此外，<xref:System.Windows.Forms.HelpProvider>元件可以開啟至特定的區域，例如內容、 索引或搜尋函式的資料表的主頁面的說明檔。</span><span class="sxs-lookup"><span data-stu-id="c9ffe-109">Additionally, the <xref:System.Windows.Forms.HelpProvider> component can open a Help file to specific areas, such as the main page of a table of contents, an index, or a search function.</span></span> <span data-ttu-id="c9ffe-110">如需一般資訊<xref:System.Windows.Forms.HelpProvider>元件，請參閱 < [HelpProvider 元件概觀](../controls/helpprovider-component-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="c9ffe-110">For general information about the <xref:System.Windows.Forms.HelpProvider> component, see [HelpProvider Component Overview](../controls/helpprovider-component-overview-windows-forms.md).</span></span> <span data-ttu-id="c9ffe-111">如需有關如何使用資訊<xref:System.Windows.Forms.HelpProvider>元件，以在 Windows Form 上顯示快顯說明請參閱[How to:顯示快顯說明](how-to-display-pop-up-help.md)。</span><span class="sxs-lookup"><span data-stu-id="c9ffe-111">For information on how to use the <xref:System.Windows.Forms.HelpProvider> component to show pop-up Help on Windows Forms, see [How to: Display Pop-up Help](how-to-display-pop-up-help.md).</span></span> <span data-ttu-id="c9ffe-112">如需使用<xref:System.Windows.Forms.ToolTip>元件，以顯示特定控制項的說明，請參閱[控制項協助使用工具提示](control-help-using-tooltips.md)。</span><span class="sxs-lookup"><span data-stu-id="c9ffe-112">For information on using the <xref:System.Windows.Forms.ToolTip> component to show control-specific Help, see [Control Help Using ToolTips](control-help-using-tooltips.md).</span></span>  
  
 <span data-ttu-id="c9ffe-113">您可以產生 HTML Help Workshop HTML 說明 1.x 檔案。</span><span class="sxs-lookup"><span data-stu-id="c9ffe-113">You can generate HTML Help 1.x files with the HTML Help Workshop.</span></span> <span data-ttu-id="c9ffe-114">如需有關 HTML 說明檔的詳細資訊，請參閱 「 HTML Help Workshop 」 或在 MSDN 中的其他 [HTML 說明] 主題。</span><span class="sxs-lookup"><span data-stu-id="c9ffe-114">For more information on HTML Help, see the "HTML Help Workshop" or the other "HTML Help" topics in MSDN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9ffe-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9ffe-115">See also</span></span>
- [<span data-ttu-id="c9ffe-116">整合 Windows Forms 中的使用者說明</span><span class="sxs-lookup"><span data-stu-id="c9ffe-116">Integrating User Help in Windows Forms</span></span>](integrating-user-help-in-windows-forms.md)
- [<span data-ttu-id="c9ffe-117">HelpProvider 元件</span><span class="sxs-lookup"><span data-stu-id="c9ffe-117">HelpProvider Component</span></span>](../controls/helpprovider-component-windows-forms.md)
- [<span data-ttu-id="c9ffe-118">ToolTip 元件</span><span class="sxs-lookup"><span data-stu-id="c9ffe-118">ToolTip Component</span></span>](../controls/tooltip-component-windows-forms.md)
- [<span data-ttu-id="c9ffe-119">Windows Forms 概觀</span><span class="sxs-lookup"><span data-stu-id="c9ffe-119">Windows Forms Overview</span></span>](../windows-forms-overview.md)
- [<span data-ttu-id="c9ffe-120">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c9ffe-120">Windows Forms</span></span>](../index.md)
