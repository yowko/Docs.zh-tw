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
ms.openlocfilehash: cefc590bb3011b282392504a78ac5c393c58493e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965687"
---
# <a name="helpprovider-component-overview-windows-forms"></a><span data-ttu-id="e6281-102">HelpProvider 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="e6281-102">HelpProvider Component Overview (Windows Forms)</span></span>
<span data-ttu-id="e6281-103">Windows Forms [HelpProvider](helpprovider-component-windows-forms.md)元件是用來將 html help 1.x 說明檔 (使用 Html 說明研討會產生的 .chm 檔案或 .htm 檔案) 與您的 Windows 應用程式建立關聯。</span><span class="sxs-lookup"><span data-stu-id="e6281-103">The Windows Forms [HelpProvider](helpprovider-component-windows-forms.md) component is used to associate an HTML Help 1.x Help file (either a .chm file, produced with the HTML Help Workshop, or an .htm file) with your Windows application.</span></span> <span data-ttu-id="e6281-104">您可以透過各種方式來提供說明:</span><span class="sxs-lookup"><span data-stu-id="e6281-104">You can provide help in a variety of ways:</span></span>  
  
- <span data-ttu-id="e6281-105">提供 Windows Forms 上控制項的即時線上說明。</span><span class="sxs-lookup"><span data-stu-id="e6281-105">Provide context-sensitive Help for controls on Windows Forms.</span></span>  
  
- <span data-ttu-id="e6281-106">在特定對話方塊或對話方塊上的特定控制項上提供即時線上說明。</span><span class="sxs-lookup"><span data-stu-id="e6281-106">Provide context-sensitive Help on a particular dialog box or specific controls on a dialog box.</span></span>  
  
- <span data-ttu-id="e6281-107">開啟說明檔至特定區域, 例如目錄的主頁面、索引或搜尋函數。</span><span class="sxs-lookup"><span data-stu-id="e6281-107">Open a Help file to specific areas, such as the main page of a Table of Contents, the Index, or a search function.</span></span>  
  
## <a name="using-the-help-provider"></a><span data-ttu-id="e6281-108">使用說明提供者</span><span class="sxs-lookup"><span data-stu-id="e6281-108">Using the Help Provider</span></span>  
 <span data-ttu-id="e6281-109">將元件新增至您的 Windows form, 可讓表單上的其他控制項公開該<xref:System.Windows.Forms.HelpProvider>元件的說明屬性。 <xref:System.Windows.Forms.HelpProvider></span><span class="sxs-lookup"><span data-stu-id="e6281-109">Adding a <xref:System.Windows.Forms.HelpProvider> component to your Windows Form allows the other controls on the form to expose the Help properties of the <xref:System.Windows.Forms.HelpProvider> component.</span></span> <span data-ttu-id="e6281-110">這可讓您為 Windows Form 上的控制項提供說明。</span><span class="sxs-lookup"><span data-stu-id="e6281-110">This enables you to provide help for the controls on your Windows Form.</span></span> <span data-ttu-id="e6281-111">您可以<xref:System.Windows.Forms.HelpProvider> <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>使用屬性, 讓說明檔與元件產生關聯。</span><span class="sxs-lookup"><span data-stu-id="e6281-111">You can associate a Help file with the <xref:System.Windows.Forms.HelpProvider> component using the <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property.</span></span> <span data-ttu-id="e6281-112">您可以藉由呼叫<xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A>並提供<xref:System.Windows.Forms.HelpNavigator>來自指定控制項之列舉的值, 來指定所提供的說明類型。</span><span class="sxs-lookup"><span data-stu-id="e6281-112">You specify the type of Help provided by calling <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> and providing a value from the <xref:System.Windows.Forms.HelpNavigator> enumeration for the specified control.</span></span> <span data-ttu-id="e6281-113">藉由呼叫<xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A>方法, 您可以提供關鍵字或主題來取得協助。</span><span class="sxs-lookup"><span data-stu-id="e6281-113">You provide the keyword or topic for Help by calling the <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> method.</span></span>  
  
 <span data-ttu-id="e6281-114">(選擇性) 若要讓特定的說明字串與另一個控制項<xref:System.Windows.Forms.HelpProvider.SetHelpString%2A>產生關聯, 請使用方法。</span><span class="sxs-lookup"><span data-stu-id="e6281-114">Optionally, to associate a specific Help string with another control, use the <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> method.</span></span> <span data-ttu-id="e6281-115">當使用者按下 F1 鍵時, 使用這個方法與控制項建立關聯的字串會顯示在快顯視窗中, 而控制項則具有焦點。</span><span class="sxs-lookup"><span data-stu-id="e6281-115">The string that you associate with a control using this method is displayed in a pop-up window when the user presses the F1 key while the control has focus.</span></span>  
  
 <span data-ttu-id="e6281-116">如果<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>尚未設定, 則您必須使用<xref:System.Windows.Forms.HelpProvider.SetHelpString%2A>來提供解說文字。</span><span class="sxs-lookup"><span data-stu-id="e6281-116">If <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> has not been set, you must use <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> to provide the Help text.</span></span> <span data-ttu-id="e6281-117">如果您同時<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>設定了和說明字串, 將會優先使用<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>以為基礎的說明。</span><span class="sxs-lookup"><span data-stu-id="e6281-117">If you have set both <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> and the Help string, Help based on <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> will take precedence.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e6281-118">在<xref:System.Windows.Forms.Help.ShowHelp%2A> <xref:System.Windows.Forms.HelpProvider>控制項的方法或<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>屬性中指定說明檔的路徑時, 您可能會遇到使用相對路徑的問題。</span><span class="sxs-lookup"><span data-stu-id="e6281-118">You may encounter problems using the relative path when specifying the path to the Help file in the <xref:System.Windows.Forms.Help.ShowHelp%2A> method or <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property of the <xref:System.Windows.Forms.HelpProvider> control.</span></span> <span data-ttu-id="e6281-119">因此, 請務必使用絕對檔案路徑來指定說明檔。</span><span class="sxs-lookup"><span data-stu-id="e6281-119">As such, be sure to use the absolute file path to specify the Help file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6281-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6281-120">See also</span></span>

- [<span data-ttu-id="e6281-121">Windows Forms 應用程式中的說明系統</span><span class="sxs-lookup"><span data-stu-id="e6281-121">Help Systems in Windows Forms Applications</span></span>](../advanced/help-systems-in-windows-forms-applications.md)
