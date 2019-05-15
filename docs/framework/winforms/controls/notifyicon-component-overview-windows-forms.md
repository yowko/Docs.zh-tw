---
title: NotifyIcon 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- NotifyIcon
helpviewer_keywords:
- NotifyIcon component [Windows Forms], about NotifyIcon component
- system tray icons [Windows Forms], about system tray icons
- system tray icons [Windows Forms], using in Windows Forms
ms.assetid: 5b9189fa-d4ae-41a6-9b97-eb1f44bb1a69
ms.openlocfilehash: def109799ddfb25b6f56a4f18d52bb19f62842f5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645714"
---
# <a name="notifyicon-component-overview-windows-forms"></a><span data-ttu-id="8a4ca-102">NotifyIcon 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="8a4ca-102">NotifyIcon Component Overview (Windows Forms)</span></span>

<span data-ttu-id="8a4ca-103">Windows Form <xref:System.Windows.Forms.NotifyIcon> 元件大多時候通常會用來顯示在背景執行的處理序圖示，而不會顯示使用者介面。</span><span class="sxs-lookup"><span data-stu-id="8a4ca-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component is typically used to display icons for processes that run in the background and do not show a user interface much of the time.</span></span> <span data-ttu-id="8a4ca-104">防毒保護程式即為一例，您可以在工作列的狀態通知區域中，按一下圖示來存取這個程式。</span><span class="sxs-lookup"><span data-stu-id="8a4ca-104">An example would be a virus protection program that can be accessed by clicking an icon in the status notification area of the taskbar.</span></span>

## <a name="key-properties-of-notifyicons"></a><span data-ttu-id="8a4ca-105">NotifyIcons 的主要屬性</span><span class="sxs-lookup"><span data-stu-id="8a4ca-105">Key Properties of NotifyIcons</span></span>

<span data-ttu-id="8a4ca-106">每個 <xref:System.Windows.Forms.NotifyIcon> 元件會在狀態區域中顯示一個圖示。</span><span class="sxs-lookup"><span data-stu-id="8a4ca-106">Each <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status area.</span></span> <span data-ttu-id="8a4ca-107">如果您有三個背景處理序，而且每個都需要顯示圖示，則您必須將三個 <xref:System.Windows.Forms.NotifyIcon> 元件加入表單。</span><span class="sxs-lookup"><span data-stu-id="8a4ca-107">If you have three background processes and wish to display an icon for each, you must add three <xref:System.Windows.Forms.NotifyIcon> components to the form.</span></span> <span data-ttu-id="8a4ca-108"><xref:System.Windows.Forms.NotifyIcon> 元件的主要屬性為 <xref:System.Windows.Forms.NotifyIcon.Icon%2A> 和 <xref:System.Windows.Forms.NotifyIcon.Visible%2A>。</span><span class="sxs-lookup"><span data-stu-id="8a4ca-108">The key properties of the <xref:System.Windows.Forms.NotifyIcon> component are <xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.</span></span> <span data-ttu-id="8a4ca-109"><xref:System.Windows.Forms.NotifyIcon.Icon%2A> 屬性會設定在狀態區域中顯示的圖示。</span><span class="sxs-lookup"><span data-stu-id="8a4ca-109">The <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property sets the icon that appears in the status area.</span></span> <span data-ttu-id="8a4ca-110">若要顯示圖示，<xref:System.Windows.Forms.NotifyIcon.Visible%2A> 屬性必須設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="8a4ca-110">In order for the icon to appear, the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property must be set to `true`.</span></span>

## <a name="notifyicons-options"></a><span data-ttu-id="8a4ca-111">NotifyIcons 選項</span><span class="sxs-lookup"><span data-stu-id="8a4ca-111">NotifyIcons Options</span></span>

<span data-ttu-id="8a4ca-112">您可以將汽球提示、捷徑功能表和工具提示與 <xref:System.Windows.Forms.NotifyIcon> 產生關聯以協助使用者。</span><span class="sxs-lookup"><span data-stu-id="8a4ca-112">You can associate balloon tips, shortcut menus, and ToolTips with a <xref:System.Windows.Forms.NotifyIcon> to assist the user.</span></span>

<span data-ttu-id="8a4ca-113">您可以呼叫 <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> 方法來指定要顯示汽球提示的時間範圍，為 <xref:System.Windows.Forms.NotifyIcon> 顯示汽球提示。</span><span class="sxs-lookup"><span data-stu-id="8a4ca-113">You can display balloon tips for a <xref:System.Windows.Forms.NotifyIcon> by calling the <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> method specifying the time span you wish the balloon tip to display.</span></span> <span data-ttu-id="8a4ca-114">您也可以分別使用 <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>、<xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> 和 <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>，來指定汽球提示的文字、圖示和標題。</span><span class="sxs-lookup"><span data-stu-id="8a4ca-114">You can also specify the text, icon and title of the balloon tip with the <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> and <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>, respectively.</span></span> <span data-ttu-id="8a4ca-115"><xref:System.Windows.Forms.NotifyIcon> 元件也可以有關聯的工具提示和捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="8a4ca-115"><xref:System.Windows.Forms.NotifyIcon> components can also have associated ToolTips and shortcut menus.</span></span> <span data-ttu-id="8a4ca-116">如需詳細資訊，請參閱 < [ToolTip 元件概觀](tooltip-component-overview-windows-forms.md)並[ContextMenu 元件概觀](contextmenu-component-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="8a4ca-116">For more information, see [ToolTip Component Overview](tooltip-component-overview-windows-forms.md) and [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8a4ca-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a4ca-117">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- [<span data-ttu-id="8a4ca-118">NotifyIcon 元件</span><span class="sxs-lookup"><span data-stu-id="8a4ca-118">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
