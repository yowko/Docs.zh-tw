---
title: 說明系統
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], adding to Windows applications
- Windows applications [Windows Forms], providing Help systems
- What's This? Help
- Help [Windows Forms], Windows Forms
- HelpProvider component [Windows Forms], providing Help in Windows applications
ms.assetid: 2a96a278-432c-41fc-9e3c-5bfedf5e1267
ms.openlocfilehash: c97a22dbdbdcc0eb282b52e16c4ef40914b1d9e7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742242"
---
# <a name="help-systems-in-windows-forms-applications"></a><span data-ttu-id="84e22-102">Windows Form 應用程式中的說明系統</span><span class="sxs-lookup"><span data-stu-id="84e22-102">Help Systems in Windows Forms Applications</span></span>
<span data-ttu-id="84e22-103">身為應用程式開發人員的其中一項最重要的禮物，可以為您的使用者提供有能力的協助系統。</span><span class="sxs-lookup"><span data-stu-id="84e22-103">One of the most important courtesies you, as a developer of applications, can furnish your users with is a competent Help system.</span></span> <span data-ttu-id="84e22-104">這是他們在混淆或 disoriented 時將會變成的地方。</span><span class="sxs-lookup"><span data-stu-id="84e22-104">This is where they will turn when they become confused or disoriented.</span></span> <span data-ttu-id="84e22-105">使用[HelpProvider 元件](../controls/helpprovider-component-windows-forms.md)可輕鬆地在 Windows 應用程式中提供說明系統。</span><span class="sxs-lookup"><span data-stu-id="84e22-105">Providing a Help system in a Windows-based application is easily done by using the [HelpProvider Component](../controls/helpprovider-component-windows-forms.md).</span></span>  
  
## <a name="different-types-of-help"></a><span data-ttu-id="84e22-106">不同類型的說明</span><span class="sxs-lookup"><span data-stu-id="84e22-106">Different Types of Help</span></span>  
 <span data-ttu-id="84e22-107">Windows Form <xref:System.Windows.Forms.HelpProvider> 元件用來將 HTML 說明 1.x 說明檔 (以 HTML Help Workshop 產生的 .chm 檔案，或 .htm 檔) 與 Windows 架構應用程式產生關聯。</span><span class="sxs-lookup"><span data-stu-id="84e22-107">The Windows Forms <xref:System.Windows.Forms.HelpProvider> component is used to associate an HTML Help 1.x Help file (either a .chm file, produced with the HTML Help Workshop, or an .htm file) with your Windows-based application.</span></span> <span data-ttu-id="84e22-108"><xref:System.Windows.Forms.HelpProvider> 元件可以用來提供 Windows Forms 或特定控制項上控制項的即時線上說明。</span><span class="sxs-lookup"><span data-stu-id="84e22-108">The <xref:System.Windows.Forms.HelpProvider> component can be used to provide context-sensitive Help for controls on Windows Forms or specific controls.</span></span> <span data-ttu-id="84e22-109">此外，<xref:System.Windows.Forms.HelpProvider> 元件可以開啟說明檔到特定區域，例如目錄的主頁面、索引或搜尋函數。</span><span class="sxs-lookup"><span data-stu-id="84e22-109">Additionally, the <xref:System.Windows.Forms.HelpProvider> component can open a Help file to specific areas, such as the main page of a table of contents, an index, or a search function.</span></span> <span data-ttu-id="84e22-110">如需 <xref:System.Windows.Forms.HelpProvider> 元件的一般資訊，請參閱[HelpProvider 元件總覽](../controls/helpprovider-component-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="84e22-110">For general information about the <xref:System.Windows.Forms.HelpProvider> component, see [HelpProvider Component Overview](../controls/helpprovider-component-overview-windows-forms.md).</span></span> <span data-ttu-id="84e22-111">如需如何使用 <xref:System.Windows.Forms.HelpProvider> 元件在 Windows Forms 上顯示快顯說明的詳細資訊，請參閱[如何：顯示](how-to-display-pop-up-help.md)快顯說明。</span><span class="sxs-lookup"><span data-stu-id="84e22-111">For information on how to use the <xref:System.Windows.Forms.HelpProvider> component to show pop-up Help on Windows Forms, see [How to: Display Pop-up Help](how-to-display-pop-up-help.md).</span></span> <span data-ttu-id="84e22-112">如需使用 <xref:System.Windows.Forms.ToolTip> 元件來顯示控制項特定協助的詳細資訊，請參閱[使用工具提示控制](control-help-using-tooltips.md)說明。</span><span class="sxs-lookup"><span data-stu-id="84e22-112">For information on using the <xref:System.Windows.Forms.ToolTip> component to show control-specific Help, see [Control Help Using ToolTips](control-help-using-tooltips.md).</span></span>  
  
 <span data-ttu-id="84e22-113">您可以使用 HTML Help 研討會產生 HTML Help 1.x 檔案。</span><span class="sxs-lookup"><span data-stu-id="84e22-113">You can generate HTML Help 1.x files with the HTML Help Workshop.</span></span> <span data-ttu-id="84e22-114">如需 HTML 說明的詳細資訊，請參閱 MSDN 中的「HTML 協助研討會」或其他「HTML 說明」主題。</span><span class="sxs-lookup"><span data-stu-id="84e22-114">For more information on HTML Help, see the "HTML Help Workshop" or the other "HTML Help" topics in MSDN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84e22-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84e22-115">See also</span></span>

- [<span data-ttu-id="84e22-116">整合 Windows Forms 中的使用者說明</span><span class="sxs-lookup"><span data-stu-id="84e22-116">Integrating User Help in Windows Forms</span></span>](integrating-user-help-in-windows-forms.md)
- [<span data-ttu-id="84e22-117">HelpProvider 元件</span><span class="sxs-lookup"><span data-stu-id="84e22-117">HelpProvider Component</span></span>](../controls/helpprovider-component-windows-forms.md)
- [<span data-ttu-id="84e22-118">ToolTip 元件</span><span class="sxs-lookup"><span data-stu-id="84e22-118">ToolTip Component</span></span>](../controls/tooltip-component-windows-forms.md)
- [<span data-ttu-id="84e22-119">Windows Forms 概觀</span><span class="sxs-lookup"><span data-stu-id="84e22-119">Windows Forms Overview</span></span>](../windows-forms-overview.md)
- <span data-ttu-id="84e22-120">[Windows Forms](../index.md) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="84e22-120">[Windows Forms](../index.md)</span></span>
