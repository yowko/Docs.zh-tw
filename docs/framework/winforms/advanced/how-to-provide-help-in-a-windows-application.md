---
title: 如何：在 Windows 應用程式中提供說明
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], Windows applications
- HTML Help [Windows Forms], Windows Forms
- Windows applications [Windows Forms], providing Help
- HelpProvider component [Windows Forms]
- forms [Windows Forms], providing Help
ms.assetid: 7c4e5cec-2bd2-4f0b-8d75-c2b88929bd61
ms.openlocfilehash: 98ed6d4e10d0eb80b99a36172980fcb33186c8ca
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43419198"
---
# <a name="how-to-provide-help-in-a-windows-application"></a><span data-ttu-id="d30a3-102">如何：在 Windows 應用程式中提供說明</span><span class="sxs-lookup"><span data-stu-id="d30a3-102">How to: Provide Help in a Windows Application</span></span>
<span data-ttu-id="d30a3-103">您可以使用的<xref:System.Windows.Forms.HelpProvider>附加至 Windows Form 上的特定控制項的說明檔內的 [說明] 主題的元件。</span><span class="sxs-lookup"><span data-stu-id="d30a3-103">You can use of the <xref:System.Windows.Forms.HelpProvider> component to attach Help topics within a Help file to specific controls on Windows Forms.</span></span> <span data-ttu-id="d30a3-104">說明檔可以是 HTML 或 HTMLHelp 1.x 或更高的格式。</span><span class="sxs-lookup"><span data-stu-id="d30a3-104">The Help file can be either HTML or HTMLHelp 1.x or greater format.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d30a3-105">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="d30a3-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d30a3-106">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="d30a3-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d30a3-107">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="d30a3-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-provide-help"></a><span data-ttu-id="d30a3-108">提供說明</span><span class="sxs-lookup"><span data-stu-id="d30a3-108">To provide Help</span></span>  
  
1.  <span data-ttu-id="d30a3-109">從**工具箱**，拖曳<xref:System.Windows.Forms.HelpProvider>元件至您的表單。</span><span class="sxs-lookup"><span data-stu-id="d30a3-109">From the **Toolbox**, drag a <xref:System.Windows.Forms.HelpProvider> component to your form.</span></span>  
  
     <span data-ttu-id="d30a3-110">此元件將位在 Windows Forms 設計工具底部的系統匣中。</span><span class="sxs-lookup"><span data-stu-id="d30a3-110">The component will reside in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="d30a3-111">在 **屬性**視窗中，將<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>屬性設為.chm、.col 或.htm 說明檔案。</span><span class="sxs-lookup"><span data-stu-id="d30a3-111">In the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property to the .chm, .col, or .htm Help file.</span></span>  
  
3.  <span data-ttu-id="d30a3-112">選取您已在您的表單，然後在另一個控制項**屬性**視窗中，將<xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="d30a3-112">Select another control you have on your form, and in the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> property.</span></span>  
  
     <span data-ttu-id="d30a3-113">這是透過傳遞的字串<xref:System.Windows.Forms.HelpProvider>元件至您的說明檔，以叫出適當的 [說明] 主題。</span><span class="sxs-lookup"><span data-stu-id="d30a3-113">This is the string passed through the <xref:System.Windows.Forms.HelpProvider> component to your Help file to summon the appropriate Help topic.</span></span>  
  
