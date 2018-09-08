---
title: 如何：撰寫 Windows Forms 的控制項
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], creating
- UserControl class [Windows Forms], Windows Forms
- custom controls [Windows Forms], creating
ms.assetid: 7570e982-545b-4c3a-a7c7-55581d313400
ms.openlocfilehash: 844e38fc62fc9fb04a723c1a4a8ad834e957c8ce
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44132683"
---
# <a name="how-to-author-controls-for-windows-forms"></a><span data-ttu-id="93379-102">如何：撰寫 Windows Forms 的控制項</span><span class="sxs-lookup"><span data-stu-id="93379-102">How to: Author Controls for Windows Forms</span></span>
<span data-ttu-id="93379-103">控制項所代表使用者與程式之間的圖形化連結。</span><span class="sxs-lookup"><span data-stu-id="93379-103">A control represents a graphical link between the user and the program.</span></span> <span data-ttu-id="93379-104">控制項可以提供或處理資料、接受使用者輸入、回應事件，或執行任意數目的其他功能來連接使用者與應用程式。</span><span class="sxs-lookup"><span data-stu-id="93379-104">A control can provide or process data, accept user input, respond to events, or perform any number of other functions that connect the user and the application.</span></span> <span data-ttu-id="93379-105">因為控制項本質上是具有圖形化介面的元件，所以可以提供元件所執行的任何功能，以及提供使用者互動。</span><span class="sxs-lookup"><span data-stu-id="93379-105">Because a control is essentially a component with a graphical interface, it can serve any function that a component does, as well as provide user interaction.</span></span> <span data-ttu-id="93379-106">建立控制項以提供特定用途，而編寫控制項只是另一個程式設計工作。</span><span class="sxs-lookup"><span data-stu-id="93379-106">Controls are created to serve specific purposes, and authoring controls is just another programming task.</span></span> <span data-ttu-id="93379-107">記住這點，下列步驟代表控制項撰寫處理序的概觀。</span><span class="sxs-lookup"><span data-stu-id="93379-107">With that in mind, the following steps represent an overview of the control authoring process.</span></span> <span data-ttu-id="93379-108">連結可提供各個步驟的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="93379-108">Links provide additional information on the individual steps.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93379-109">如果您想要撰寫自訂控制項以在 Web Forms 上使用，請參閱[開發自訂 ASP.NET 伺服器控制項](https://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef)。</span><span class="sxs-lookup"><span data-stu-id="93379-109">If you want to author a custom control to use on Web Forms, see [Developing Custom ASP.NET Server Controls](https://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).</span></span>  
>   
>  <span data-ttu-id="93379-110">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="93379-110">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="93379-111">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="93379-111">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="93379-112">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="93379-112">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-author-a-control"></a><span data-ttu-id="93379-113">撰寫控制項</span><span class="sxs-lookup"><span data-stu-id="93379-113">To author a control</span></span>  
  
1.  <span data-ttu-id="93379-114">決定您希望控制項完成的事項，或在您的應用程式中扮演的角色。</span><span class="sxs-lookup"><span data-stu-id="93379-114">Determine what you want your control to accomplish, or what part it will play in your application.</span></span> <span data-ttu-id="93379-115">應考量的因素包括：</span><span class="sxs-lookup"><span data-stu-id="93379-115">Factors to consider are:</span></span>  
  
    -   <span data-ttu-id="93379-116">您需要何種圖形化介面？</span><span class="sxs-lookup"><span data-stu-id="93379-116">What kind of graphical interface do you need?</span></span>  
  
    -   <span data-ttu-id="93379-117">此控制項將處理哪些特定的使用者互動？</span><span class="sxs-lookup"><span data-stu-id="93379-117">What specific user interactions will this control handle?</span></span>  
  
    -   <span data-ttu-id="93379-118">您需要的功能是由任何現有控制項提供嗎？</span><span class="sxs-lookup"><span data-stu-id="93379-118">Is the functionality you need provided by any existing controls?</span></span>  
  
    -   <span data-ttu-id="93379-119">您可以藉由結合數個 Windows Forms 控制項來取得您需要的功能嗎？</span><span class="sxs-lookup"><span data-stu-id="93379-119">Can you get the functionality you need by combining several Windows Forms controls?</span></span>  
  
2.  <span data-ttu-id="93379-120">如果您需要控制項的物件模型，請決定如何將功能散發於整個物件模型，以及在控制項與任何子物件之間分配功能。</span><span class="sxs-lookup"><span data-stu-id="93379-120">If you need an object model for your control, determine how functionality will be distributed throughout the object model, and divide up functionality between the control and any subobjects.</span></span> <span data-ttu-id="93379-121">如果您要規劃複雜的控制項，或想要併入多個功能，物件模型可能很有用。</span><span class="sxs-lookup"><span data-stu-id="93379-121">An object model may be useful if you are planning a complex control, or want to incorporate several functionalities.</span></span>  
  
