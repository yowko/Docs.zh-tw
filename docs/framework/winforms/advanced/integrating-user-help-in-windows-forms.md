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
ms.openlocfilehash: 207ceeafa2ea06340310577c636deb5ea1977aae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942918"
---
# <a name="integrating-user-help-in-windows-forms"></a><span data-ttu-id="257ce-102">整合 Windows Form 中的使用者說明</span><span class="sxs-lookup"><span data-stu-id="257ce-102">Integrating User Help in Windows Forms</span></span>
<span data-ttu-id="257ce-103">建置以 Windows 為基礎的應用程式的很重要，但通常會被忽略的層面是混淆的 [說明] 系統，而這是混淆的使用者有尋求協助的地方。</span><span class="sxs-lookup"><span data-stu-id="257ce-103">An essential, but often overlooked, aspect of building Windows-based applications is the Help system, as this is where users turn for assistance in times of confusion.</span></span> <span data-ttu-id="257ce-104">Windows Form 支援兩種不同的說明，每個由[HelpProvider 元件](../controls/helpprovider-component-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="257ce-104">Windows Forms support two different types of Help, each provided by the [HelpProvider Component](../controls/helpprovider-component-windows-forms.md).</span></span> <span data-ttu-id="257ce-105">第一種使用者指向 HTML 或 HTML 說明 1 的說明檔。*x*或更高的格式。</span><span class="sxs-lookup"><span data-stu-id="257ce-105">The first involves pointing the user to a Help file of either HTML or HTML Help 1.*x* or greater format.</span></span> <span data-ttu-id="257ce-106">第二個可顯示簡短"這是什麼 」-在個別控制項中，輸入說明這是對話方塊特別有用。</span><span class="sxs-lookup"><span data-stu-id="257ce-106">The second can display brief "What's This"-type Help on individual controls; this is especially useful on dialog boxes.</span></span> <span data-ttu-id="257ce-107">在相同表單上可用的說明這兩種類型。</span><span class="sxs-lookup"><span data-stu-id="257ce-107">Both types of Help can be used on the same form.</span></span>  
  
 <span data-ttu-id="257ce-108">此外， [ToolTip 元件](../controls/tooltip-component-windows-forms.md)可用來為 Windows Form 上的控制項提供個別的說明。</span><span class="sxs-lookup"><span data-stu-id="257ce-108">Additionally, the [ToolTip Component](../controls/tooltip-component-windows-forms.md) can be used to provide individual Help for controls on Windows Forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="257ce-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="257ce-109">In This Section</span></span>  
 [<span data-ttu-id="257ce-110">如何：在 Windows 應用程式中提供說明</span><span class="sxs-lookup"><span data-stu-id="257ce-110">How to: Provide Help in a Windows Application</span></span>](how-to-provide-help-in-a-windows-application.md)  
 <span data-ttu-id="257ce-111">說明如何使用`HelpProvider`將控制項連結至檔案，說明系統中的元件。</span><span class="sxs-lookup"><span data-stu-id="257ce-111">Explains how to use the `HelpProvider` component to link controls to files in a Help system.</span></span>  
  
 [<span data-ttu-id="257ce-112">如何：顯示快顯說明</span><span class="sxs-lookup"><span data-stu-id="257ce-112">How to: Display Pop-up Help</span></span>](how-to-display-pop-up-help.md)  
 <span data-ttu-id="257ce-113">說明如何使用`HelpProvider`元件，以在 Windows Form 上顯示快顯說明。</span><span class="sxs-lookup"><span data-stu-id="257ce-113">Explains how to use the `HelpProvider` component to show pop-up Help on Windows Forms.</span></span>  
  
 [<span data-ttu-id="257ce-114">使用工具提示來顯示控制項說明</span><span class="sxs-lookup"><span data-stu-id="257ce-114">Control Help Using ToolTips</span></span>](control-help-using-tooltips.md)  
 <span data-ttu-id="257ce-115">描述如何使用`ToolTip`元件，以顯示特定控制項的說明。</span><span class="sxs-lookup"><span data-stu-id="257ce-115">Describes using the `ToolTip` component to show control-specific Help.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="257ce-116">相關章節</span><span class="sxs-lookup"><span data-stu-id="257ce-116">Related Sections</span></span>  
 [<span data-ttu-id="257ce-117">HelpProvider 元件</span><span class="sxs-lookup"><span data-stu-id="257ce-117">HelpProvider Component</span></span>](../controls/helpprovider-component-windows-forms.md)  
 <span data-ttu-id="257ce-118">說明的基本概念`HelpProvider`元件。</span><span class="sxs-lookup"><span data-stu-id="257ce-118">Explains the basics of the `HelpProvider` component.</span></span>  
  
 [<span data-ttu-id="257ce-119">ToolTip 元件</span><span class="sxs-lookup"><span data-stu-id="257ce-119">ToolTip Component</span></span>](../controls/tooltip-component-windows-forms.md)  
 <span data-ttu-id="257ce-120">說明的基本概念`ToolTip`元件。</span><span class="sxs-lookup"><span data-stu-id="257ce-120">Explains the basics of the `ToolTip` component.</span></span>  
  
 [<span data-ttu-id="257ce-121">Windows Forms 概觀</span><span class="sxs-lookup"><span data-stu-id="257ce-121">Windows Forms Overview</span></span>](../windows-forms-overview.md)  
 <span data-ttu-id="257ce-122">說明 Windows Form 的基本概念。</span><span class="sxs-lookup"><span data-stu-id="257ce-122">Explains the basics of Windows Forms.</span></span>  
  
 [<span data-ttu-id="257ce-123">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="257ce-123">Windows Forms</span></span>](../index.md)  
 <span data-ttu-id="257ce-124">提供 Windows Form 的概觀。</span><span class="sxs-lookup"><span data-stu-id="257ce-124">Provides an overview of Windows Forms.</span></span>
