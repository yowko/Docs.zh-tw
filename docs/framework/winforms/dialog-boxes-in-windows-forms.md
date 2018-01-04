---
title: "Windows Form 中的對話方塊"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dialog boxes [Windows Forms], Windows Forms
- Windows Forms dialog boxes
- dialogs [Windows Forms], using in Windows Forms
ms.assetid: d43d022b-451b-490d-9386-dc79d98fbf8a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b8f493013744ffa7819d4cb554f794d9a591a371
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="dialog-boxes-in-windows-forms"></a><span data-ttu-id="d9d21-102">Windows Form 中的對話方塊</span><span class="sxs-lookup"><span data-stu-id="d9d21-102">Dialog Boxes in Windows Forms</span></span>
<span data-ttu-id="d9d21-103">對話方塊用來與使用者互動，並擷取資訊。</span><span class="sxs-lookup"><span data-stu-id="d9d21-103">Dialog boxes are used to interact with the user and retrieve information.</span></span> <span data-ttu-id="d9d21-104">簡單地說，對話方塊是一個其 <xref:System.Windows.Forms.FormBorderStyle> 列舉屬性設定為 `FixedDialog` 的表單。</span><span class="sxs-lookup"><span data-stu-id="d9d21-104">In simple terms, a dialog box is a form with its <xref:System.Windows.Forms.FormBorderStyle> enumeration property set to `FixedDialog`.</span></span> <span data-ttu-id="d9d21-105">您可以使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中的 Windows Form 設計工具，建構自己的自訂對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d9d21-105">You can construct your own custom dialog boxes by using the Windows Forms Designer in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="d9d21-106">加入控制項，例如加入 `Label`、`Textbox` 和 `Button` 來依據您特定需求自訂對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d9d21-106">Add controls such as `Label`, `Textbox`, and `Button` to customize dialog boxes to your specific needs.</span></span> <span data-ttu-id="d9d21-107">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]也包含預先定義的對話方塊，例如**開啟舊檔**和訊息方塊，您可以調整您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d9d21-107">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] also includes predefined dialog boxes, such as **File Open** and message boxes, which you can adapt for your own applications.</span></span> <span data-ttu-id="d9d21-108">如需詳細資訊，請參閱[對話方塊控制項和元件](../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="d9d21-108">For more information, see [Dialog-Box Controls and Components](../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d9d21-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="d9d21-109">In This Section</span></span>  
 [<span data-ttu-id="d9d21-110">操作說明：顯示 Windows Forms 的對話方塊</span><span class="sxs-lookup"><span data-stu-id="d9d21-110">How to: Display Dialog Boxes for Windows Forms</span></span>](../../../docs/framework/winforms/how-to-display-dialog-boxes-for-windows-forms.md)  
 <span data-ttu-id="d9d21-111">提供顯示對話方塊的指示。</span><span class="sxs-lookup"><span data-stu-id="d9d21-111">Gives directions for showing dialog boxes.</span></span>  
  
-   <span data-ttu-id="d9d21-112">[如何： 擷取使用多個屬性選擇性地對話方塊資訊](http://msdn.microsoft.com/library/56taefba\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d9d21-112">[How to: Retrieve Dialog Box Information Selectively Using Multiple Properties](http://msdn.microsoft.com/library/56taefba\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="d9d21-113">[如何： 從對話方塊中的父表單擷取資訊](http://msdn.microsoft.com/library/k70t19bb\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d9d21-113">[How to: Retrieve Information from the Parent Form of a Dialog Box](http://msdn.microsoft.com/library/k70t19bb\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="d9d21-114">[使用者輸入到對話方塊](http://msdn.microsoft.com/library/1s9ws53w\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d9d21-114">[User Input to Dialog Boxes](http://msdn.microsoft.com/library/1s9ws53w\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="d9d21-115">[如何： 擷取對話方塊的結果](http://msdn.microsoft.com/library/40x40td1\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d9d21-115">[How to: Retrieve the Result for Dialog Boxes](http://msdn.microsoft.com/library/40x40td1\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="d9d21-116">[逐步解說： 擷取使用物件共同地對話方塊資訊](http://msdn.microsoft.com/library/cakx2hdw\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d9d21-116">[Walkthrough: Retrieving Dialog Box Information Collectively Using Objects](http://msdn.microsoft.com/library/cakx2hdw\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="d9d21-117">[如何： 關閉對話方塊並保留使用者輸入](http://msdn.microsoft.com/library/65ad5907\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d9d21-117">[How to: Close Dialog Boxes and Retain User Input](http://msdn.microsoft.com/library/65ad5907\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="d9d21-118">[如何： 在設計階段建立對話方塊](http://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d9d21-118">[How to: Create Dialog Boxes at Design Time](http://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="d9d21-119">[如何： 顯示訊息方塊](http://msdn.microsoft.com/library/3tt9e94f\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d9d21-119">[How to: Display Message Boxes](http://msdn.microsoft.com/library/3tt9e94f\(v=vs.110\))</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d9d21-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="d9d21-120">Related Sections</span></span>  
 [<span data-ttu-id="d9d21-121">對話方塊控制項和元件</span><span class="sxs-lookup"><span data-stu-id="d9d21-121">Dialog-Box Controls and Components</span></span>](../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)  
 <span data-ttu-id="d9d21-122">列出預先定義的對話方塊控制項。</span><span class="sxs-lookup"><span data-stu-id="d9d21-122">Lists the predefined dialog box controls.</span></span>  
  
 [<span data-ttu-id="d9d21-123">變更 Windows Forms 的外觀</span><span class="sxs-lookup"><span data-stu-id="d9d21-123">Changing the Appearance of Windows Forms</span></span>](../../../docs/framework/winforms/changing-the-appearance-of-windows-forms.md)  
 <span data-ttu-id="d9d21-124">包含主題連結，描述如何變更 Windows Forms 應用程式的外觀。</span><span class="sxs-lookup"><span data-stu-id="d9d21-124">Contains links to topics that describe how to change the appearance of Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="d9d21-125">TabControl 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="d9d21-125">TabControl Control Overview</span></span>](../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 <span data-ttu-id="d9d21-126">說明如何將索引標籤控制項合併到對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="d9d21-126">Explains how you incorporate the tab control into a dialog box.</span></span>
