---
title: HelpProvider 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- HelpProvider
helpviewer_keywords:
- HelpProvider component [Windows Forms], about HelpProvider component
- Help [Windows Forms], adding to Windows applications
- F1 Help [Windows Forms], adding to Windows Forms
- dialog boxes [Windows Forms], context-sensitive Help
- Windows Forms, context-sensitive Help
ms.assetid: 6b10c2cc-c577-4cb5-9669-e37b33416af9
ms.openlocfilehash: 5fc447e00ca46f251a895f0de82118a11310a8d9
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972647"
---
# <a name="helpprovider-component-overview-windows-forms"></a><span data-ttu-id="17f38-102">HelpProvider 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="17f38-102">HelpProvider Component Overview (Windows Forms)</span></span>
<span data-ttu-id="17f38-103">Windows Forms [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md)元件可用來將 HTML 說明 1.x 說明檔 （.chm 檔案，以 HTML Help Workshop 產生或.htm 檔） 與 Windows 應用程式產生關聯。</span><span class="sxs-lookup"><span data-stu-id="17f38-103">The Windows Forms [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) component is used to associate an HTML Help 1.x Help file (either a .chm file, produced with the HTML Help Workshop, or an .htm file) with your Windows application.</span></span> <span data-ttu-id="17f38-104">您可以提供說明各種不同的方式：</span><span class="sxs-lookup"><span data-stu-id="17f38-104">You can provide help in a variety of ways:</span></span>  
  
-   <span data-ttu-id="17f38-105">Windows Form 上的控制項提供即時線上說明。</span><span class="sxs-lookup"><span data-stu-id="17f38-105">Provide context-sensitive Help for controls on Windows Forms.</span></span>  
  
-   <span data-ttu-id="17f38-106">提供特定的對話方塊中或在對話方塊中的特定控制項上的即時線上說明。</span><span class="sxs-lookup"><span data-stu-id="17f38-106">Provide context-sensitive Help on a particular dialog box or specific controls on a dialog box.</span></span>  
  
-   <span data-ttu-id="17f38-107">開啟至特定的區域，例如目錄、 索引或搜尋函式的主頁面的說明檔。</span><span class="sxs-lookup"><span data-stu-id="17f38-107">Open a Help file to specific areas, such as the main page of a Table of Contents, the Index, or a search function.</span></span>  
  
## <a name="using-the-help-provider"></a><span data-ttu-id="17f38-108">使用服務提供者</span><span class="sxs-lookup"><span data-stu-id="17f38-108">Using the Help Provider</span></span>  
 <span data-ttu-id="17f38-109">新增<xref:System.Windows.Forms.HelpProvider>至您的 Windows 表單的元件可讓要公開 （expose） 的說明內容的表單上的其他控制項<xref:System.Windows.Forms.HelpProvider>元件。</span><span class="sxs-lookup"><span data-stu-id="17f38-109">Adding a <xref:System.Windows.Forms.HelpProvider> component to your Windows Form allows the other controls on the form to expose the Help properties of the <xref:System.Windows.Forms.HelpProvider> component.</span></span> <span data-ttu-id="17f38-110">這可讓您提供關於您的 Windows Form 上控制項的說明。</span><span class="sxs-lookup"><span data-stu-id="17f38-110">This enables you to provide help for the controls on your Windows Form.</span></span> <span data-ttu-id="17f38-111">您可以建立關聯的說明檔案<xref:System.Windows.Forms.HelpProvider>元件使用<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="17f38-111">You can associate a Help file with the <xref:System.Windows.Forms.HelpProvider> component using the <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property.</span></span> <span data-ttu-id="17f38-112">您指定的呼叫所提供的說明類型<xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A>並提供值，以從<xref:System.Windows.Forms.HelpNavigator>列舉指定的控制項。</span><span class="sxs-lookup"><span data-stu-id="17f38-112">You specify the type of Help provided by calling <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> and providing a value from the <xref:System.Windows.Forms.HelpNavigator> enumeration for the specified control.</span></span> <span data-ttu-id="17f38-113">您提供的關鍵字或主題的說明藉由呼叫<xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="17f38-113">You provide the keyword or topic for Help by calling the <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> method.</span></span>  
  
 <span data-ttu-id="17f38-114">（選擇性） 若要將特定的說明字串與另一個控制項產生關聯，請使用<xref:System.Windows.Forms.HelpProvider.SetHelpString%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="17f38-114">Optionally, to associate a specific Help string with another control, use the <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> method.</span></span> <span data-ttu-id="17f38-115">當使用者按下 F1 鍵，且焦點在控制項時，會顯示快顯視窗中使用這個方法的控制項與相關聯的字串。</span><span class="sxs-lookup"><span data-stu-id="17f38-115">The string that you associate with a control using this method is displayed in a pop-up window when the user presses the F1 key while the control has focus.</span></span>  
  
 <span data-ttu-id="17f38-116">如果<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>尚未設定，您必須使用<xref:System.Windows.Forms.HelpProvider.SetHelpString%2A>提供說明文字。</span><span class="sxs-lookup"><span data-stu-id="17f38-116">If <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> has not been set, you must use <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> to provide the Help text.</span></span> <span data-ttu-id="17f38-117">如果您已將兩者<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>和 [說明] 字串，說明根據<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>會優先使用。</span><span class="sxs-lookup"><span data-stu-id="17f38-117">If you have set both <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> and the Help string, Help based on <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> will take precedence.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17f38-118">您可能會遇到問題時指定的路徑中的說明檔案，請使用相對路徑<xref:System.Windows.Forms.Help.ShowHelp%2A>方法或<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>屬性<xref:System.Windows.Forms.HelpProvider>控制項。</span><span class="sxs-lookup"><span data-stu-id="17f38-118">You may encounter problems using the relative path when specifying the path to the Help file in the <xref:System.Windows.Forms.Help.ShowHelp%2A> method or <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property of the <xref:System.Windows.Forms.HelpProvider> control.</span></span> <span data-ttu-id="17f38-119">因此，請務必使用指定的說明檔的絕對檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="17f38-119">As such, be sure to use the absolute file path to specify the Help file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17f38-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17f38-120">See also</span></span>
- [<span data-ttu-id="17f38-121">Windows Forms 應用程式中的說明系統</span><span class="sxs-lookup"><span data-stu-id="17f38-121">Help Systems in Windows Forms Applications</span></span>](../../../../docs/framework/winforms/advanced/help-systems-in-windows-forms-applications.md)