4.  <span data-ttu-id="d30a3-114">在 **屬性**視窗中，將<xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A>屬性設為值的<xref:System.Windows.Forms.HelpNavigator>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="d30a3-114">In the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> property to a value of the <xref:System.Windows.Forms.HelpNavigator> enumeration.</span></span>  
  
     <span data-ttu-id="d30a3-115">這會決定將 **HelpKeyword** 屬性傳遞給說明系統的方式。</span><span class="sxs-lookup"><span data-stu-id="d30a3-115">This determines the way in which the **HelpKeyword** property is passed to the Help system.</span></span> <span data-ttu-id="d30a3-116">下表顯示可能的設定和其描述。</span><span class="sxs-lookup"><span data-stu-id="d30a3-116">The following table shows the possible settings and their descriptions.</span></span>  
  
    |<span data-ttu-id="d30a3-117">成員名稱</span><span class="sxs-lookup"><span data-stu-id="d30a3-117">Member Name</span></span>|<span data-ttu-id="d30a3-118">描述</span><span class="sxs-lookup"><span data-stu-id="d30a3-118">Description</span></span>|  
    |-----------------|-----------------|  
    |<span data-ttu-id="d30a3-119">AssociateIndex</span><span class="sxs-lookup"><span data-stu-id="d30a3-119">AssociateIndex</span></span>|<span data-ttu-id="d30a3-120">指定在指定的 URL 中執行所指定主題的索引。</span><span class="sxs-lookup"><span data-stu-id="d30a3-120">Specifies that the index for a specified topic is performed in the specified URL.</span></span>|  
    |<span data-ttu-id="d30a3-121">Find</span><span class="sxs-lookup"><span data-stu-id="d30a3-121">Find</span></span>|<span data-ttu-id="d30a3-122">指定顯示所指定 URL 的搜尋頁面。</span><span class="sxs-lookup"><span data-stu-id="d30a3-122">Specifies that the search page of a specified URL is displayed.</span></span>|  
    |<span data-ttu-id="d30a3-123">索引</span><span class="sxs-lookup"><span data-stu-id="d30a3-123">Index</span></span>|<span data-ttu-id="d30a3-124">指定顯示所指定 URL 的索引。</span><span class="sxs-lookup"><span data-stu-id="d30a3-124">Specifies that the index of a specified URL is displayed.</span></span>|  
    |<span data-ttu-id="d30a3-125">KeywordIndex</span><span class="sxs-lookup"><span data-stu-id="d30a3-125">KeywordIndex</span></span>|<span data-ttu-id="d30a3-126">指定要搜尋的關鍵字以及要在指定的 URL 中採取的動作。</span><span class="sxs-lookup"><span data-stu-id="d30a3-126">Specifies a keyword to search for and the action to take in the specified URL.</span></span>|  
    |<span data-ttu-id="d30a3-127">TableOfContents</span><span class="sxs-lookup"><span data-stu-id="d30a3-127">TableOfContents</span></span>|<span data-ttu-id="d30a3-128">指定顯示 HTML 1.0 說明檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="d30a3-128">Specifies that the table of contents of the HTML 1.0 Help file is displayed.</span></span>|  
    |<span data-ttu-id="d30a3-129">主題</span><span class="sxs-lookup"><span data-stu-id="d30a3-129">Topic</span></span>|<span data-ttu-id="d30a3-130">指定顯示指定之 URL 所參考的主題。</span><span class="sxs-lookup"><span data-stu-id="d30a3-130">Specifies that the topic referenced by the specified URL is displayed.</span></span>|  
  
 <span data-ttu-id="d30a3-131">在執行階段，按下 F1 時控制項 — 對於您已設定**HelpKeyword**並**HelpNavigator**屬性 — 有焦點將會開啟您與它相關的說明檔<xref:System.Windows.Forms.HelpProvider>元件。</span><span class="sxs-lookup"><span data-stu-id="d30a3-131">At run time, pressing F1 when the control—for which you have set the **HelpKeyword** and **HelpNavigator** properties—has focus will open the Help file you associated with that <xref:System.Windows.Forms.HelpProvider> component.</span></span>  
  
 <span data-ttu-id="d30a3-132">目前，**HelpNamespace** 屬性支援下列三種格式的說明檔：HTMLHelp 1.x、HTMLHelp 2.0 和 HTML。</span><span class="sxs-lookup"><span data-stu-id="d30a3-132">Currently, the **HelpNamespace** property supports Help files in the following three formats: HTMLHelp 1.x, HTMLHelp 2.0, and HTML.</span></span> <span data-ttu-id="d30a3-133">因此，您可以將 **HelpNamespace** 屬性設定為 http:// 位址，例如網頁。</span><span class="sxs-lookup"><span data-stu-id="d30a3-133">Thus, you can set the **HelpNamespace** property to an http:// address, such as a Web page.</span></span> <span data-ttu-id="d30a3-134">如果這麼做，則會開啟將 **HelpKeyword** 屬性中所指定的字串用作錨點之網頁的預設瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="d30a3-134">If this is done, it will open the default browser to the Web page with the string specified in the **HelpKeyword** property used as the anchor.</span></span> <span data-ttu-id="d30a3-135">錨點是用來跳到 HTML 網頁的特定組件。</span><span class="sxs-lookup"><span data-stu-id="d30a3-135">The anchor is used to jump to a specific part of an HTML page.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d30a3-136">請先仔細檢查用戶端所傳送的任何資訊，再將它用於應用程式中。</span><span class="sxs-lookup"><span data-stu-id="d30a3-136">Be careful to check any information that is sent from a client before using it in your application.</span></span> <span data-ttu-id="d30a3-137">惡意使用者可能會嘗試傳送或插入可執行的指令碼、SQL 陳述式或其他程式碼。</span><span class="sxs-lookup"><span data-stu-id="d30a3-137">Malicious users might try to send or inject executable script, SQL statements, or other code.</span></span> <span data-ttu-id="d30a3-138">在顯示使用者的輸入、將它儲存在資料庫中，或使用它之前，請先檢查它未包含可能不安全的資訊。</span><span class="sxs-lookup"><span data-stu-id="d30a3-138">Before you display a user's input, store it in a database, or work with it, check that it does not contain potentially unsafe information.</span></span> <span data-ttu-id="d30a3-139">一般檢查方式是在您收到來自使用者的輸入時，使用規則運算式來尋找關鍵字，例如 "SCRIPT"。</span><span class="sxs-lookup"><span data-stu-id="d30a3-139">A typical way to check is to use a regular expression to look for keywords such as "SCRIPT" when you receive input from a user.</span></span>  
  
 <span data-ttu-id="d30a3-140">您也可以使用<xref:System.Windows.Forms.HelpProvider>元件來顯示快顯說明，即使您將它設定為顯示在 Windows Forms 上控制項的說明檔案。</span><span class="sxs-lookup"><span data-stu-id="d30a3-140">You can also use the <xref:System.Windows.Forms.HelpProvider> component to show pop-up Help, even if you have it configured to display Help files for the controls on your Windows Forms.</span></span> <span data-ttu-id="d30a3-141">如需詳細資訊，請參閱[如何：顯示快顯說明](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)。</span><span class="sxs-lookup"><span data-stu-id="d30a3-141">For more information, see [How to: Display Pop-up Help](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d30a3-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d30a3-142">See Also</span></span>  
 [<span data-ttu-id="d30a3-143">操作說明：顯示快顯說明</span><span class="sxs-lookup"><span data-stu-id="d30a3-143">How to: Display Pop-up Help</span></span>](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)  
 [<span data-ttu-id="d30a3-144">使用工具提示來顯示控制項說明</span><span class="sxs-lookup"><span data-stu-id="d30a3-144">Control Help Using ToolTips</span></span>](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 [<span data-ttu-id="d30a3-145">整合 Windows Forms 中的使用者說明</span><span class="sxs-lookup"><span data-stu-id="d30a3-145">Integrating User Help in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [<span data-ttu-id="d30a3-146">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d30a3-146">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)
