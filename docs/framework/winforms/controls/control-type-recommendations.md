---
title: "控制項類型建議"
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
- user controls [Windows Forms], when to use
- custom controls [Windows Forms], types
- controls [Windows Forms], creating
ms.assetid: 5235fe9d-c36a-4c08-ae76-6cb90b50085e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 638a439a663925be6eea230984310f7b86b81030
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="control-type-recommendations"></a><span data-ttu-id="5e31d-102">控制項類型建議</span><span class="sxs-lookup"><span data-stu-id="5e31d-102">Control Type Recommendations</span></span>
<span data-ttu-id="5e31d-103">.NET Framework 可讓您有能力開發及實作新的控制項。</span><span class="sxs-lookup"><span data-stu-id="5e31d-103">The .NET Framework gives you power to develop and implement new controls.</span></span> <span data-ttu-id="5e31d-104">除了熟悉的使用者控制項，現在您會發現您也可以撰寫自訂控制項來執行它們自己的繪製，而且甚至能夠透過繼承，擴充現有控制項的功能。</span><span class="sxs-lookup"><span data-stu-id="5e31d-104">In addition to the familiar user control, you will now find that you are able to write custom controls that perform their own painting, and are even able to extend the functionality of existing controls through inheritance.</span></span> <span data-ttu-id="5e31d-105">決定要建立的控制項類型可能會令人困擾。</span><span class="sxs-lookup"><span data-stu-id="5e31d-105">Deciding which type of control to create can be confusing.</span></span> <span data-ttu-id="5e31d-106">本章節強調您可以繼承的各類型控制項之間的差異，並提供關於為您的專案選擇類型的注意事項。</span><span class="sxs-lookup"><span data-stu-id="5e31d-106">This section highlights the differences between the various types of controls from which you can inherit, and gives considerations regarding the type to choose for your project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e31d-107">如果您想要撰寫 Web Forms 上使用的控制項，請參閱[開發自訂 ASP.NET 伺服器控制項](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef)。</span><span class="sxs-lookup"><span data-stu-id="5e31d-107">If you want to author a control to use on Web Forms, see [Developing Custom ASP.NET Server Controls](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).</span></span>  
  
## <a name="inheriting-from-a-windows-forms-control"></a><span data-ttu-id="5e31d-108">繼承 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="5e31d-108">Inheriting from a Windows Forms Control</span></span>  
 <span data-ttu-id="5e31d-109">您可以從任何現有的 Windows Form 控制項衍生繼承的控制項。</span><span class="sxs-lookup"><span data-stu-id="5e31d-109">You can derive an inherited control from any existing Windows Forms control.</span></span> <span data-ttu-id="5e31d-110">這種方法可讓您保留 Windows Form 控制項的所有固有功能，然後藉由加入自訂屬性、方法或其他功能，以擴充該功能。</span><span class="sxs-lookup"><span data-stu-id="5e31d-110">This approach allows you to retain all of the inherent functionality of a Windows Forms control, and to then extend that functionality by adding custom properties, methods, or other functionality.</span></span> <span data-ttu-id="5e31d-111">例如，您可以建立從 <xref:System.Windows.Forms.TextBox> 衍生的控制項，它只接受數字，而且會自動將輸入轉換成值。</span><span class="sxs-lookup"><span data-stu-id="5e31d-111">For example, you might create a control derived from <xref:System.Windows.Forms.TextBox> that can accept only numbers and automatically converts input into a value.</span></span> <span data-ttu-id="5e31d-112">這類控制項可能會包含在文字方塊中的文字變更呼叫的驗證程式碼，而且可能會有一個額外的屬性 Value。</span><span class="sxs-lookup"><span data-stu-id="5e31d-112">Such a control might contain validation code that was called whenever the text in the text box changed, and could have an additional property, Value.</span></span> <span data-ttu-id="5e31d-113">在一些控制項中，您也可以藉由覆寫基底類別的 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法，將自訂外觀加入至控制項的圖形化介面。</span><span class="sxs-lookup"><span data-stu-id="5e31d-113">In some controls, you can also add a custom appearance to the graphical interface of your control by overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class.</span></span>  
  
 <span data-ttu-id="5e31d-114">如果有下列情況，便繼承自 Windows Form 控制項：</span><span class="sxs-lookup"><span data-stu-id="5e31d-114">Inherit from a Windows Forms control if:</span></span>  
  
-   <span data-ttu-id="5e31d-115">大部分的所需功能已經與現有的 Windows Form 控制項相同。</span><span class="sxs-lookup"><span data-stu-id="5e31d-115">Most of the functionality you need is already identical to an existing Windows Forms control.</span></span>  
  
-   <span data-ttu-id="5e31d-116">您不需要自訂的圖形化介面，或是您想要為現有的控制項設計新的圖形化前端。</span><span class="sxs-lookup"><span data-stu-id="5e31d-116">You do not need a custom graphical interface, or you want to design a new graphical front end for an existing control.</span></span>  
  
