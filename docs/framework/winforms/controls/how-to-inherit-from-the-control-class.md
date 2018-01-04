---
title: "如何：繼承自 Control 類別"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f7cbca79cd3541df1db7ace3a7d5f67bf3f2b2ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-inherit-from-the-control-class"></a><span data-ttu-id="dd460-102">如何：繼承自 Control 類別</span><span class="sxs-lookup"><span data-stu-id="dd460-102">How to: Inherit from the Control Class</span></span>
<span data-ttu-id="dd460-103">如果您想要建立使用 Windows Form 上的完全自訂控制項，您應該繼承自<xref:System.Windows.Forms.Control>類別。</span><span class="sxs-lookup"><span data-stu-id="dd460-103">If you want to create a completely custom control to use on a Windows Form, you should inherit from the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="dd460-104">同時繼承自<xref:System.Windows.Forms.Control>類別會要求您執行詳細的規劃和實作，它也提供您選項的最大範圍。</span><span class="sxs-lookup"><span data-stu-id="dd460-104">While inheriting from the <xref:System.Windows.Forms.Control> class requires that you perform more planning and implementation, it also provides you with the largest range of options.</span></span> <span data-ttu-id="dd460-105">繼承自<xref:System.Windows.Forms.Control>，繼承的非常基本的功能可讓工作的控制項。</span><span class="sxs-lookup"><span data-stu-id="dd460-105">When inheriting from <xref:System.Windows.Forms.Control>, you inherit the very basic functionality that makes controls work.</span></span> <span data-ttu-id="dd460-106">繼承的功能<xref:System.Windows.Forms.Control>類別會處理透過鍵盤和滑鼠的使用者輸入，定義範圍和控制項的大小、 提供的 windows 控制代碼，並提供訊息處理和安全性。</span><span class="sxs-lookup"><span data-stu-id="dd460-106">The functionality inherent in the <xref:System.Windows.Forms.Control> class handles user input through the keyboard and mouse, defines the bounds and size of the control, provides a windows handle, and provides message handling and security.</span></span> <span data-ttu-id="dd460-107">它不會併入任何繪製功能 (在此例中是控制項圖形化介面的實際轉譯)，也不會併入任何特定的使用者互動功能。</span><span class="sxs-lookup"><span data-stu-id="dd460-107">It does not incorporate any painting, which in this case is the actual rendering of the graphical interface of the control, nor does it incorporate any specific user interaction functionality.</span></span> <span data-ttu-id="dd460-108">您必須透過自訂程式碼來提供上述一切。</span><span class="sxs-lookup"><span data-stu-id="dd460-108">You must provide all of these aspects through custom code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dd460-109">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="dd460-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="dd460-110">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="dd460-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="dd460-111">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="dd460-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-a-custom-control"></a><span data-ttu-id="dd460-112">建立自訂控制項</span><span class="sxs-lookup"><span data-stu-id="dd460-112">To create a custom control</span></span>  
  
1.  <span data-ttu-id="dd460-113">建立新的 [Windows 應用程式] 或 [Windows 控制項程式庫] 專案。</span><span class="sxs-lookup"><span data-stu-id="dd460-113">Create a new **Windows Application** or **Windows Control Library** project.</span></span>  
  
2.  <span data-ttu-id="dd460-114">從 [專案] 功能表中，選擇 [新增類別]。</span><span class="sxs-lookup"><span data-stu-id="dd460-114">From the **Project** menu, choose **Add Class**.</span></span>  
  
3.  <span data-ttu-id="dd460-115">在 [新增項目] 對話方塊中，按一下 [自訂控制項]。</span><span class="sxs-lookup"><span data-stu-id="dd460-115">In the **Add New Item** dialog box, click **Custom Control**.</span></span>  
  
     <span data-ttu-id="dd460-116">新的自訂控制項會新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="dd460-116">A new custom control is added to your project.</span></span>  
  
4.  <span data-ttu-id="dd460-117">按 F7 鍵，開啟自訂控制項的 [程式碼編輯器]。</span><span class="sxs-lookup"><span data-stu-id="dd460-117">Press F7 to open the **Code Editor** for your custom control.</span></span>  
  
5.  <span data-ttu-id="dd460-118">找出<xref:System.Windows.Forms.Control.OnPaint%2A>方法，將會是空的呼叫除了<xref:System.Windows.Forms.Control.OnPaint%2A>基底類別的方法。</span><span class="sxs-lookup"><span data-stu-id="dd460-118">Locate the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which will be empty except for a call to the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class.</span></span>  
  
6.  <span data-ttu-id="dd460-119">修改程式碼，以併入您要用於控制項的任何自訂繪製功能。</span><span class="sxs-lookup"><span data-stu-id="dd460-119">Modify the code to incorporate any custom painting you want for your control.</span></span>  
  
     <span data-ttu-id="dd460-120">如需撰寫程式碼來轉譯控制項圖形的相關資訊，請參閱[自訂控制項繪製和轉譯](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)。</span><span class="sxs-lookup"><span data-stu-id="dd460-120">For information about writing code to render graphics for controls, see [Custom Control Painting and Rendering](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).</span></span>  
  
7.  <span data-ttu-id="dd460-121">實作您的控制項將併入的任何自訂方法、屬性或事件。</span><span class="sxs-lookup"><span data-stu-id="dd460-121">Implement any custom methods, properties, or events that your control will incorporate.</span></span>  
  
8.  <span data-ttu-id="dd460-122">儲存並測試您的控制項。</span><span class="sxs-lookup"><span data-stu-id="dd460-122">Save and test your control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd460-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="dd460-123">See Also</span></span>  
 [<span data-ttu-id="dd460-124">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="dd460-124">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [<span data-ttu-id="dd460-125">操作說明：繼承自 UserControl 類別</span><span class="sxs-lookup"><span data-stu-id="dd460-125">How to: Inherit from the UserControl Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [<span data-ttu-id="dd460-126">操作說明：繼承自現有的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="dd460-126">How to: Inherit from Existing Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [<span data-ttu-id="dd460-127">操作說明：撰寫 Windows Forms 的控制項</span><span class="sxs-lookup"><span data-stu-id="dd460-127">How to: Author Controls for Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [<span data-ttu-id="dd460-128">Visual Basic 中的繼承事件處理常式疑難排解</span><span class="sxs-lookup"><span data-stu-id="dd460-128">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [<span data-ttu-id="dd460-129">在設計階段開發 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="dd460-129">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)
