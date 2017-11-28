---
title: "HelpProvider 元件概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: HelpProvider
helpviewer_keywords:
- HelpProvider component [Windows Forms], about HelpProvider component
- Help [Windows Forms], adding to Windows applications
- F1 Help [Windows Forms], adding to Windows Forms
- dialog boxes [Windows Forms], context-sensitive Help
- Windows Forms, context-sensitive Help
ms.assetid: 6b10c2cc-c577-4cb5-9669-e37b33416af9
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 42a788e44fde80662748e19a7244ce77bb26118f
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="helpprovider-component-overview-windows-forms"></a><span data-ttu-id="fa179-102">HelpProvider 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="fa179-102">HelpProvider Component Overview (Windows Forms)</span></span>
<span data-ttu-id="fa179-103">Windows Form [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md)元件可用來將 HTML 說明 1.x 說明檔 （以 HTML Help Workshop 產生的.chm 檔案或.htm 檔） 與 Windows 應用程式產生關聯。</span><span class="sxs-lookup"><span data-stu-id="fa179-103">The Windows Forms [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) component is used to associate an HTML Help 1.x Help file (either a .chm file, produced with the HTML Help Workshop, or an .htm file) with your Windows application.</span></span> <span data-ttu-id="fa179-104">您可以提供各種不同的方式說明：</span><span class="sxs-lookup"><span data-stu-id="fa179-104">You can provide help in a variety of ways:</span></span>  
  
-   <span data-ttu-id="fa179-105">提供 Windows Form 上控制項的即時線上說明。</span><span class="sxs-lookup"><span data-stu-id="fa179-105">Provide context-sensitive Help for controls on Windows Forms.</span></span>  
  
-   <span data-ttu-id="fa179-106">提供特定的對話方塊或在對話方塊中的特定控制項上的即時線上說明。</span><span class="sxs-lookup"><span data-stu-id="fa179-106">Provide context-sensitive Help on a particular dialog box or specific controls on a dialog box.</span></span>  
  
-   <span data-ttu-id="fa179-107">開啟說明檔案以特定區域，例如目錄、 索引或搜尋函式的主頁面。</span><span class="sxs-lookup"><span data-stu-id="fa179-107">Open a Help file to specific areas, such as the main page of a Table of Contents, the Index, or a search function.</span></span>  
  
## <a name="using-the-help-provider"></a><span data-ttu-id="fa179-108">使用說明提供者</span><span class="sxs-lookup"><span data-stu-id="fa179-108">Using the Help Provider</span></span>  
 <span data-ttu-id="fa179-109">加入<xref:System.Windows.Forms.HelpProvider>加入 Windows Form 的元件可讓要公開 （expose） 的說明內容的表單上的其他控制項<xref:System.Windows.Forms.HelpProvider>元件。</span><span class="sxs-lookup"><span data-stu-id="fa179-109">Adding a <xref:System.Windows.Forms.HelpProvider> component to your Windows Form allows the other controls on the form to expose the Help properties of the <xref:System.Windows.Forms.HelpProvider> component.</span></span> <span data-ttu-id="fa179-110">這可讓您提供關於 Windows Form 上控制項的說明。</span><span class="sxs-lookup"><span data-stu-id="fa179-110">This enables you to provide help for the controls on your Windows Form.</span></span> <span data-ttu-id="fa179-111">您可以建立關聯的說明檔案<xref:System.Windows.Forms.HelpProvider>元件使用<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="fa179-111">You can associate a Help file with the <xref:System.Windows.Forms.HelpProvider> component using the <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property.</span></span> <span data-ttu-id="fa179-112">您指定的呼叫所提供的說明類型<xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A>並提供的值從<xref:System.Windows.Forms.HelpNavigator>列舉指定之控制項。</span><span class="sxs-lookup"><span data-stu-id="fa179-112">You specify the type of Help provided by calling <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> and providing a value from the <xref:System.Windows.Forms.HelpNavigator> enumeration for the specified control.</span></span> <span data-ttu-id="fa179-113">您提供的關鍵字或主題的說明藉由呼叫<xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="fa179-113">You provide the keyword or topic for Help by calling the <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> method.</span></span>  
  
 <span data-ttu-id="fa179-114">（選擇性） 若要將特定的 [說明] 字串與另一個控制項產生關聯，請使用<xref:System.Windows.Forms.HelpProvider.SetHelpString%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="fa179-114">Optionally, to associate a specific Help string with another control, use the <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> method.</span></span> <span data-ttu-id="fa179-115">當使用者按下 F1 鍵，且焦點在控制項時，您會使用這個方法的控制項關聯的字串會顯示快顯視窗中。</span><span class="sxs-lookup"><span data-stu-id="fa179-115">The string that you associate with a control using this method is displayed in a pop-up window when the user presses the F1 key while the control has focus.</span></span>  
  
 <span data-ttu-id="fa179-116">如果<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>是否尚未設定，您必須使用<xref:System.Windows.Forms.HelpProvider.SetHelpString%2A>提供說明文字。</span><span class="sxs-lookup"><span data-stu-id="fa179-116">If <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> has not been set, you must use <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> to provide the Help text.</span></span> <span data-ttu-id="fa179-117">如果您同時設定<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>的說明字串，說明根據<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>更高的優先順序。</span><span class="sxs-lookup"><span data-stu-id="fa179-117">If you have set both <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> and the Help string, Help based on <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> will take precedence.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fa179-118">您可能會遇到問題使用相對路徑時指定的說明檔的路徑中<xref:System.Windows.Forms.Help.ShowHelp%2A>方法或<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>屬性<xref:System.Windows.Forms.HelpProvider>控制項。</span><span class="sxs-lookup"><span data-stu-id="fa179-118">You may encounter problems using the relative path when specifiying the path to the Help file in the <xref:System.Windows.Forms.Help.ShowHelp%2A> method or <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property of the <xref:System.Windows.Forms.HelpProvider> control.</span></span> <span data-ttu-id="fa179-119">在這種情況，請務必使用指定的說明檔的絕對檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="fa179-119">As such, be sure to use the absolute file path to specify the Help file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa179-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa179-120">See Also</span></span>  
 [<span data-ttu-id="fa179-121">Windows Forms 應用程式中的說明系統</span><span class="sxs-lookup"><span data-stu-id="fa179-121">Help Systems in Windows Forms Applications</span></span>](../../../../docs/framework/winforms/advanced/help-systems-in-windows-forms-applications.md)