## <a name="inheriting-from-the-usercontrol-class"></a><span data-ttu-id="5e31d-117">繼承自 UserControl 類別</span><span class="sxs-lookup"><span data-stu-id="5e31d-117">Inheriting from the UserControl Class</span></span>  
 <span data-ttu-id="5e31d-118">使用者控制項是封裝成通用容器的 Windows Form 控制項的集合。</span><span class="sxs-lookup"><span data-stu-id="5e31d-118">A user control is a collection of Windows Forms controls encapsulated into a common container.</span></span> <span data-ttu-id="5e31d-119">容器保存了與每個 Windows Form 控制項相關聯的所有固有功能，並可讓您選擇性地公開 (expose) 和繫結其屬性。</span><span class="sxs-lookup"><span data-stu-id="5e31d-119">The container holds all of the inherent functionality associated with each of the Windows Forms controls and allows you to selectively expose and bind their properties.</span></span> <span data-ttu-id="5e31d-120">使用者控制項的一個例子可能是建置用來顯示資料庫中客戶地址資料的控制項。</span><span class="sxs-lookup"><span data-stu-id="5e31d-120">An example of a user control might be a control built to display customer address data from a database.</span></span> <span data-ttu-id="5e31d-121">這個控制項可包括數個文字方塊來顯示每個欄位，以及按鈕控制項來巡覽記錄。</span><span class="sxs-lookup"><span data-stu-id="5e31d-121">This control would include several textboxes to display each field, and button controls to navigate through the records.</span></span> <span data-ttu-id="5e31d-122">資料繫結屬性可以選擇性地公開，而整個控制項可以封裝，並且在各應用程式之間重複使用。</span><span class="sxs-lookup"><span data-stu-id="5e31d-122">Data-binding properties could be selectively exposed, and the entire control could be packaged and reused from application to application.</span></span>  
  
 <span data-ttu-id="5e31d-123">如果有下列情況，便繼承自 <xref:System.Windows.Forms.UserControl> 類別：</span><span class="sxs-lookup"><span data-stu-id="5e31d-123">Inherit from the <xref:System.Windows.Forms.UserControl> class if:</span></span>  
  
-   <span data-ttu-id="5e31d-124">您想要將數個 Windows Form 控制項的功能結合成一個可重複使用的單位。</span><span class="sxs-lookup"><span data-stu-id="5e31d-124">You want to combine the functionality of several Windows Forms controls into a single reusable unit.</span></span>  
  
## <a name="inheriting-from-the-control-class"></a><span data-ttu-id="5e31d-125">繼承自 Control 類別</span><span class="sxs-lookup"><span data-stu-id="5e31d-125">Inheriting from the Control Class</span></span>  
 <span data-ttu-id="5e31d-126">建立控制項的另一個方法是藉由繼承自 <xref:System.Windows.Forms.Control>，實際地從頭建立一個控制項。</span><span class="sxs-lookup"><span data-stu-id="5e31d-126">Another way to create a control is to create one substantially from scratch by inheriting from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="5e31d-127"><xref:System.Windows.Forms.Control> 類別會提供控制項所需的所有基本功能 (例如事件)，但不提供控制項特有的功能或圖形化介面。</span><span class="sxs-lookup"><span data-stu-id="5e31d-127">The <xref:System.Windows.Forms.Control> class provides all of the basic functionality required by controls (for example, events), but no control-specific functionality or graphical interface.</span></span> <span data-ttu-id="5e31d-128">藉由繼承自 <xref:System.Windows.Forms.Control> 類別來建立控制項，比繼承自使用者控制項或現有的 Windows Form 控制項需要更多的思考和投入工作。</span><span class="sxs-lookup"><span data-stu-id="5e31d-128">Creating a control by inheriting from the <xref:System.Windows.Forms.Control> class requires a lot more thought and effort than inheriting from user control or an existing Windows Forms control.</span></span> <span data-ttu-id="5e31d-129">作者必須撰寫控制項 <xref:System.Windows.Forms.Control.OnPaint%2A> 事件程式碼，以及任何所需的功能特定程式碼。</span><span class="sxs-lookup"><span data-stu-id="5e31d-129">The author must write code for the <xref:System.Windows.Forms.Control.OnPaint%2A> event of the control, as well as any functionality specific code that is needed.</span></span> <span data-ttu-id="5e31d-130">不過這允許更多的彈性，且您可以自訂控制項，以符合您的確切需求。</span><span class="sxs-lookup"><span data-stu-id="5e31d-130">Greater flexibility is allowed, however, and you can custom tailor a control to suit your exact needs.</span></span> <span data-ttu-id="5e31d-131">自訂控制項的一個例子是複製類比時鐘外觀和動作的時鐘控制項。</span><span class="sxs-lookup"><span data-stu-id="5e31d-131">An example of a custom control is a clock control that duplicates the look and action of an analog clock.</span></span> <span data-ttu-id="5e31d-132">會叫用自訂繪製，讓時鐘指針移動以回應內部計時器元件的 <xref:System.Windows.Forms.Timer.Tick> 事件。</span><span class="sxs-lookup"><span data-stu-id="5e31d-132">Custom painting would be invoked to cause the hands of the clock to move in response to <xref:System.Windows.Forms.Timer.Tick> events from an internal timer component.</span></span>  
  
 <span data-ttu-id="5e31d-133">如果有下列情況，便繼承自 <xref:System.Windows.Forms.Control> 類別：</span><span class="sxs-lookup"><span data-stu-id="5e31d-133">Inherit from the <xref:System.Windows.Forms.Control> class if:</span></span>  
  