3.  <span data-ttu-id="93379-122">決定您需要的控制項類型 (例如，使用者控制項、自訂控制項、繼承的 Windows Forms 控制項)。</span><span class="sxs-lookup"><span data-stu-id="93379-122">Determine the type of control (for example, user control, custom control, inherited Windows Forms control) you need.</span></span> <span data-ttu-id="93379-123">如需詳細資訊，請參閱[控制項類型建議](../../../../docs/framework/winforms/controls/control-type-recommendations.md)和[各種自訂控制項](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="93379-123">For details, see [Control Type Recommendations](../../../../docs/framework/winforms/controls/control-type-recommendations.md) and [Varieties of Custom Controls](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).</span></span>  
  
4.  <span data-ttu-id="93379-124">將功能表示為控制項的屬性、方法和事件及其子物件或附屬結構，並指派適當的存取層級 (例如，公用、受保護等等)。</span><span class="sxs-lookup"><span data-stu-id="93379-124">Express functionality as properties, methods, and events of the control and its subobjects or subsidiary structures, and assign appropriate access levels (for example, public, protected, and so on).</span></span>  
  
5.  <span data-ttu-id="93379-125">如果您需要自訂控制項的繪製，請為它新增程式碼。</span><span class="sxs-lookup"><span data-stu-id="93379-125">If you need custom painting for your control, add code for it.</span></span> <span data-ttu-id="93379-126">如需詳細資訊，請參閱[自訂控制項繪製和轉譯](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)。</span><span class="sxs-lookup"><span data-stu-id="93379-126">For details, see [Custom Control Painting and Rendering](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).</span></span>  
  
6.  <span data-ttu-id="93379-127">如果您的控制項繼承自<xref:System.Windows.Forms.UserControl>，您可以藉由建置控制專案中執行測試及其執行階段行為**UserControl 測試容器**。</span><span class="sxs-lookup"><span data-stu-id="93379-127">If your control inherits from <xref:System.Windows.Forms.UserControl>, you can test its runtime behavior by building the control project and running it in the **UserControl Test Container**.</span></span> <span data-ttu-id="93379-128">如需詳細資訊，請參閱[如何：測試 UserControl 的執行階段行為](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)。</span><span class="sxs-lookup"><span data-stu-id="93379-128">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
7.  <span data-ttu-id="93379-129">您也可以建立新專案 (例如 Windows 應用程式) 並將它放入容器中，來測試您的控制項並進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="93379-129">You can also test and debug your control by creating a new project, such as a Windows Application, and placing it into a container.</span></span> <span data-ttu-id="93379-130">此處理序的示範在[逐步解說：使用 Visual Basic 撰寫複合控制項](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)中。</span><span class="sxs-lookup"><span data-stu-id="93379-130">This process is demonstrated as part of [Walkthrough: Authoring a Composite Control with Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md).</span></span>  
  
8.  <span data-ttu-id="93379-131">當您新增每項功能時，將功能新增至測試專案，以執行新功能。</span><span class="sxs-lookup"><span data-stu-id="93379-131">As you add each feature, add features to your test project to exercise the new functionality.</span></span>  
  
9. <span data-ttu-id="93379-132">重複執行，並調整設計。</span><span class="sxs-lookup"><span data-stu-id="93379-132">Repeat, refining the design.</span></span>  
  
10. <span data-ttu-id="93379-133">封裝並部署您的控制項。</span><span class="sxs-lookup"><span data-stu-id="93379-133">Package and deploy your control.</span></span> <span data-ttu-id="93379-134">如需詳細資訊，請參閱[部署應用程式、服務和元件](https://msdn.microsoft.com/library/wtzawcsz)。</span><span class="sxs-lookup"><span data-stu-id="93379-134">For details, see [Deploying Applications, Services, and Components](https://msdn.microsoft.com/library/wtzawcsz).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93379-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93379-135">See Also</span></span>  
 [<span data-ttu-id="93379-136">逐步解說：使用 Visual Basic 撰寫複合控制項</span><span class="sxs-lookup"><span data-stu-id="93379-136">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [<span data-ttu-id="93379-137">逐步解說：使用 Visual Basic 繼承自 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="93379-137">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [<span data-ttu-id="93379-138">操作說明：繼承自 UserControl 類別</span><span class="sxs-lookup"><span data-stu-id="93379-138">How to: Inherit from the UserControl Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [<span data-ttu-id="93379-139">操作說明：繼承自 Control 類別</span><span class="sxs-lookup"><span data-stu-id="93379-139">How to: Inherit from the Control Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [<span data-ttu-id="93379-140">操作說明：繼承自現有的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="93379-140">How to: Inherit from Existing Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [<span data-ttu-id="93379-141">操作說明：測試 UserControl 的執行階段行為</span><span class="sxs-lookup"><span data-stu-id="93379-141">How to: Test the Run-Time Behavior of a UserControl</span></span>](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 [<span data-ttu-id="93379-142">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="93379-142">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
