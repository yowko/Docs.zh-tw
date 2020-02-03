---
title: 整合使用者協助
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], Windows Forms (using designer)
- Windows Forms, Help (using designer)
- HTML Help [Windows Forms], Windows Forms (using designer)
- Help [Windows Forms], Windows applications (using designer)
- forms. Help (using designer)
- Windows applications [Windows Forms], Help (using designer)
ms.assetid: a8563d25-8a75-4bc7-a024-f1870591b50f
ms.openlocfilehash: c402615d68c75327613d21bd35f1587b10f1dbf3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731573"
---
# <a name="integrating-user-help-in-windows-forms"></a><span data-ttu-id="ef8d4-102">整合 Windows Form 中的使用者說明</span><span class="sxs-lookup"><span data-stu-id="ef8d4-102">Integrating User Help in Windows Forms</span></span>
<span data-ttu-id="ef8d4-103">建立以 Windows 為基礎之應用程式的重要但經常被忽略的層面是說明系統，因為這是使用者在混淆時提供協助的地方。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-103">An essential, but often overlooked, aspect of building Windows-based applications is the Help system, as this is where users turn for assistance in times of confusion.</span></span> <span data-ttu-id="ef8d4-104">Windows Forms 支援兩種不同類型的說明，分別由[HelpProvider 元件](../controls/helpprovider-component-windows-forms.md)提供。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-104">Windows Forms support two different types of Help, each provided by the [HelpProvider Component](../controls/helpprovider-component-windows-forms.md).</span></span> <span data-ttu-id="ef8d4-105">第一種方式是將使用者指向 HTML 或 HTML Help 1 的說明檔。*x*或更大的格式。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-105">The first involves pointing the user to a Help file of either HTML or HTML Help 1.*x* or greater format.</span></span> <span data-ttu-id="ef8d4-106">第二個可以在個別控制項上顯示簡短的「這是什麼」類型的說明;這在對話方塊中特別有用。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-106">The second can display brief "What's This"-type Help on individual controls; this is especially useful on dialog boxes.</span></span> <span data-ttu-id="ef8d4-107">這兩種類型的說明都可以在相同的表單上使用。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-107">Both types of Help can be used on the same form.</span></span>  
  
 <span data-ttu-id="ef8d4-108">此外，[工具提示元件](../controls/tooltip-component-windows-forms.md)可以用來為 Windows Forms 上的控制項提供個別的協助。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-108">Additionally, the [ToolTip Component](../controls/tooltip-component-windows-forms.md) can be used to provide individual Help for controls on Windows Forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ef8d4-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="ef8d4-109">In This Section</span></span>  
 [<span data-ttu-id="ef8d4-110">操作說明：在 Windows 應用程式中提供說明</span><span class="sxs-lookup"><span data-stu-id="ef8d4-110">How to: Provide Help in a Windows Application</span></span>](how-to-provide-help-in-a-windows-application.md)  
 <span data-ttu-id="ef8d4-111">說明如何使用 `HelpProvider` 元件，將控制項連結至說明系統中的檔案。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-111">Explains how to use the `HelpProvider` component to link controls to files in a Help system.</span></span>  
  
 [<span data-ttu-id="ef8d4-112">操作說明：顯示快顯說明</span><span class="sxs-lookup"><span data-stu-id="ef8d4-112">How to: Display Pop-up Help</span></span>](how-to-display-pop-up-help.md)  
 <span data-ttu-id="ef8d4-113">說明如何使用 `HelpProvider` 元件，在 Windows Forms 上顯示快顯說明。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-113">Explains how to use the `HelpProvider` component to show pop-up Help on Windows Forms.</span></span>  
  
 [<span data-ttu-id="ef8d4-114">使用工具提示來顯示控制項說明</span><span class="sxs-lookup"><span data-stu-id="ef8d4-114">Control Help Using ToolTips</span></span>](control-help-using-tooltips.md)  
 <span data-ttu-id="ef8d4-115">描述如何使用 `ToolTip` 元件來顯示控制項特定的協助。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-115">Describes using the `ToolTip` component to show control-specific Help.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ef8d4-116">相關章節</span><span class="sxs-lookup"><span data-stu-id="ef8d4-116">Related Sections</span></span>  
 [<span data-ttu-id="ef8d4-117">HelpProvider 元件</span><span class="sxs-lookup"><span data-stu-id="ef8d4-117">HelpProvider Component</span></span>](../controls/helpprovider-component-windows-forms.md)  
 <span data-ttu-id="ef8d4-118">說明 `HelpProvider` 元件的基本概念。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-118">Explains the basics of the `HelpProvider` component.</span></span>  
  
 [<span data-ttu-id="ef8d4-119">ToolTip 元件</span><span class="sxs-lookup"><span data-stu-id="ef8d4-119">ToolTip Component</span></span>](../controls/tooltip-component-windows-forms.md)  
 <span data-ttu-id="ef8d4-120">說明 `ToolTip` 元件的基本概念。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-120">Explains the basics of the `ToolTip` component.</span></span>  
  
 [<span data-ttu-id="ef8d4-121">Windows Forms 概觀</span><span class="sxs-lookup"><span data-stu-id="ef8d4-121">Windows Forms Overview</span></span>](../windows-forms-overview.md)  
 <span data-ttu-id="ef8d4-122">說明 Windows Forms 的基本概念。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-122">Explains the basics of Windows Forms.</span></span>  
  
 <span data-ttu-id="ef8d4-123">[Windows Forms](../index.md) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="ef8d4-123">[Windows Forms](../index.md)</span></span>  
 <span data-ttu-id="ef8d4-124">提供 Windows Forms 的總覽。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-124">Provides an overview of Windows Forms.</span></span>
