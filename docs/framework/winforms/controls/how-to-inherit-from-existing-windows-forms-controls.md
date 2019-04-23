---
title: HOW TO：繼承現有的 Windows Forms 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
ms.openlocfilehash: 788addee7c024577d029626da4aeb86d0ca9076a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59300524"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a><span data-ttu-id="ecf5a-102">HOW TO：繼承現有的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="ecf5a-102">How to: Inherit from Existing Windows Forms Controls</span></span>
<span data-ttu-id="ecf5a-103">如果您想要擴充現有控制項的功能，您可以透過繼承來建立衍生自現有控制項的控制項。</span><span class="sxs-lookup"><span data-stu-id="ecf5a-103">If you want to extend the functionality of an existing control, you can create a control derived from an existing control through inheritance.</span></span> <span data-ttu-id="ecf5a-104">繼承自現有的控制項時，您會繼承該控制項的所有功能和視覺屬性。</span><span class="sxs-lookup"><span data-stu-id="ecf5a-104">When inheriting from an existing control, you inherit all of the functionality and visual properties of that control.</span></span> <span data-ttu-id="ecf5a-105">例如，如果您所建立的控制項繼承自<xref:System.Windows.Forms.Button>、 您的新控制項看起來和 act 完全像標準<xref:System.Windows.Forms.Button>控制項。</span><span class="sxs-lookup"><span data-stu-id="ecf5a-105">For example, if you were creating a control that inherited from <xref:System.Windows.Forms.Button>, your new control would look and act exactly like a standard <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="ecf5a-106">您就可以透過實作自訂方法和屬性，來擴充或修改新控制項的功能。</span><span class="sxs-lookup"><span data-stu-id="ecf5a-106">You could then extend or modify the functionality of your new control through the implementation of custom methods and properties.</span></span> <span data-ttu-id="ecf5a-107">在一些控制項中，您也可以變更繼承的控制項的視覺外觀藉由覆寫其<xref:System.Windows.Forms.Control.OnPaint%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="ecf5a-107">In some controls, you can also change the visual appearance of your inherited control by overriding its <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ecf5a-108">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="ecf5a-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="ecf5a-109">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="ecf5a-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="ecf5a-110">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="ecf5a-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-an-inherited-control"></a><span data-ttu-id="ecf5a-111">建立繼承的控制項</span><span class="sxs-lookup"><span data-stu-id="ecf5a-111">To create an inherited control</span></span>  
  
1. <span data-ttu-id="ecf5a-112">建立新的 [Windows Forms 應用程式] 專案。</span><span class="sxs-lookup"><span data-stu-id="ecf5a-112">Create a new **Windows Forms Application** project.</span></span>  
  
