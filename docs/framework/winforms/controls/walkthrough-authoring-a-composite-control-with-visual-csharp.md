---
title: 逐步解說：使用 Visual C# 撰寫複合控制項
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [C#]
- user controls [Windows Forms], creating with Visual C#
- UserControl class [Windows Forms], walkthroughs
- user controls [C#]
- custom controls [Windows Forms], creating
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
ms.openlocfilehash: 5f8384140b813400e106ad959684264304541c93
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "45990046"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-c"></a><span data-ttu-id="d03d3-102">逐步解說：使用 Visual C# 撰寫複合控制項</span><span class="sxs-lookup"><span data-stu-id="d03d3-102">Walkthrough: Authoring a Composite Control with Visual C#</span></span> #
<span data-ttu-id="d03d3-103">複合控制項提供可以建立及重複使用自訂圖形介面的方法。</span><span class="sxs-lookup"><span data-stu-id="d03d3-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="d03d3-104">複合控制項基本上是具有視覺表示的元件。</span><span class="sxs-lookup"><span data-stu-id="d03d3-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="d03d3-105">因此，它可能包含一或多個 Windows Forms 控制項、元件或程式碼區塊，可以藉由驗證使用者輸入、修改顯示屬性，或執行作者需要的其他工作來擴充功能。</span><span class="sxs-lookup"><span data-stu-id="d03d3-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="d03d3-106">複合控制項可以放在 Windows Forms 上，與其他控制項的方式相同。</span><span class="sxs-lookup"><span data-stu-id="d03d3-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="d03d3-107">在本逐步解說的第一個部分中，您可以建立簡單的複合控制項，稱為 `ctlClock`。</span><span class="sxs-lookup"><span data-stu-id="d03d3-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="d03d3-108">在逐步解說的第二個部分中，您透過繼承擴充 `ctlClock` 的功能。</span><span class="sxs-lookup"><span data-stu-id="d03d3-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d03d3-109">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="d03d3-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d03d3-110">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="d03d3-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d03d3-111">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="d03d3-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="d03d3-112">建立專案</span><span class="sxs-lookup"><span data-stu-id="d03d3-112">Creating the Project</span></span>  
 <span data-ttu-id="d03d3-113">當您建立新的專案時，您會指定其名稱以設定根命名空間、組件名稱和專案名稱，並且確定預設元件將會在正確的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="d03d3-113">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="d03d3-114">建立 ctlClockLib 控制項程式庫和 ctlClock 控制項</span><span class="sxs-lookup"><span data-stu-id="d03d3-114">To create the ctlClockLib control library and the ctlClock control</span></span>  
  
1.  <span data-ttu-id="d03d3-115">在 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]，開啟 [新增專案] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d03d3-115">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="d03d3-116">從 Visual C# 專案的清單中，選取**Windows Form 控制項程式庫**專案範本中，輸入`ctlClockLib`中**名稱**方塊，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d03d3-116">From the list of Visual C# projects, select the **Windows Forms Control Library** project template, type `ctlClockLib` in the **Name** box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="d03d3-117">專案名稱，`ctlClockLib`，預設也會指派給根命名空間。</span><span class="sxs-lookup"><span data-stu-id="d03d3-117">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="d03d3-118">根命名空間是用來限定組件中的元件名稱。</span><span class="sxs-lookup"><span data-stu-id="d03d3-118">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="d03d3-119">例如，如果兩個組件提供元件，名為 `ctlClock`，您可以使用 `ctlClockLib.ctlClock.` 指定您的 `ctlClock` 元件</span><span class="sxs-lookup"><span data-stu-id="d03d3-119">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>  
  
3.  <span data-ttu-id="d03d3-120">以滑鼠右鍵按一下 [方案總管] 中的 [UserControl1.cs]，然後按一下 [重新命名]。</span><span class="sxs-lookup"><span data-stu-id="d03d3-120">In Solution Explorer, right-click **UserControl1.cs**, and then click **Rename**.</span></span> <span data-ttu-id="d03d3-121">將檔案名稱變更為 `ctlClock.cs`。</span><span class="sxs-lookup"><span data-stu-id="d03d3-121">Change the file name to `ctlClock.cs`.</span></span> <span data-ttu-id="d03d3-122">當系統詢問您是否要重新命名程式碼元素 "UserControl1" 的所有參考時，按一下 [是]按鈕。</span><span class="sxs-lookup"><span data-stu-id="d03d3-122">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d03d3-123">根據預設，複合控制項是繼承自<xref:System.Windows.Forms.UserControl>系統所提供的類別。</span><span class="sxs-lookup"><span data-stu-id="d03d3-123">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="d03d3-124"><xref:System.Windows.Forms.UserControl>類別提供所有複合控制項，所需的功能，並會實作標準方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="d03d3-124">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>  
  
4.  <span data-ttu-id="d03d3-125">在 [檔案] 功能表上按一下 [全部儲存] 以儲存專案。</span><span class="sxs-lookup"><span data-stu-id="d03d3-125">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="d03d3-126">將 Windows 控制項和元件新增至複合控制項</span><span class="sxs-lookup"><span data-stu-id="d03d3-126">Adding Windows Controls and Components to the Composite Control</span></span>  
 <span data-ttu-id="d03d3-127">視覺化介面是複合控制項不可或缺的一部分。</span><span class="sxs-lookup"><span data-stu-id="d03d3-127">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="d03d3-128">這個視覺化介面是藉由將一或多個 Windows 控制項新增至設計工具介面來實作。</span><span class="sxs-lookup"><span data-stu-id="d03d3-128">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="d03d3-129">在下列示範中，您將 Windows 控制項合併到您的複合控制項，並且撰寫程式碼來實作功能。</span><span class="sxs-lookup"><span data-stu-id="d03d3-129">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="d03d3-130">將標籤和計時器新增至複合控制項</span><span class="sxs-lookup"><span data-stu-id="d03d3-130">To add a Label and a Timer to your composite control</span></span>  
  
1.  <span data-ttu-id="d03d3-131">在 [方案總管] 中，以滑鼠右鍵按一下 [ctlClock.cs]，然後按一下 [檢視表設計工具]。</span><span class="sxs-lookup"><span data-stu-id="d03d3-131">In Solution Explorer, right-click **ctlClock.cs**, and then click **View Designer**.</span></span>  
  
2.  <span data-ttu-id="d03d3-132">在 [工具箱] 中展開 [通用控制項] 節點，然後再按兩下 [標籤]。</span><span class="sxs-lookup"><span data-stu-id="d03d3-132">In the **Toolbox**, expand the **Common Controls** node, and then double-click **Label**.</span></span>  
  
     <span data-ttu-id="d03d3-133">A<xref:System.Windows.Forms.Label>控制項，名為`label1`新增至您的控制項設計工具介面上。</span><span class="sxs-lookup"><span data-stu-id="d03d3-133">A <xref:System.Windows.Forms.Label> control named `label1` is added to your control on the designer surface.</span></span>  
  
3.  <span data-ttu-id="d03d3-134">在設計工具中，按一下 [label1]。</span><span class="sxs-lookup"><span data-stu-id="d03d3-134">In the designer, click **label1**.</span></span> <span data-ttu-id="d03d3-135">在 [屬性] 視窗中設定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="d03d3-135">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="d03d3-136">屬性</span><span class="sxs-lookup"><span data-stu-id="d03d3-136">Property</span></span>|<span data-ttu-id="d03d3-137">變更為</span><span class="sxs-lookup"><span data-stu-id="d03d3-137">Change to</span></span>|  
    |--------------|---------------|  
    |<span data-ttu-id="d03d3-138">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d03d3-138">**Name**</span></span>|`lblDisplay`|  
    |<span data-ttu-id="d03d3-139">**Text**</span><span class="sxs-lookup"><span data-stu-id="d03d3-139">**Text**</span></span>|`(blank space)`|  
    |<span data-ttu-id="d03d3-140">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="d03d3-140">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="d03d3-141">**Font.Size**</span><span class="sxs-lookup"><span data-stu-id="d03d3-141">**Font.Size**</span></span>|`14`|  
  
4.  <span data-ttu-id="d03d3-142">在 [工具箱] 中展開 [元件] 節點，然後再按兩下 [計時器]。</span><span class="sxs-lookup"><span data-stu-id="d03d3-142">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>  
  
     <span data-ttu-id="d03d3-143">因為<xref:System.Windows.Forms.Timer>是元件，它有在執行階段沒有視覺表示法。</span><span class="sxs-lookup"><span data-stu-id="d03d3-143">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="d03d3-144">因此，它不會與控制項一起出現在設計工具介面上，而是會出現在 [元件設計工具] 中 (位於設計工具介面底部的系統匣)。</span><span class="sxs-lookup"><span data-stu-id="d03d3-144">Therefore, it does not appear with the controls on the designer surface, but rather in the **Component Designer** (a tray at the bottom of the designer surface).</span></span>  
  
5.  <span data-ttu-id="d03d3-145">在**Component Designer**，按一下**timer1**，然後將<xref:System.Windows.Forms.Timer.Interval%2A>屬性設`1000`和<xref:System.Windows.Forms.Timer.Enabled%2A>屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="d03d3-145">In the **Component Designer**, click **timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="d03d3-146"><xref:System.Windows.Forms.Timer.Interval%2A>屬性控制的頻率<xref:System.Windows.Forms.Timer>元件刻度。</span><span class="sxs-lookup"><span data-stu-id="d03d3-146">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the <xref:System.Windows.Forms.Timer> component ticks.</span></span> <span data-ttu-id="d03d3-147">每次 `timer1` 走動時，它會執行 `timer1_Tick` 事件中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d03d3-147">Each time `timer1` ticks, it runs the code in the `timer1_Tick` event.</span></span> <span data-ttu-id="d03d3-148">間隔代表刻度之間的毫秒數。</span><span class="sxs-lookup"><span data-stu-id="d03d3-148">The interval represents the number of milliseconds between ticks.</span></span>  
  
6.  <span data-ttu-id="d03d3-149">在 [元件設計工具] 中，按兩下 [timer1] 以前往 `ctlClock` 的 `timer1_Tick` 事件。</span><span class="sxs-lookup"><span data-stu-id="d03d3-149">In the **Component Designer**, double-click **timer1** to go to the `timer1_Tick` event for `ctlClock`.</span></span>  
  
7.  <span data-ttu-id="d03d3-150">修改程式碼，使它類似下列程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="d03d3-150">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="d03d3-151">請確定將存取修飾詞從 `private` 變更為 `protected`。</span><span class="sxs-lookup"><span data-stu-id="d03d3-151">Be sure to change the access modifier from `private` to `protected`.</span></span>  
  
    ```csharp  
    protected void timer1_Tick(object sender, System.EventArgs e)  
    {  
        // Causes the label to display the current time.  
        lblDisplay.Text = DateTime.Now.ToLongTimeString();   
    }  
    ```  
  
     <span data-ttu-id="d03d3-152">此程式碼會造成目前時間在 `lblDisplay` 中顯示。</span><span class="sxs-lookup"><span data-stu-id="d03d3-152">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="d03d3-153">因為 `timer1` 的間隔設為 `1000`，每一千毫秒便會發生此事件，因此每秒會更新目前時間。</span><span class="sxs-lookup"><span data-stu-id="d03d3-153">Because the interval of `timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>  
  
8.  <span data-ttu-id="d03d3-154">修改方法為可使用 `virtual`關鍵字覆寫。</span><span class="sxs-lookup"><span data-stu-id="d03d3-154">Modify the method to be overridable with the `virtual` keyword.</span></span> <span data-ttu-id="d03d3-155">如需詳細資訊，請參閱以下的「從使用者控制項繼承」一節。</span><span class="sxs-lookup"><span data-stu-id="d03d3-155">For more information, see the  "Inheriting from a User Control" section below.</span></span>  
  
    ```csharp  
    protected virtual void timer1_Tick(object sender, System.EventArgs e)  
    ```  
  
9. <span data-ttu-id="d03d3-156">在 [檔案] 功能表上按一下 [全部儲存] 以儲存專案。</span><span class="sxs-lookup"><span data-stu-id="d03d3-156">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-properties-to-the-composite-control"></a><span data-ttu-id="d03d3-157">將屬性新增至複合控制項</span><span class="sxs-lookup"><span data-stu-id="d03d3-157">Adding Properties to the Composite Control</span></span>  
 <span data-ttu-id="d03d3-158">您的時鐘控制項現在會封裝<xref:System.Windows.Forms.Label>控制項和<xref:System.Windows.Forms.Timer>元件，各有其自己的固有的屬性集。</span><span class="sxs-lookup"><span data-stu-id="d03d3-158">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="d03d3-159">雖然這些控制項的個別屬性無法供控制項的後續使用者存取，但是您可以建立並公開自訂屬性，方法是撰寫適當的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="d03d3-159">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="d03d3-160">在下列程序中，您會將屬性新增至控制項，讓使用者變更背景與文字的色彩。</span><span class="sxs-lookup"><span data-stu-id="d03d3-160">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>  
  
#### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="d03d3-161">若要將屬性新增至複合控制項</span><span class="sxs-lookup"><span data-stu-id="d03d3-161">To add a property to your composite control</span></span>  
  
1.  <span data-ttu-id="d03d3-162">在 [方案總管] 中，以滑鼠右鍵按一下 [ctlClock.cs]，然後按一下 [檢視程式碼]。</span><span class="sxs-lookup"><span data-stu-id="d03d3-162">In Solution Explorer, right-click **ctlClock.cs**, and then click **View Code**.</span></span>  
  
     <span data-ttu-id="d03d3-163">控制項的 [程式碼編輯器] 隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="d03d3-163">The **Code Editor** for your control opens.</span></span>  
  
2.  <span data-ttu-id="d03d3-164">尋找 `public partial class ctlClock` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="d03d3-164">Locate the `public partial class ctlClock` statement.</span></span> <span data-ttu-id="d03d3-165">在左大括號 (`{)` 底下，輸入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="d03d3-165">Beneath the opening brace (`{)`, type the following code.</span></span>  
  
    ```csharp  
    private Color colFColor;  
    private Color colBColor;  
    ```  
  
     <span data-ttu-id="d03d3-166">這些陳述式會建立私用變數，您將用來儲存您即將建立之屬性的值。</span><span class="sxs-lookup"><span data-stu-id="d03d3-166">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>  
  
3.  <span data-ttu-id="d03d3-167">在 步驟 2 的變數宣告底下輸入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="d03d3-167">Type the following code beneath the variable declarations from step 2.</span></span>  
  
    ```csharp  
    // Declares the name and type of the property.  
    public Color ClockBackColor  
    {  
        // Retrieves the value of the private variable colBColor.  
        get  
        {  
            return colBColor;  
        }  
        // Stores the selected value in the private variable colBColor, and   
        // updates the background color of the label control lblDisplay.  
        set  
        {  
            colBColor = value;  
            lblDisplay.BackColor = colBColor;     
        }  
    }  
    // Provides a similar set of instructions for the foreground color.  
    public Color ClockForeColor  
    {  
        get  
        {  
            return colFColor;  
        }  
        set  
        {  
            colFColor = value;  
            lblDisplay.ForeColor = colFColor;  
        }  
    }  
    ```  
  
     <span data-ttu-id="d03d3-168">上述程式碼會製作兩個自訂屬性，`ClockForeColor` 和 `ClockBackColor`，以供此控制項的後續使用者使用。</span><span class="sxs-lookup"><span data-stu-id="d03d3-168">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control.</span></span> <span data-ttu-id="d03d3-169">`get` 和 `set` 陳述式提供屬性值的儲存和擷取，以及用來實作適合該屬性之功能的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d03d3-169">The `get` and `set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>  
  
4.  <span data-ttu-id="d03d3-170">在 [檔案] 功能表上按一下 [全部儲存] 以儲存專案。</span><span class="sxs-lookup"><span data-stu-id="d03d3-170">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="testing-the-control"></a><span data-ttu-id="d03d3-171">測試控制項</span><span class="sxs-lookup"><span data-stu-id="d03d3-171">Testing the Control</span></span>  
 <span data-ttu-id="d03d3-172">控制項不是獨立應用程式；它們必須裝載在容器中。</span><span class="sxs-lookup"><span data-stu-id="d03d3-172">Controls are not stand-alone applications; they must be hosted in a container.</span></span> <span data-ttu-id="d03d3-173">測試控制項的執行階段行為，並且使用 **UserControl 測試容器**執行其屬性。</span><span class="sxs-lookup"><span data-stu-id="d03d3-173">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="d03d3-174">如需詳細資訊，請參閱[如何：測試 UserControl 的執行階段行為](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)。</span><span class="sxs-lookup"><span data-stu-id="d03d3-174">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
#### <a name="to-test-your-control"></a><span data-ttu-id="d03d3-175">若要測試控制項</span><span class="sxs-lookup"><span data-stu-id="d03d3-175">To test your control</span></span>  
  
1.  <span data-ttu-id="d03d3-176">按下 F5 鍵以建置專案，並且在 **UserControl 測試容器**中執行您的控制項。</span><span class="sxs-lookup"><span data-stu-id="d03d3-176">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>  
  
2.  <span data-ttu-id="d03d3-177">在測試容器的屬性方格中，尋找 `ClockBackColor` 屬性，然後選取屬性以顯示色彩調色盤。</span><span class="sxs-lookup"><span data-stu-id="d03d3-177">In the test container's property grid, locate the `ClockBackColor` property, and then select the property to display the color palette.</span></span>  
  
3.  <span data-ttu-id="d03d3-178">按一下它以選擇色彩。</span><span class="sxs-lookup"><span data-stu-id="d03d3-178">Choose a color by clicking it.</span></span>  
  
     <span data-ttu-id="d03d3-179">控制項的背景色彩會變更為您所選取的色彩。</span><span class="sxs-lookup"><span data-stu-id="d03d3-179">The background color of your control changes to the color you selected.</span></span>  
  
4.  <span data-ttu-id="d03d3-180">使用類似的一連串事件，確認 `ClockForeColor` 屬性是否如預期運作。</span><span class="sxs-lookup"><span data-stu-id="d03d3-180">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>  
  
     <span data-ttu-id="d03d3-181">在本節和先前的章節中，您已經知道元件和 Windows 控制項如何與程式碼合併並且封裝，以複合控制項的形式提供自訂功能。</span><span class="sxs-lookup"><span data-stu-id="d03d3-181">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="d03d3-182">您已經了解如何在您的複合控制項中公開屬性，以及如何在完成之後測試您的控制項。</span><span class="sxs-lookup"><span data-stu-id="d03d3-182">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="d03d3-183">在下一節中，您將學習如何使用 `ctlClock` 做為基底，建構繼承的複合控制項。</span><span class="sxs-lookup"><span data-stu-id="d03d3-183">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>  
  
## <a name="inheriting-from-a-composite-control"></a><span data-ttu-id="d03d3-184">繼承自複合控制項</span><span class="sxs-lookup"><span data-stu-id="d03d3-184">Inheriting from a Composite Control</span></span>  
 <span data-ttu-id="d03d3-185">在先前章節中，您了解如何將 Windows 控制項、元件和程式碼合併成可重複使用的複合控制項。</span><span class="sxs-lookup"><span data-stu-id="d03d3-185">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="d03d3-186">複合控制項現在可以做為建置其他控制項的基底。</span><span class="sxs-lookup"><span data-stu-id="d03d3-186">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="d03d3-187">從基底類別衍生類別的處理序稱為「繼承」。</span><span class="sxs-lookup"><span data-stu-id="d03d3-187">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="d03d3-188">在本節中，您將建立稱為 `ctlAlarmClock` 的複合控制項。</span><span class="sxs-lookup"><span data-stu-id="d03d3-188">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="d03d3-189">這個控制項將會從其父控制項 (`ctlClock`) 衍生。</span><span class="sxs-lookup"><span data-stu-id="d03d3-189">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="d03d3-190">您將學習藉由覆寫父方法並且新增新方法和屬性，來擴充 `ctlClock` 的功能。</span><span class="sxs-lookup"><span data-stu-id="d03d3-190">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>  
  
 <span data-ttu-id="d03d3-191">建立繼承的控制項的第一個步驟是從其父代衍生。</span><span class="sxs-lookup"><span data-stu-id="d03d3-191">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="d03d3-192">這個動作會建立新的控制項，其中具有父控制項的所有屬性、方法和圖形特性，但是也可以做為基底，以新增新的或修改功能。</span><span class="sxs-lookup"><span data-stu-id="d03d3-192">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>  
  
#### <a name="to-create-the-inherited-control"></a><span data-ttu-id="d03d3-193">若要建立繼承的控制項</span><span class="sxs-lookup"><span data-stu-id="d03d3-193">To create the inherited control</span></span>  
  
1.  <span data-ttu-id="d03d3-194">在 [方案總管] 中，以滑鼠右鍵按一下 [ctlClockLib]，指向 [新增]，然後按一下 [使用者控制項]。</span><span class="sxs-lookup"><span data-stu-id="d03d3-194">In Solution Explorer, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>  
  
     <span data-ttu-id="d03d3-195">[新增項目] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="d03d3-195">The **Add New Item** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="d03d3-196">選取**繼承的使用者控制項**範本。</span><span class="sxs-lookup"><span data-stu-id="d03d3-196">Select the **Inherited User Control** template.</span></span>  
  
3.  <span data-ttu-id="d03d3-197">在 [名稱] 方塊中，輸入 `ctlAlarmClock.cs` 然後按一下 [新增]。</span><span class="sxs-lookup"><span data-stu-id="d03d3-197">In the **Name** box, type `ctlAlarmClock.cs`, and then click **Add**.</span></span>  
  
     <span data-ttu-id="d03d3-198">[繼承選取器] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="d03d3-198">The **Inheritance Picker** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="d03d3-199">在 [元件名稱] 底下，按兩下 [ctlClock]。</span><span class="sxs-lookup"><span data-stu-id="d03d3-199">Under **Component Name**, double-click **ctlClock**.</span></span>  
  
5.  <span data-ttu-id="d03d3-200">在 [方案總管] 中，瀏覽目前的專案。</span><span class="sxs-lookup"><span data-stu-id="d03d3-200">In Solution Explorer, browse through the current projects.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d03d3-201">名為 **ctlAlarmClock.cs** 的檔案已新增至目前的專案。</span><span class="sxs-lookup"><span data-stu-id="d03d3-201">A file called **ctlAlarmClock.cs** has been added to the current project.</span></span>  
  
### <a name="adding-the-alarm-properties"></a><span data-ttu-id="d03d3-202">新增警示屬性</span><span class="sxs-lookup"><span data-stu-id="d03d3-202">Adding the Alarm Properties</span></span>  
 <span data-ttu-id="d03d3-203">屬性會以新增至複合控制項的相同方式，新增至繼承的控制項。</span><span class="sxs-lookup"><span data-stu-id="d03d3-203">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="d03d3-204">您現在會使用屬性宣告語法將兩個屬性新增至您的控制項︰`AlarmTime`，它將會儲存警示停止之日期和時間的值，以及 `AlarmSet`，它將會指示是否已設定警示。</span><span class="sxs-lookup"><span data-stu-id="d03d3-204">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>  
  
##### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="d03d3-205">若要將屬性新增至複合控制項</span><span class="sxs-lookup"><span data-stu-id="d03d3-205">To add properties to your composite control</span></span>  
  
1.  <span data-ttu-id="d03d3-206">在 [方案總管] 中，以滑鼠右鍵按一下 [ctlAlarmClock]，然後按一下 [檢視程式碼]。</span><span class="sxs-lookup"><span data-stu-id="d03d3-206">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="d03d3-207">尋找 `public class` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="d03d3-207">Locate the `public class` statement.</span></span> <span data-ttu-id="d03d3-208">請注意，您的控制項繼承自`ctlClockLib.ctlClock`。</span><span class="sxs-lookup"><span data-stu-id="d03d3-208">Note that your control inherits from `ctlClockLib.ctlClock`.</span></span> <span data-ttu-id="d03d3-209">在左大括號 (`{)` 陳述式底下，輸入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="d03d3-209">Beneath the opening brace (`{)` statement, type the following code.</span></span>  
  
    ```csharp  
    private DateTime dteAlarmTime;  
    private bool blnAlarmSet;  
    // These properties will be declared as public to allow future   
    // developers to access them.  
    public DateTime AlarmTime  
    {  
        get  
        {  
            return dteAlarmTime;  
        }  
        set  
        {  
            dteAlarmTime = value;  
        }  
    }  
    public bool AlarmSet  
    {  
        get  
        {  
            return blnAlarmSet;  
        }  
        set  
        {  
            blnAlarmSet = value;  
        }  
    }  
    ```  
  
### <a name="adding-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="d03d3-210">新增至控制項的圖形化介面</span><span class="sxs-lookup"><span data-stu-id="d03d3-210">Adding to the Graphical Interface of the Control</span></span>  
 <span data-ttu-id="d03d3-211">繼承的控制項具有視覺化介面，與它所繼承的控制項相同。</span><span class="sxs-lookup"><span data-stu-id="d03d3-211">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="d03d3-212">它擁有與其父控制項相同的組成控制項，但是無法使用組成控制項的屬性，除非特別公開。</span><span class="sxs-lookup"><span data-stu-id="d03d3-212">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="d03d3-213">您可以使用新增至任何複合控制項的相同方式，新增至繼承的複合控制項的圖形化介面。</span><span class="sxs-lookup"><span data-stu-id="d03d3-213">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="d03d3-214">若要繼續新增至警示時鐘的視覺化介面，您要新增標籤控制項，該控制項會在警示響起時閃爍。</span><span class="sxs-lookup"><span data-stu-id="d03d3-214">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>  
  
##### <a name="to-add-the-label-control"></a><span data-ttu-id="d03d3-215">若要新增標籤控制項</span><span class="sxs-lookup"><span data-stu-id="d03d3-215">To add the label control</span></span>  
  
1.  <span data-ttu-id="d03d3-216">在 [方案總管] 中，以滑鼠右鍵按一下 [ctlAlarmClock]，然後按一下 [檢視表設計工具]。</span><span class="sxs-lookup"><span data-stu-id="d03d3-216">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Designer**.</span></span>  
  
     <span data-ttu-id="d03d3-217">`ctlAlarmClock` 的設計工具隨即在主視窗中開啟。</span><span class="sxs-lookup"><span data-stu-id="d03d3-217">The designer for `ctlAlarmClock` opens in the main window.</span></span>  
  
2.  <span data-ttu-id="d03d3-218">按一下控制項的顯示部分，並檢視 [屬性] 視窗。</span><span class="sxs-lookup"><span data-stu-id="d03d3-218">Click the display portion of the control, and view the Properties window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d03d3-219">所有屬性顯示時，它們會以灰色顯示。</span><span class="sxs-lookup"><span data-stu-id="d03d3-219">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="d03d3-220">這表示這些屬性是 `lblDisplay` 的原生屬性，而且無法修改或在 [屬性] 視窗中存取。</span><span class="sxs-lookup"><span data-stu-id="d03d3-220">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="d03d3-221">根據預設，包含在複合控制項中的控制項是 `private`，而且其屬性無法使用任何方法存取。</span><span class="sxs-lookup"><span data-stu-id="d03d3-221">By default, controls contained in a composite control are `private`, and their properties are not accessible by any means.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d03d3-222">如果您想要讓複合控制項的後續使用者可以存取其內部控制項，請將它們宣告為 `public` 或 `protected`。</span><span class="sxs-lookup"><span data-stu-id="d03d3-222">If you want subsequent users of your composite control to have access to its internal controls, declare them as `public` or `protected`.</span></span> <span data-ttu-id="d03d3-223">這可讓您使用適當的程式碼，設定及修改包含在複合控制項中的控制項屬性。</span><span class="sxs-lookup"><span data-stu-id="d03d3-223">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>  
  
3.  <span data-ttu-id="d03d3-224">新增<xref:System.Windows.Forms.Label>至複合控制項的控制項。</span><span class="sxs-lookup"><span data-stu-id="d03d3-224">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>  
  
4.  <span data-ttu-id="d03d3-225">使用滑鼠，拖曳<xref:System.Windows.Forms.Label>正下方的顯示方塊中的控制項。</span><span class="sxs-lookup"><span data-stu-id="d03d3-225">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="d03d3-226">在 [屬性] 視窗中設定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="d03d3-226">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="d03d3-227">屬性</span><span class="sxs-lookup"><span data-stu-id="d03d3-227">Property</span></span>|<span data-ttu-id="d03d3-228">設定</span><span class="sxs-lookup"><span data-stu-id="d03d3-228">Setting</span></span>|  
    |--------------|-------------|  
    |<span data-ttu-id="d03d3-229">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d03d3-229">**Name**</span></span>|`lblAlarm`|  
    |<span data-ttu-id="d03d3-230">**Text**</span><span class="sxs-lookup"><span data-stu-id="d03d3-230">**Text**</span></span>|<span data-ttu-id="d03d3-231">**Alarm!**</span><span class="sxs-lookup"><span data-stu-id="d03d3-231">**Alarm!**</span></span>|  
    |<span data-ttu-id="d03d3-232">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="d03d3-232">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="d03d3-233">**可見**</span><span class="sxs-lookup"><span data-stu-id="d03d3-233">**Visible**</span></span>|`false`|  
  
### <a name="adding-the-alarm-functionality"></a><span data-ttu-id="d03d3-234">新增警示功能</span><span class="sxs-lookup"><span data-stu-id="d03d3-234">Adding the Alarm Functionality</span></span>  
 <span data-ttu-id="d03d3-235">在先前的程序中，您新增屬性和控制項，在您的複合控制項中啟用警示功能。</span><span class="sxs-lookup"><span data-stu-id="d03d3-235">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="d03d3-236">在此程序中，您將會新增程式碼以比較目前時間與警示時間，如果它們相同，則讓警示閃爍。</span><span class="sxs-lookup"><span data-stu-id="d03d3-236">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to flash an alarm.</span></span> <span data-ttu-id="d03d3-237">藉由覆寫 `ctlClock` 的 `timer1_Tick` 方法，並且將額外程式碼新增至其中，您就可以擴充 `ctlAlarmClock` 的功能，同時保留 `ctlClock` 的所有固有功能。</span><span class="sxs-lookup"><span data-stu-id="d03d3-237">By overriding the `timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a><span data-ttu-id="d03d3-238">若要覆寫 ctlClock 的 timer1_Tick 方法</span><span class="sxs-lookup"><span data-stu-id="d03d3-238">To override the timer1_Tick method of ctlClock</span></span>  
  
1.  <span data-ttu-id="d03d3-239">在 [程式碼編輯器] 中，尋找 `private bool blnAlarmSet;` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="d03d3-239">In the **Code Editor**, locate the `private bool blnAlarmSet;` statement.</span></span> <span data-ttu-id="d03d3-240">緊接著在其下新增下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="d03d3-240">Immediately beneath it, add the following statement.</span></span>  
  
    ```csharp  
    private bool blnColorTicker;  
    ```  
  
2.  <span data-ttu-id="d03d3-241">在 [程式碼編輯器] 中，在類別結尾尋找右大括號 (`})`。</span><span class="sxs-lookup"><span data-stu-id="d03d3-241">In the **Code Editor**, locate the closing brace (`})` at the end of the class.</span></span> <span data-ttu-id="d03d3-242">緊接在大括號之前，新增下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="d03d3-242">Just before the brace, add the following code.</span></span>  
  
    ```csharp  
    protected override void timer1_Tick(object sender, System.EventArgs e)  
    {  
        // Calls the Timer1_Tick method of ctlClock.  
        base.timer1_Tick(sender, e);  
        // Checks to see if the alarm is set.  
        if (AlarmSet == false)  
            return;  
        else  
            // If the date, hour, and minute of the alarm time are the same as  
            // the current time, flash an alarm.   
        {  
            if (AlarmTime.Date == DateTime.Now.Date && AlarmTime.Hour ==   
                DateTime.Now.Hour && AlarmTime.Minute == DateTime.Now.Minute)  
            {  
                // Sets lblAlarmVisible to true, and changes the background color based on  
                // the value of blnColorTicker. The background color of the label   
                // will flash once per tick of the clock.  
                lblAlarm.Visible = true;  
                if (blnColorTicker == false)   
                {  
                    lblAlarm.BackColor = Color.Red;  
                    blnColorTicker = true;  
                }  
                else  
                {  
                    lblAlarm.BackColor = Color.Blue;  
                    blnColorTicker = false;  
                }  
            }  
            else  
            {  
                // Once the alarm has sounded for a minute, the label is made   
                // invisible again.  
                lblAlarm.Visible = false;  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="d03d3-243">新增這個程式碼會完成幾項工作。</span><span class="sxs-lookup"><span data-stu-id="d03d3-243">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="d03d3-244">`override` 陳述式會指示控制項使用這個方法來取代繼承自基底控制項的方法。</span><span class="sxs-lookup"><span data-stu-id="d03d3-244">The `override` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="d03d3-245">呼叫這個方法時，它會呼叫它藉由叫用 `base.timer1_Tick` 陳述式覆寫的方法，確保併入原始控制項的所有功能在此控制項中重現。</span><span class="sxs-lookup"><span data-stu-id="d03d3-245">When this method is called, it calls the method it overrides by invoking the `base.timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="d03d3-246">接著，它會執行其他程式碼以併入警示功能。</span><span class="sxs-lookup"><span data-stu-id="d03d3-246">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="d03d3-247">發生警示時，閃爍標籤控制項就會出現。</span><span class="sxs-lookup"><span data-stu-id="d03d3-247">A flashing label control will appear when the alarm occurs.</span></span>  
  
     <span data-ttu-id="d03d3-248">警示時鐘控制項已接近完成。</span><span class="sxs-lookup"><span data-stu-id="d03d3-248">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="d03d3-249">唯一剩餘的事項是實作將它關閉的方式。</span><span class="sxs-lookup"><span data-stu-id="d03d3-249">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="d03d3-250">若要這樣做，您要將程式碼新增至 `lblAlarm_Click` 方法。</span><span class="sxs-lookup"><span data-stu-id="d03d3-250">To do this, you will add code to the `lblAlarm_Click` method.</span></span>  
  
##### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="d03d3-251">若要實作關閉方法</span><span class="sxs-lookup"><span data-stu-id="d03d3-251">To implement the shutoff method</span></span>  
  
1.  <span data-ttu-id="d03d3-252">在 [方案總管] 中，以滑鼠右鍵按一下 [ctlAlarmClock.cs]，然後按一下 [檢視表設計工具]。</span><span class="sxs-lookup"><span data-stu-id="d03d3-252">In Solution Explorer, right-click **ctlAlarmClock.cs**, and then click **View Designer**.</span></span>  
  
     <span data-ttu-id="d03d3-253">設計工具隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="d03d3-253">The designer opens.</span></span>  
  
2.  <span data-ttu-id="d03d3-254">將按鈕新增至控制項。</span><span class="sxs-lookup"><span data-stu-id="d03d3-254">Add a button to the control.</span></span> <span data-ttu-id="d03d3-255">將按鈕的屬性設定如下。</span><span class="sxs-lookup"><span data-stu-id="d03d3-255">Set the properties of the button as follows.</span></span>  
  
    |<span data-ttu-id="d03d3-256">屬性</span><span class="sxs-lookup"><span data-stu-id="d03d3-256">Property</span></span>|<span data-ttu-id="d03d3-257">值</span><span class="sxs-lookup"><span data-stu-id="d03d3-257">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="d03d3-258">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d03d3-258">**Name**</span></span>|`btnAlarmOff`|  
    |<span data-ttu-id="d03d3-259">**Text**</span><span class="sxs-lookup"><span data-stu-id="d03d3-259">**Text**</span></span>|<span data-ttu-id="d03d3-260">**停用警示**</span><span class="sxs-lookup"><span data-stu-id="d03d3-260">**Disable Alarm**</span></span>|  
  
3.  <span data-ttu-id="d03d3-261">在設計工具中，按兩下 [btnAlarmOff]。</span><span class="sxs-lookup"><span data-stu-id="d03d3-261">In the designer, double-click **btnAlarmOff**.</span></span>  
  
     <span data-ttu-id="d03d3-262">[程式碼編輯器] 隨即開啟至 `private void btnAlarmOff_Click` 行。</span><span class="sxs-lookup"><span data-stu-id="d03d3-262">The **Code Editor** opens to the `private void btnAlarmOff_Click` line.</span></span>  
  
4.  <span data-ttu-id="d03d3-263">修改此方法，使它類似下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="d03d3-263">Modify this method so that it resembles the following code.</span></span>  
  
    ```csharp  
    private void btnAlarmOff_Click(object sender, System.EventArgs e)  
    {  
        // Turns off the alarm.  
        AlarmSet = false;  
        // Hides the flashing label.  
        lblAlarm.Visible = false;  
    }  
    ```  
  
5.  <span data-ttu-id="d03d3-264">在 [檔案] 功能表上按一下 [全部儲存] 以儲存專案。</span><span class="sxs-lookup"><span data-stu-id="d03d3-264">On the **File** menu, click **Save All** to save the project.</span></span>  
  
### <a name="using-the-inherited-control-on-a-form"></a><span data-ttu-id="d03d3-265">在表單上使用繼承的控制項</span><span class="sxs-lookup"><span data-stu-id="d03d3-265">Using the Inherited Control on a Form</span></span>  
 <span data-ttu-id="d03d3-266">您可以使用測試基底類別控制項的相同方式，測試繼承的控制項，`ctlClock`︰按下 F5 鍵以建置專案，然後在 **UserControl 測試容器**中執行控制項。</span><span class="sxs-lookup"><span data-stu-id="d03d3-266">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="d03d3-267">如需詳細資訊，請參閱[如何：測試 UserControl 的執行階段行為](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)。</span><span class="sxs-lookup"><span data-stu-id="d03d3-267">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="d03d3-268">若要使用控制項，您必須將它裝載在表單上。</span><span class="sxs-lookup"><span data-stu-id="d03d3-268">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="d03d3-269">如同標準複合控制項，繼承的複合控制項無法獨立存在，而且必須裝載在表單或其他容器。</span><span class="sxs-lookup"><span data-stu-id="d03d3-269">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="d03d3-270">由於 `ctlAlarmClock` 有更深入的功能，需要額外的程式碼來進行測試。</span><span class="sxs-lookup"><span data-stu-id="d03d3-270">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="d03d3-271">在此程序中，您將撰寫一個簡單的程式來測試 `ctlAlarmClock` 的功能。</span><span class="sxs-lookup"><span data-stu-id="d03d3-271">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="d03d3-272">您將撰寫程式碼以設定及顯示 `ctlAlarmClock` 的 `AlarmTime` 屬性，然後測試其固有功能。</span><span class="sxs-lookup"><span data-stu-id="d03d3-272">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="d03d3-273">若要建置控制項並且新增至測試表單</span><span class="sxs-lookup"><span data-stu-id="d03d3-273">To build and add your control to a test form</span></span>  
  
1.  <span data-ttu-id="d03d3-274">在 [方案總管] 中，以滑鼠右鍵按一下 [ctlClockLib]，然後按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="d03d3-274">In Solution Explorer, right-click **ctlClockLib**, and then click **Build**.</span></span>  
  
2.  <span data-ttu-id="d03d3-275">將新的 **Windows 應用程式**專案新增至解決方案，並且將它命名為 `Test`。</span><span class="sxs-lookup"><span data-stu-id="d03d3-275">Add a new **Windows Application** project to the solution, and name it `Test`.</span></span>  
  
3.  <span data-ttu-id="d03d3-276">在 [方案總管] 中，以滑鼠右鍵按一下測試專案的 [參考] 節點。</span><span class="sxs-lookup"><span data-stu-id="d03d3-276">In Solution Explorer, right-click the **References** node for your test project.</span></span> <span data-ttu-id="d03d3-277">按一下 [加入參考]以顯示 [加入參考] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d03d3-277">Click **Add Reference** to display the **Add Reference** dialog box.</span></span> <span data-ttu-id="d03d3-278">按一下標籤為 [專案] 的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d03d3-278">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="d03d3-279">您的 `ctlClockLib` 專案會列在 [專案名稱] 底下。</span><span class="sxs-lookup"><span data-stu-id="d03d3-279">Your `ctlClockLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="d03d3-280">按兩下專案以將參考新增至測試專案。</span><span class="sxs-lookup"><span data-stu-id="d03d3-280">Double-click the project to add the reference to the test project.</span></span>  
  
4.  <span data-ttu-id="d03d3-281">在 [方案總管] 中，以滑鼠右鍵按一下 [測試]，然後按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="d03d3-281">In Solution Explorer, right-click **Test**, and then click **Build**.</span></span>  
  
5.  <span data-ttu-id="d03d3-282">在 [工具箱] 中，展開 [ctlClockLib 元件] 節點。</span><span class="sxs-lookup"><span data-stu-id="d03d3-282">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>  
  
6.  <span data-ttu-id="d03d3-283">按兩下 [ctlAlarmClock] 以將 `ctlAlarmClock` 的複本新增至表單。</span><span class="sxs-lookup"><span data-stu-id="d03d3-283">Double-click **ctlAlarmClock** to add a copy of `ctlAlarmClock` to your form.</span></span>  
  
7.  <span data-ttu-id="d03d3-284">在**工具箱**，找出並按兩下**DateTimePicker**加入<xref:System.Windows.Forms.DateTimePicker>控制項至表單，然後再加入<xref:System.Windows.Forms.Label>按兩下控制項**標籤**.</span><span class="sxs-lookup"><span data-stu-id="d03d3-284">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>  
  
8.  <span data-ttu-id="d03d3-285">使用滑鼠將控制項放置在表單上方便的位置。</span><span class="sxs-lookup"><span data-stu-id="d03d3-285">Use the mouse to position the controls in a convenient place on the form.</span></span>  
  
9. <span data-ttu-id="d03d3-286">以下列方式設定這些控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="d03d3-286">Set the properties of these controls in the following manner.</span></span>  
  
    |<span data-ttu-id="d03d3-287">控制項</span><span class="sxs-lookup"><span data-stu-id="d03d3-287">Control</span></span>|<span data-ttu-id="d03d3-288">屬性</span><span class="sxs-lookup"><span data-stu-id="d03d3-288">Property</span></span>|<span data-ttu-id="d03d3-289">值</span><span class="sxs-lookup"><span data-stu-id="d03d3-289">Value</span></span>|  
    |-------------|--------------|-----------|  
    |`label1`|<span data-ttu-id="d03d3-290">**Text**</span><span class="sxs-lookup"><span data-stu-id="d03d3-290">**Text**</span></span>|`(blank space)`|  
    ||<span data-ttu-id="d03d3-291">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d03d3-291">**Name**</span></span>|`lblTest`|  
    |`dateTimePicker1`|<span data-ttu-id="d03d3-292">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d03d3-292">**Name**</span></span>|`dtpTest`|  
    ||<span data-ttu-id="d03d3-293">**格式**</span><span class="sxs-lookup"><span data-stu-id="d03d3-293">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
10. <span data-ttu-id="d03d3-294">在設計工具中，按兩下 [dtpTest]。</span><span class="sxs-lookup"><span data-stu-id="d03d3-294">In the designer, double-click **dtpTest**.</span></span>  
  
     <span data-ttu-id="d03d3-295">[程式碼編輯器] 隨即開啟至 `private void dtpTest_ValueChanged`。</span><span class="sxs-lookup"><span data-stu-id="d03d3-295">The **Code Editor** opens to `private void dtpTest_ValueChanged`.</span></span>  
  
11. <span data-ttu-id="d03d3-296">修改此程式碼，使它類似下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="d03d3-296">Modify the code so that it resembles the following.</span></span>  
  
    ```csharp  
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)  
    {  
        ctlAlarmClock1.AlarmTime = dtpTest.Value;  
        ctlAlarmClock1.AlarmSet = true;  
        lblTest.Text = "Alarm Time is " +  
            ctlAlarmClock1.AlarmTime.ToShortTimeString();  
    }  
    ```  
  
12. <span data-ttu-id="d03d3-297">在 [方案總管] 中，以滑鼠右鍵按一下 [測試]，然後按一下 [設定為啟始專案]。</span><span class="sxs-lookup"><span data-stu-id="d03d3-297">In Solution Explorer, right-click **Test**, and then click **Set as StartUp Project**.</span></span>  
  
13. <span data-ttu-id="d03d3-298">按一下 [偵錯] 功能表上的 [開始偵錯]。</span><span class="sxs-lookup"><span data-stu-id="d03d3-298">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
     <span data-ttu-id="d03d3-299">測試程式隨即啟動。</span><span class="sxs-lookup"><span data-stu-id="d03d3-299">The test program starts.</span></span> <span data-ttu-id="d03d3-300">請注意，目前的時間在更新`ctlAlarmClock`控制項，以及開始時間所示<xref:System.Windows.Forms.DateTimePicker>控制項。</span><span class="sxs-lookup"><span data-stu-id="d03d3-300">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>  
  
14. <span data-ttu-id="d03d3-301">按一下 <xref:System.Windows.Forms.DateTimePicker>其中會顯示在一小時的分鐘。</span><span class="sxs-lookup"><span data-stu-id="d03d3-301">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>  
  
15. <span data-ttu-id="d03d3-302">使用鍵盤，將分鐘值設定為大於 `ctlAlarmClock` 顯示的目前時間一分鐘。</span><span class="sxs-lookup"><span data-stu-id="d03d3-302">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>  
  
     <span data-ttu-id="d03d3-303">警示設定的時間會在 `lblTest` 中顯示。</span><span class="sxs-lookup"><span data-stu-id="d03d3-303">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="d03d3-304">等候顯示的時間達到警示設定時間。</span><span class="sxs-lookup"><span data-stu-id="d03d3-304">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="d03d3-305">當顯示的時間達到警示設定時間，則 `lblAlarm` 會閃爍。</span><span class="sxs-lookup"><span data-stu-id="d03d3-305">When the displayed time reaches the time to which the alarm is set, the `lblAlarm` will flash.</span></span>  
  
16. <span data-ttu-id="d03d3-306">按一下 `btnAlarmOff` 來關閉警示。</span><span class="sxs-lookup"><span data-stu-id="d03d3-306">Turn off the alarm by clicking `btnAlarmOff`.</span></span> <span data-ttu-id="d03d3-307">您現在可以重設警示。</span><span class="sxs-lookup"><span data-stu-id="d03d3-307">You may now reset the alarm.</span></span>  
  
     <span data-ttu-id="d03d3-308">本逐步解說涵蓋了數個重要概念。</span><span class="sxs-lookup"><span data-stu-id="d03d3-308">This walkthrough has covered a number of key concepts.</span></span> <span data-ttu-id="d03d3-309">您已經了解藉由將控制項和元件合併成複合控制項容器，來建立複合控制項。</span><span class="sxs-lookup"><span data-stu-id="d03d3-309">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="d03d3-310">您已經了解將屬性新增至您的控制項，以及撰寫程式碼來實作自訂功能。</span><span class="sxs-lookup"><span data-stu-id="d03d3-310">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="d03d3-311">在最後一節中，您會了解透過繼承擴充指定複合控制項的功能，並且藉由覆寫這些方法來變更主方法的功能。</span><span class="sxs-lookup"><span data-stu-id="d03d3-311">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d03d3-312">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d03d3-312">See Also</span></span>  
 [<span data-ttu-id="d03d3-313">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="d03d3-313">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [<span data-ttu-id="d03d3-314">使用元件進行程式設計</span><span class="sxs-lookup"><span data-stu-id="d03d3-314">Programming with Components</span></span>](https://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)  
 [<span data-ttu-id="d03d3-315">元件撰寫逐步解說</span><span class="sxs-lookup"><span data-stu-id="d03d3-315">Component Authoring Walkthroughs</span></span>](https://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 [<span data-ttu-id="d03d3-316">操作說明：在選擇工具箱項目對話方塊中顯示控制項</span><span class="sxs-lookup"><span data-stu-id="d03d3-316">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [<span data-ttu-id="d03d3-317">逐步解說：使用 Visual C# 繼承自 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="d03d3-317">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