-   <span data-ttu-id="5e31d-134">您想要提供控制項的自訂圖形表示。</span><span class="sxs-lookup"><span data-stu-id="5e31d-134">You want to provide a custom graphical representation of your control.</span></span>  
  
-   <span data-ttu-id="5e31d-135">您需要實作無法透過標準控制項使用的自訂功能。</span><span class="sxs-lookup"><span data-stu-id="5e31d-135">You need to implement custom functionality that is not available through standard controls.</span></span>  
  
-   <span data-ttu-id="5e31d-136">[操作說明：在選擇工具箱項目對話方塊中顯示控制項](http://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="5e31d-136">[How to: Display a Control in the Choose Toolbox Items Dialog Box](http://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="5e31d-137">[逐步解說：使用 DesignerSerializationVisibilityAttribute 序列化標準類型的集合](http://msdn.microsoft.com/library/ms171731\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="5e31d-137">[Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/ms171731\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="5e31d-138">[逐步解說：使用 Visual C# 繼承自 Windows Forms 控制項](http://msdn.microsoft.com/en-us/library/5h0k2e6x\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="5e31d-138">[Walkthrough: Inheriting from a Windows Forms Control with Visual C#](http://msdn.microsoft.com/en-us/library/5h0k2e6x\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="5e31d-139">[操作說明：為控制項提供工具箱點陣圖](http://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="5e31d-139">[How to: Provide a Toolbox Bitmap for a Control](http://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="5e31d-140">[操作說明：繼承自現有的 Windows Forms 控制項](http://msdn.microsoft.com/library/7h62478z\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="5e31d-140">[How to: Inherit from Existing Windows Forms Controls](http://msdn.microsoft.com/library/7h62478z\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="5e31d-141">[逐步解說：在設計階段偵錯自訂的 Windows Forms 控制項](http://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="5e31d-141">[Walkthrough: Debugging Custom Windows Forms Controls at Design Time](http://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="5e31d-142">[如何：繼承自 Control 類別](http://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="5e31d-142">[How to: Inherit from the Control Class](http://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="5e31d-143">[操作說明：測試 UserControl 的執行階段行為](http://msdn.microsoft.com/library/ms171738\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="5e31d-143">[How to: Test the Run-Time Behavior of a UserControl](http://msdn.microsoft.com/library/ms171738\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="5e31d-144">[操作說明：在設計階段將控制項對齊表單邊緣](http://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="5e31d-144">[How to: Align a Control to the Edges of Forms at Design Time](http://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="5e31d-145">[操作說明：繼承自 UserControl 類別](http://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="5e31d-145">[How to: Inherit from the UserControl Class](http://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="5e31d-146">[如何：撰寫 Windows Forms 的控制項](http://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="5e31d-146">[How to: Author Controls for Windows Forms](http://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="5e31d-147">[如何：撰寫複合控制項](http://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="5e31d-147">[How to: Author Composite Controls](http://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="5e31d-148">[逐步解說：使用 Visual Basic 撰寫複合控制項](http://msdn.microsoft.com/library/c316f119\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="5e31d-148">[Walkthrough: Authoring a Composite Control with Visual Basic](http://msdn.microsoft.com/library/c316f119\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="5e31d-149">[逐步解說：使用 Visual C# 撰寫複合控制項](http://msdn.microsoft.com/en-us/library/a6h7e207\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="5e31d-149">[Walkthrough: Authoring a Composite Control with Visual C#](http://msdn.microsoft.com/en-us/library/a6h7e207\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="5e31d-150">[逐步解說：使用 Visual Basic 繼承自 Windows Forms 控制項](http://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="5e31d-150">[Walkthrough: Inheriting from a Windows Forms Control with Visual Basic](http://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="5e31d-151">[如何：建立採用設計階段功能的 Windows Forms 控制項](http://msdn.microsoft.com/library/307hck25\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="5e31d-151">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](http://msdn.microsoft.com/library/307hck25\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="5e31d-152">[如何：建立採用設計階段功能的 Windows Forms 控制項](http://msdn.microsoft.com/library/307hck25\(v=vs.120\))</span><span class="sxs-lookup"><span data-stu-id="5e31d-152">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](http://msdn.microsoft.com/library/307hck25\(v=vs.120\))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e31d-153">請參閱</span><span class="sxs-lookup"><span data-stu-id="5e31d-153">See Also</span></span>  
 [<span data-ttu-id="5e31d-154">操作說明：開發簡單的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="5e31d-154">How to: Develop a Simple Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)  
 [<span data-ttu-id="5e31d-155">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="5e31d-155">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
