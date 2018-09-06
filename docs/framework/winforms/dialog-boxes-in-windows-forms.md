---
title: Windows Form 中的對話方塊
ms.date: 03/30/2017
helpviewer_keywords:
- dialog boxes [Windows Forms], Windows Forms
- Windows Forms dialog boxes
- dialogs [Windows Forms], using in Windows Forms
ms.assetid: d43d022b-451b-490d-9386-dc79d98fbf8a
ms.openlocfilehash: ef07c087ca43efaf99231453fcb56af0db24234a
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43776936"
---
# <a name="dialog-boxes-in-windows-forms"></a><span data-ttu-id="ba6fe-102">Windows Form 中的對話方塊</span><span class="sxs-lookup"><span data-stu-id="ba6fe-102">Dialog Boxes in Windows Forms</span></span>
<span data-ttu-id="ba6fe-103">對話方塊用來與使用者互動，並擷取資訊。</span><span class="sxs-lookup"><span data-stu-id="ba6fe-103">Dialog boxes are used to interact with the user and retrieve information.</span></span> <span data-ttu-id="ba6fe-104">簡單地說，對話方塊是一個其 <xref:System.Windows.Forms.FormBorderStyle> 列舉屬性設定為 `FixedDialog` 的表單。</span><span class="sxs-lookup"><span data-stu-id="ba6fe-104">In simple terms, a dialog box is a form with its <xref:System.Windows.Forms.FormBorderStyle> enumeration property set to `FixedDialog`.</span></span> <span data-ttu-id="ba6fe-105">您可以在 Visual Studio 中使用 Windows Form 設計工具來建構您自己的自訂對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ba6fe-105">You can construct your own custom dialog boxes by using the Windows Forms Designer in Visual Studio.</span></span> <span data-ttu-id="ba6fe-106">加入控制項，例如加入 `Label`、`Textbox` 和 `Button` 來依據您特定需求自訂對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ba6fe-106">Add controls such as `Label`, `Textbox`, and `Button` to customize dialog boxes to your specific needs.</span></span> <span data-ttu-id="ba6fe-107">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]也包含預先定義的對話方塊，例如**開啟舊檔**和訊息方塊，您可以針對自己的應用程式調整。</span><span class="sxs-lookup"><span data-stu-id="ba6fe-107">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] also includes predefined dialog boxes, such as **File Open** and message boxes, which you can adapt for your own applications.</span></span> <span data-ttu-id="ba6fe-108">如需詳細資訊，請參閱 <<c0> [ 對話方塊中控制項和元件](../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="ba6fe-108">For more information, see [Dialog-Box Controls and Components](../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ba6fe-109">本章節內容</span><span class="sxs-lookup"><span data-stu-id="ba6fe-109">In This Section</span></span>  
 [<span data-ttu-id="ba6fe-110">操作說明：顯示 Windows Forms 的對話方塊</span><span class="sxs-lookup"><span data-stu-id="ba6fe-110">How to: Display Dialog Boxes for Windows Forms</span></span>](../../../docs/framework/winforms/how-to-display-dialog-boxes-for-windows-forms.md)  
 <span data-ttu-id="ba6fe-111">提供顯示對話方塊的指示。</span><span class="sxs-lookup"><span data-stu-id="ba6fe-111">Gives directions for showing dialog boxes.</span></span>  
  
-   <span data-ttu-id="ba6fe-112">[如何： 擷取使用多個屬性選擇性地對話方塊資訊](https://msdn.microsoft.com/library/56taefba\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ba6fe-112">[How to: Retrieve Dialog Box Information Selectively Using Multiple Properties](https://msdn.microsoft.com/library/56taefba\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ba6fe-113">[如何： 從對話方塊中的父表單擷取資訊](https://msdn.microsoft.com/library/k70t19bb\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ba6fe-113">[How to: Retrieve Information from the Parent Form of a Dialog Box](https://msdn.microsoft.com/library/k70t19bb\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ba6fe-114">[使用者輸入到對話方塊](https://msdn.microsoft.com/library/1s9ws53w\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ba6fe-114">[User Input to Dialog Boxes](https://msdn.microsoft.com/library/1s9ws53w\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ba6fe-115">[如何： 擷取對話方塊結果](https://msdn.microsoft.com/library/40x40td1\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ba6fe-115">[How to: Retrieve the Result for Dialog Boxes](https://msdn.microsoft.com/library/40x40td1\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ba6fe-116">[逐步解說： 擷取使用物件共同地對話方塊資訊](https://msdn.microsoft.com/library/cakx2hdw\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ba6fe-116">[Walkthrough: Retrieving Dialog Box Information Collectively Using Objects](https://msdn.microsoft.com/library/cakx2hdw\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ba6fe-117">[如何： 關閉對話方塊並保留使用者輸入](https://msdn.microsoft.com/library/65ad5907\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ba6fe-117">[How to: Close Dialog Boxes and Retain User Input](https://msdn.microsoft.com/library/65ad5907\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ba6fe-118">[如何： 在設計階段建立對話方塊](https://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ba6fe-118">[How to: Create Dialog Boxes at Design Time](https://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ba6fe-119">[如何： 顯示訊息方塊](https://msdn.microsoft.com/library/3tt9e94f\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ba6fe-119">[How to: Display Message Boxes](https://msdn.microsoft.com/library/3tt9e94f\(v=vs.110\))</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ba6fe-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="ba6fe-120">Related Sections</span></span>  
 [<span data-ttu-id="ba6fe-121">對話方塊控制項和元件</span><span class="sxs-lookup"><span data-stu-id="ba6fe-121">Dialog-Box Controls and Components</span></span>](../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)  
 <span data-ttu-id="ba6fe-122">列出預先定義的對話方塊控制項。</span><span class="sxs-lookup"><span data-stu-id="ba6fe-122">Lists the predefined dialog box controls.</span></span>  
  
 [<span data-ttu-id="ba6fe-123">變更 Windows Forms 的外觀</span><span class="sxs-lookup"><span data-stu-id="ba6fe-123">Changing the Appearance of Windows Forms</span></span>](../../../docs/framework/winforms/changing-the-appearance-of-windows-forms.md)  
 <span data-ttu-id="ba6fe-124">包含主題連結，描述如何變更 Windows Form 應用程式的外觀。</span><span class="sxs-lookup"><span data-stu-id="ba6fe-124">Contains links to topics that describe how to change the appearance of Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="ba6fe-125">TabControl 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="ba6fe-125">TabControl Control Overview</span></span>](../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 <span data-ttu-id="ba6fe-126">說明如何將索引標籤控制項合併到對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="ba6fe-126">Explains how you incorporate the tab control into a dialog box.</span></span>
