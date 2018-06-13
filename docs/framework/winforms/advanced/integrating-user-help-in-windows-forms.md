---
title: 整合 Windows Form 中的使用者說明
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], Windows Forms (using designer)
- Windows Forms, Help (using designer)
- HTML Help [Windows Forms], Windows Forms (using designer)
- Help [Windows Forms], Windows applications (using designer)
- forms. Help (using designer)
- Windows applications [Windows Forms], Help (using designer)
ms.assetid: a8563d25-8a75-4bc7-a024-f1870591b50f
ms.openlocfilehash: b16ba14eea68083cd7bdfc91c88375406137f450
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527219"
---
# <a name="integrating-user-help-in-windows-forms"></a><span data-ttu-id="e43a9-102">整合 Windows Form 中的使用者說明</span><span class="sxs-lookup"><span data-stu-id="e43a9-102">Integrating User Help in Windows Forms</span></span>
<span data-ttu-id="e43a9-103">建立 Windows 架構應用程式的很重要，但通常會被忽略的層面是混淆的，說明系統，而這是混淆的使用者有尋求協助的地方。</span><span class="sxs-lookup"><span data-stu-id="e43a9-103">An essential, but often overlooked, aspect of building Windows-based applications is the Help system, as this is where users turn for assistance in times of confusion.</span></span> <span data-ttu-id="e43a9-104">Windows Form 支援兩種不同類型的說明，提供的每一個由[HelpProvider 元件](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="e43a9-104">Windows Forms support two different types of Help, each provided by the [HelpProvider Component](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md).</span></span> <span data-ttu-id="e43a9-105">第一個牽涉到使用者指向 HTML 或 HTML 說明 1 的說明檔。*x*或更高的格式。</span><span class="sxs-lookup"><span data-stu-id="e43a9-105">The first involves pointing the user to a Help file of either HTML or HTML Help 1.*x* or greater format.</span></span> <span data-ttu-id="e43a9-106">第二個可以顯示簡短的 「 什麼 」 這層上個別控制項中，輸入說明這是對話方塊中特別有用。</span><span class="sxs-lookup"><span data-stu-id="e43a9-106">The second can display brief "What's This"-type Help on individual controls; this is especially useful on dialog boxes.</span></span> <span data-ttu-id="e43a9-107">這兩種類型的說明可以使用相同表單上。</span><span class="sxs-lookup"><span data-stu-id="e43a9-107">Both types of Help can be used on the same form.</span></span>  
  
 <span data-ttu-id="e43a9-108">此外， [ToolTip 元件](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)可用來提供 Windows Form 上控制項的個別說明。</span><span class="sxs-lookup"><span data-stu-id="e43a9-108">Additionally, the [ToolTip Component](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md) can be used to provide individual Help for controls on Windows Forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e43a9-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="e43a9-109">In This Section</span></span>  
 [<span data-ttu-id="e43a9-110">操作說明：在 Windows 應用程式中提供說明</span><span class="sxs-lookup"><span data-stu-id="e43a9-110">How to: Provide Help in a Windows Application</span></span>](../../../../docs/framework/winforms/advanced/how-to-provide-help-in-a-windows-application.md)  
 <span data-ttu-id="e43a9-111">說明如何使用`HelpProvider`控制項連結至檔案，說明系統中的元件。</span><span class="sxs-lookup"><span data-stu-id="e43a9-111">Explains how to use the `HelpProvider` component to link controls to files in a Help system.</span></span>  
  
 [<span data-ttu-id="e43a9-112">操作說明：顯示快顯說明</span><span class="sxs-lookup"><span data-stu-id="e43a9-112">How to: Display Pop-up Help</span></span>](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)  
 <span data-ttu-id="e43a9-113">說明如何使用`HelpProvider`元件在 Windows Form 上顯示快顯的說明。</span><span class="sxs-lookup"><span data-stu-id="e43a9-113">Explains how to use the `HelpProvider` component to show pop-up Help on Windows Forms.</span></span>  
  
 [<span data-ttu-id="e43a9-114">使用工具提示來顯示控制項說明</span><span class="sxs-lookup"><span data-stu-id="e43a9-114">Control Help Using ToolTips</span></span>](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 <span data-ttu-id="e43a9-115">描述如何使用`ToolTip`顯示控制項的特定說明的元件。</span><span class="sxs-lookup"><span data-stu-id="e43a9-115">Describes using the `ToolTip` component to show control-specific Help.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e43a9-116">相關章節</span><span class="sxs-lookup"><span data-stu-id="e43a9-116">Related Sections</span></span>  
 [<span data-ttu-id="e43a9-117">HelpProvider 元件</span><span class="sxs-lookup"><span data-stu-id="e43a9-117">HelpProvider Component</span></span>](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md)  
 <span data-ttu-id="e43a9-118">說明的基本概念`HelpProvider`元件。</span><span class="sxs-lookup"><span data-stu-id="e43a9-118">Explains the basics of the `HelpProvider` component.</span></span>  
  
 [<span data-ttu-id="e43a9-119">ToolTip 元件</span><span class="sxs-lookup"><span data-stu-id="e43a9-119">ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)  
 <span data-ttu-id="e43a9-120">說明的基本概念`ToolTip`元件。</span><span class="sxs-lookup"><span data-stu-id="e43a9-120">Explains the basics of the `ToolTip` component.</span></span>  
  
 [<span data-ttu-id="e43a9-121">Windows Forms 概觀</span><span class="sxs-lookup"><span data-stu-id="e43a9-121">Windows Forms Overview</span></span>](../../../../docs/framework/winforms/windows-forms-overview.md)  
 <span data-ttu-id="e43a9-122">說明 Windows Form 的基本概念。</span><span class="sxs-lookup"><span data-stu-id="e43a9-122">Explains the basics of Windows Forms.</span></span>  
  
 [<span data-ttu-id="e43a9-123">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e43a9-123">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)  
 <span data-ttu-id="e43a9-124">提供 Windows Form 的概觀。</span><span class="sxs-lookup"><span data-stu-id="e43a9-124">Provides an overview of Windows Forms.</span></span>
