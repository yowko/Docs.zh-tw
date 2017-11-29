---
title: "NotifyIcon 元件概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: NotifyIcon
helpviewer_keywords:
- NotifyIcon component [Windows Forms], about NotifyIcon component
- system tray icons [Windows Forms], about system tray icons
- system tray icons [Windows Forms], using in Windows Forms
ms.assetid: 5b9189fa-d4ae-41a6-9b97-eb1f44bb1a69
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d951d45232437026cc41d8e40284207ea1c64ab9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="notifyicon-component-overview-windows-forms"></a><span data-ttu-id="303b5-102">NotifyIcon 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="303b5-102">NotifyIcon Component Overview (Windows Forms)</span></span>
<span data-ttu-id="303b5-103">Windows Form <xref:System.Windows.Forms.NotifyIcon> 元件大多時候通常會用來顯示在背景執行的處理序圖示，而不會顯示使用者介面。</span><span class="sxs-lookup"><span data-stu-id="303b5-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component is typically used to display icons for processes that run in the background and do not show a user interface much of the time.</span></span> <span data-ttu-id="303b5-104">防毒保護程式即為一例，您可以在工作列的狀態通知區域中，按一下圖示來存取這個程式。</span><span class="sxs-lookup"><span data-stu-id="303b5-104">An example would be a virus protection program that can be accessed by clicking an icon in the status notification area of the taskbar.</span></span>  
  
## <a name="key-properties-of-notifyicons"></a><span data-ttu-id="303b5-105">NotifyIcons 的主要屬性</span><span class="sxs-lookup"><span data-stu-id="303b5-105">Key Properties of NotifyIcons</span></span>  
 <span data-ttu-id="303b5-106">每個 <xref:System.Windows.Forms.NotifyIcon> 元件會在狀態區域中顯示一個圖示。</span><span class="sxs-lookup"><span data-stu-id="303b5-106">Each <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status area.</span></span> <span data-ttu-id="303b5-107">如果您有三個背景處理序，而且每個都需要顯示圖示，則您必須將三個 <xref:System.Windows.Forms.NotifyIcon> 元件加入表單。</span><span class="sxs-lookup"><span data-stu-id="303b5-107">If you have three background processes and wish to display an icon for each, you must add three <xref:System.Windows.Forms.NotifyIcon> components to the form.</span></span> <span data-ttu-id="303b5-108"><xref:System.Windows.Forms.NotifyIcon> 元件的主要屬性為 <xref:System.Windows.Forms.NotifyIcon.Icon%2A> 和 <xref:System.Windows.Forms.NotifyIcon.Visible%2A>。</span><span class="sxs-lookup"><span data-stu-id="303b5-108">The key properties of the <xref:System.Windows.Forms.NotifyIcon> component are <xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.</span></span> <span data-ttu-id="303b5-109"><xref:System.Windows.Forms.NotifyIcon.Icon%2A> 屬性會設定在狀態區域中顯示的圖示。</span><span class="sxs-lookup"><span data-stu-id="303b5-109">The <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property sets the icon that appears in the status area.</span></span> <span data-ttu-id="303b5-110">若要顯示圖示，<xref:System.Windows.Forms.NotifyIcon.Visible%2A> 屬性必須設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="303b5-110">In order for the icon to appear, the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property must be set to `true`.</span></span>  
  
 <span data-ttu-id="303b5-111">如果您使用 [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)]，則具有可搭配 <xref:System.Windows.Forms.NotifyIcon> 控制項使用之大型標準影像程式庫的存取權。</span><span class="sxs-lookup"><span data-stu-id="303b5-111">If you are using [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], you have access to a large library of standard images that you can use with the <xref:System.Windows.Forms.NotifyIcon> control.</span></span>  
  
## <a name="notifyicons-options"></a><span data-ttu-id="303b5-112">NotifyIcons 選項</span><span class="sxs-lookup"><span data-stu-id="303b5-112">NotifyIcons Options</span></span>  
 <span data-ttu-id="303b5-113">您可以將汽球提示、捷徑功能表和工具提示與 <xref:System.Windows.Forms.NotifyIcon> 產生關聯以協助使用者。</span><span class="sxs-lookup"><span data-stu-id="303b5-113">You can associate balloon tips, shortcut menus, and ToolTips with a <xref:System.Windows.Forms.NotifyIcon> to assist the user.</span></span>  
  
 <span data-ttu-id="303b5-114">您可以呼叫 <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> 方法來指定要顯示汽球提示的時間範圍，為 <xref:System.Windows.Forms.NotifyIcon> 顯示汽球提示。</span><span class="sxs-lookup"><span data-stu-id="303b5-114">You can display balloon tips for a <xref:System.Windows.Forms.NotifyIcon> by calling the <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> method specifying the time span you wish the balloon tip to display.</span></span> <span data-ttu-id="303b5-115">您也可以分別使用 <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>、<xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> 和 <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>，來指定汽球提示的文字、圖示和標題。</span><span class="sxs-lookup"><span data-stu-id="303b5-115">You can also specify the text, icon and title of the balloon tip with the <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> and <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>, respectively.</span></span> <span data-ttu-id="303b5-116"><xref:System.Windows.Forms.NotifyIcon> 元件也可以有關聯的工具提示和捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="303b5-116"><xref:System.Windows.Forms.NotifyIcon> components can also have associated ToolTips and shortcut menus.</span></span> <span data-ttu-id="303b5-117">如需詳細資訊，請參閱[ToolTip 元件概觀](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)和[ContextMenu 元件概觀](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="303b5-117">For more information, see [ToolTip Component Overview](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md) and [ContextMenu Component Overview](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="303b5-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="303b5-118">See Also</span></span>  
 <xref:System.Windows.Forms.NotifyIcon>  
 [<span data-ttu-id="303b5-119">NotifyIcon 元件</span><span class="sxs-lookup"><span data-stu-id="303b5-119">NotifyIcon Component</span></span>](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)