2. <span data-ttu-id="ecf5a-113">從 [專案] 功能表選擇 [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="ecf5a-113">From the **Project** menu, choose **Add New Item**.</span></span>  
  
     <span data-ttu-id="ecf5a-114">[新增項目] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="ecf5a-114">The **Add New Item** dialog box appears.</span></span>  
  
3. <span data-ttu-id="ecf5a-115">在 [新增項目] 對話方塊中，連按兩下 [自訂控制項]。</span><span class="sxs-lookup"><span data-stu-id="ecf5a-115">In the **Add New Item** dialog box, double-click **Custom Control**.</span></span>  
  
     <span data-ttu-id="ecf5a-116">新的自訂控制項會新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="ecf5a-116">A new custom control is added to your project.</span></span>  
  
4. <span data-ttu-id="ecf5a-117">如果您使用 Visual Basic，請在 [方案總管] 的頂端，按一下 [顯示所有檔案]。</span><span class="sxs-lookup"><span data-stu-id="ecf5a-117">If you using Visual Basic, at the top of **Solution Explorer**, click **Show All Files**.</span></span> <span data-ttu-id="ecf5a-118">展開 CustomControl1.vb，然後在程式碼編輯器中開啟 CustomControl1.Designer.vb。</span><span class="sxs-lookup"><span data-stu-id="ecf5a-118">Expand CustomControl1.vb and then open CustomControl1.Designer.vb in the Code Editor.</span></span>  
  
5. <span data-ttu-id="ecf5a-119">如果您使用 C#，請在程式碼編輯器中開啟 CustomControl1.cs。</span><span class="sxs-lookup"><span data-stu-id="ecf5a-119">If you are using C#, open CustomControl1.cs in the Code Editor.</span></span>  
  
6. <span data-ttu-id="ecf5a-120">找出類別宣告中，繼承自<xref:System.Windows.Forms.Control>。</span><span class="sxs-lookup"><span data-stu-id="ecf5a-120">Locate the class declaration, which inherits from <xref:System.Windows.Forms.Control>.</span></span>  
  
7. <span data-ttu-id="ecf5a-121">將基底類別變更為您想要繼承的控制項。</span><span class="sxs-lookup"><span data-stu-id="ecf5a-121">Change the base class to the control that you want to inherit from.</span></span>  
  
     <span data-ttu-id="ecf5a-122">例如，如果您想要繼承自<xref:System.Windows.Forms.Button>，將類別宣告變更如下：</span><span class="sxs-lookup"><span data-stu-id="ecf5a-122">For example, if you want to inherit from <xref:System.Windows.Forms.Button>, change the class declaration to the following:</span></span>  
  
    ```vb  
    Partial Class CustomControl1  
        Inherits System.Windows.Forms.Button  
    ```  
  
    ```csharp  
    public partial class CustomControl1 : System.Windows.Forms.Button  
    ```  
  
8. <span data-ttu-id="ecf5a-123">如果您使用 Visual Basic，請儲存並關閉 CustomControl1.Designer.vb。</span><span class="sxs-lookup"><span data-stu-id="ecf5a-123">If you are using Visual Basic, save and close CustomControl1.Designer.vb.</span></span> <span data-ttu-id="ecf5a-124">在程式碼編輯器中開啟 CustomControl1.vb。</span><span class="sxs-lookup"><span data-stu-id="ecf5a-124">Open CustomControl1.vb in the Code Editor.</span></span>  
  
9. <span data-ttu-id="ecf5a-125">實作您的控制項將併入的任何自訂方法或屬性。</span><span class="sxs-lookup"><span data-stu-id="ecf5a-125">Implement any custom methods or properties that your control will incorporate.</span></span>  
  
10. <span data-ttu-id="ecf5a-126">如果您想要修改您的控制項的圖形化外觀，覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="ecf5a-126">If you want to modify the graphical appearance of your control, override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ecf5a-127">覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>將不允許您修改所有控制項的外觀。</span><span class="sxs-lookup"><span data-stu-id="ecf5a-127">Overriding <xref:System.Windows.Forms.Control.OnPaint%2A> will not allow you to modify the appearance of all controls.</span></span> <span data-ttu-id="ecf5a-128">所有由 Windows 完成其繪製這些控制項 (例如<xref:System.Windows.Forms.TextBox>) 絕不會呼叫其<xref:System.Windows.Forms.Control.OnPaint%2A>方法，，因此永遠不會使用自訂程式碼。</span><span class="sxs-lookup"><span data-stu-id="ecf5a-128">Those controls that have all of their painting done by Windows (for example, <xref:System.Windows.Forms.TextBox>) never call their <xref:System.Windows.Forms.Control.OnPaint%2A> method, and thus will never use the custom code.</span></span> <span data-ttu-id="ecf5a-129">請參閱說明文件特定的控制項，您想要修改是否<xref:System.Windows.Forms.Control.OnPaint%2A>方法才有效。</span><span class="sxs-lookup"><span data-stu-id="ecf5a-129">Refer to the Help documentation for the particular control you want to modify to see if the <xref:System.Windows.Forms.Control.OnPaint%2A> method is available.</span></span> <span data-ttu-id="ecf5a-130">如需所有 Windows Forms 控制項的清單，請參閱[要在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="ecf5a-130">For a list of all the Windows Form Controls, see [Controls to Use on Windows Forms](controls-to-use-on-windows-forms.md).</span></span> <span data-ttu-id="ecf5a-131">如果控制項沒有<xref:System.Windows.Forms.Control.OnPaint%2A>列為成員方法，您無法變更其外觀藉由覆寫這個方法。</span><span class="sxs-lookup"><span data-stu-id="ecf5a-131">If a control does not have <xref:System.Windows.Forms.Control.OnPaint%2A> listed as a member method, you cannot alter its appearance by overriding this method.</span></span> <span data-ttu-id="ecf5a-132">如需自訂繪製的詳細資訊，請參閱[自訂控制項繪製和轉譯](custom-control-painting-and-rendering.md)。</span><span class="sxs-lookup"><span data-stu-id="ecf5a-132">For more information about custom painting, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>  
  
    ```vb  
    Protected Overrides Sub OnPaint(ByVal e As _  
       System.Windows.Forms.PaintEventArgs)  
       MyBase.OnPaint(e)  
       ' Insert code to do custom painting.   
       ' If you want to completely change the appearance of your control,  
       ' do not call MyBase.OnPaint(e).  
    End Sub  
    ```  
  
    ```csharp  
    protected override void OnPaint(PaintEventArgs pe)  
    {  
       base.OnPaint(pe);  
       // Insert code to do custom painting.  
       // If you want to completely change the appearance of your control,  
       // do not call base.OnPaint(pe).  
    }  
    ```  
  
11. <span data-ttu-id="ecf5a-133">儲存並測試您的控制項。</span><span class="sxs-lookup"><span data-stu-id="ecf5a-133">Save and test your control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecf5a-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ecf5a-134">See also</span></span>

- [<span data-ttu-id="ecf5a-135">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="ecf5a-135">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="ecf5a-136">如何：繼承自 Control 類別</span><span class="sxs-lookup"><span data-stu-id="ecf5a-136">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="ecf5a-137">如何：繼承自 UserControl 類別</span><span class="sxs-lookup"><span data-stu-id="ecf5a-137">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="ecf5a-138">如何：撰寫 Windows forms 的控制項</span><span class="sxs-lookup"><span data-stu-id="ecf5a-138">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="ecf5a-139">Visual Basic 中的繼承事件處理常式疑難排解</span><span class="sxs-lookup"><span data-stu-id="ecf5a-139">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="ecf5a-140">逐步解說：繼承自使用 Visual Basic 的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="ecf5a-140">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)
- [<span data-ttu-id="ecf5a-141">逐步解說：繼承自具有視覺效果的 Windows Forms 控制項C#</span><span class="sxs-lookup"><span data-stu-id="ecf5a-141">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
