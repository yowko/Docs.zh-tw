---
title: 逐步解說：使用 Visual C# 撰寫複合控制項
ms.date: 03/30/2017
dev_langs:
- CSharp
helpviewer_keywords:
- custom controls [C#]
- user controls [Windows Forms], creating with Visual C#
- UserControl class [Windows Forms], walkthroughs
- user controls [C#]
- custom controls [Windows Forms], creating
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d1af6c0e013f82569eed8d085df0249f4fb991bb
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015685"
---
# <a name="walkthrough-author-a-composite-control-with-c"></a><span data-ttu-id="938b4-102">逐步解說：撰寫具有 C 的複合控制項\#</span><span class="sxs-lookup"><span data-stu-id="938b4-102">Walkthrough: Author a Composite Control with C\#</span></span>

<span data-ttu-id="938b4-103">複合控制項提供可以建立及重複使用自訂圖形介面的方法。</span><span class="sxs-lookup"><span data-stu-id="938b4-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="938b4-104">複合控制項基本上是具有視覺表示的元件。</span><span class="sxs-lookup"><span data-stu-id="938b4-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="938b4-105">因此，它可能包含一或多個 Windows Forms 控制項、元件或程式碼區塊，可以藉由驗證使用者輸入、修改顯示屬性，或執行作者需要的其他工作來擴充功能。</span><span class="sxs-lookup"><span data-stu-id="938b4-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="938b4-106">複合控制項可以放在 Windows Forms 上，與其他控制項的方式相同。</span><span class="sxs-lookup"><span data-stu-id="938b4-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="938b4-107">在本逐步解說的第一個部分中，您可以建立簡單的複合控制項，稱為 `ctlClock`。</span><span class="sxs-lookup"><span data-stu-id="938b4-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="938b4-108">在逐步解說的第二個部分中，您透過繼承擴充 `ctlClock` 的功能。</span><span class="sxs-lookup"><span data-stu-id="938b4-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="938b4-109">建立專案</span><span class="sxs-lookup"><span data-stu-id="938b4-109">Create the Project</span></span>

<span data-ttu-id="938b4-110">當您建立新的專案時，您會指定其名稱以設定根命名空間、組件名稱和專案名稱，並且確定預設元件將會在正確的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="938b4-110">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="938b4-111">建立 ctlClockLib 控制項程式庫和 ctlClock 控制項</span><span class="sxs-lookup"><span data-stu-id="938b4-111">To create the ctlClockLib control library and the ctlClock control</span></span>

1. <span data-ttu-id="938b4-112">在 Visual Studio 中, 建立新的**Windows Forms 控制項程式庫**專案, 並將其命名為**ctlClockLib**。</span><span class="sxs-lookup"><span data-stu-id="938b4-112">In Visual Studio, create a new **Windows Forms Control Library** project, and name it **ctlClockLib**.</span></span>

     <span data-ttu-id="938b4-113">專案名稱，`ctlClockLib`，預設也會指派給根命名空間。</span><span class="sxs-lookup"><span data-stu-id="938b4-113">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="938b4-114">根命名空間是用來限定組件中的元件名稱。</span><span class="sxs-lookup"><span data-stu-id="938b4-114">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="938b4-115">例如，如果兩個組件提供元件，名為 `ctlClock`，您可以使用 `ctlClockLib.ctlClock.` 指定您的 `ctlClock` 元件</span><span class="sxs-lookup"><span data-stu-id="938b4-115">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>

2. <span data-ttu-id="938b4-116">在**方案總管**中, 以滑鼠右鍵按一下 [ **UserControl1.cs**], 然後按一下 [**重新命名**]。</span><span class="sxs-lookup"><span data-stu-id="938b4-116">In **Solution Explorer**, right-click **UserControl1.cs**, and then click **Rename**.</span></span> <span data-ttu-id="938b4-117">將檔案名稱變更為 `ctlClock.cs`。</span><span class="sxs-lookup"><span data-stu-id="938b4-117">Change the file name to `ctlClock.cs`.</span></span> <span data-ttu-id="938b4-118">當系統詢問您是否要重新命名程式碼元素 "UserControl1" 的所有參考時，按一下 [是]按鈕。</span><span class="sxs-lookup"><span data-stu-id="938b4-118">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>

    > [!NOTE]
    > <span data-ttu-id="938b4-119">根據預設, 複合控制項會繼承系統所提供<xref:System.Windows.Forms.UserControl>的類別。</span><span class="sxs-lookup"><span data-stu-id="938b4-119">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="938b4-120">類別<xref:System.Windows.Forms.UserControl>提供所有複合控制項所需的功能, 並實作為標準方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="938b4-120">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>

3. <span data-ttu-id="938b4-121">在 [檔案] 功能表上按一下 [全部儲存] 以儲存專案。</span><span class="sxs-lookup"><span data-stu-id="938b4-121">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="add-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="938b4-122">將 Windows 控制項和元件新增至複合控制項</span><span class="sxs-lookup"><span data-stu-id="938b4-122">Add Windows Controls and Components to the Composite Control</span></span>

<span data-ttu-id="938b4-123">視覺化介面是複合控制項不可或缺的一部分。</span><span class="sxs-lookup"><span data-stu-id="938b4-123">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="938b4-124">這個視覺化介面是藉由將一或多個 Windows 控制項新增至設計工具介面來實作。</span><span class="sxs-lookup"><span data-stu-id="938b4-124">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="938b4-125">在下列示範中，您將 Windows 控制項合併到您的複合控制項，並且撰寫程式碼來實作功能。</span><span class="sxs-lookup"><span data-stu-id="938b4-125">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="938b4-126">將標籤和計時器新增至複合控制項</span><span class="sxs-lookup"><span data-stu-id="938b4-126">To add a Label and a Timer to your composite control</span></span>

1. <span data-ttu-id="938b4-127">在**方案總管**中, 以滑鼠右鍵按一下 [ **ctlClock.cs**], 然後按一下 [**視圖設計**工具]。</span><span class="sxs-lookup"><span data-stu-id="938b4-127">In **Solution Explorer**, right-click **ctlClock.cs**, and then click **View Designer**.</span></span>

2. <span data-ttu-id="938b4-128">在 [工具箱] 中展開 [通用控制項] 節點，然後再按兩下 [標籤]。</span><span class="sxs-lookup"><span data-stu-id="938b4-128">In the **Toolbox**, expand the **Common Controls** node, and then double-click **Label**.</span></span>

     <span data-ttu-id="938b4-129"><xref:System.Windows.Forms.Label> 名`label1`為的控制項會加入至設計工具介面上的控制項。</span><span class="sxs-lookup"><span data-stu-id="938b4-129">A <xref:System.Windows.Forms.Label> control named `label1` is added to your control on the designer surface.</span></span>

3. <span data-ttu-id="938b4-130">在設計工具中，按一下 [label1]。</span><span class="sxs-lookup"><span data-stu-id="938b4-130">In the designer, click **label1**.</span></span> <span data-ttu-id="938b4-131">在 [屬性] 視窗中設定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="938b4-131">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="938b4-132">屬性</span><span class="sxs-lookup"><span data-stu-id="938b4-132">Property</span></span>|<span data-ttu-id="938b4-133">變更為</span><span class="sxs-lookup"><span data-stu-id="938b4-133">Change to</span></span>|
    |--------------|---------------|
    |<span data-ttu-id="938b4-134">**名稱**</span><span class="sxs-lookup"><span data-stu-id="938b4-134">**Name**</span></span>|`lblDisplay`|
    |<span data-ttu-id="938b4-135">**Text**</span><span class="sxs-lookup"><span data-stu-id="938b4-135">**Text**</span></span>|`(blank space)`|
    |<span data-ttu-id="938b4-136">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="938b4-136">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="938b4-137">**Font.Size**</span><span class="sxs-lookup"><span data-stu-id="938b4-137">**Font.Size**</span></span>|`14`|

4. <span data-ttu-id="938b4-138">在 [工具箱] 中展開 [元件] 節點，然後再按兩下 [計時器]。</span><span class="sxs-lookup"><span data-stu-id="938b4-138">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>

     <span data-ttu-id="938b4-139"><xref:System.Windows.Forms.Timer>因為是元件, 所以在執行時間沒有視覺表示。</span><span class="sxs-lookup"><span data-stu-id="938b4-139">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="938b4-140">因此，它不會與控制項一起出現在設計工具介面上，而是會出現在 [元件設計工具] 中 (位於設計工具介面底部的系統匣)。</span><span class="sxs-lookup"><span data-stu-id="938b4-140">Therefore, it does not appear with the controls on the designer surface, but rather in the **Component Designer** (a tray at the bottom of the designer surface).</span></span>

5. <span data-ttu-id="938b4-141">在**元件設計**工具中, 按一下 [ **timer1**], 然後<xref:System.Windows.Forms.Timer.Interval%2A>將屬性`1000`設為<xref:System.Windows.Forms.Timer.Enabled%2A> , 並`true`將屬性設定為。</span><span class="sxs-lookup"><span data-stu-id="938b4-141">In the **Component Designer**, click **timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>

     <span data-ttu-id="938b4-142">屬性會控制<xref:System.Windows.Forms.Timer>元件刻度的頻率。 <xref:System.Windows.Forms.Timer.Interval%2A></span><span class="sxs-lookup"><span data-stu-id="938b4-142">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the <xref:System.Windows.Forms.Timer> component ticks.</span></span> <span data-ttu-id="938b4-143">每次 `timer1` 走動時，它會執行 `timer1_Tick` 事件中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="938b4-143">Each time `timer1` ticks, it runs the code in the `timer1_Tick` event.</span></span> <span data-ttu-id="938b4-144">間隔代表刻度之間的毫秒數。</span><span class="sxs-lookup"><span data-stu-id="938b4-144">The interval represents the number of milliseconds between ticks.</span></span>

6. <span data-ttu-id="938b4-145">在 [元件設計工具] 中，按兩下 [timer1] 以前往 `ctlClock` 的 `timer1_Tick` 事件。</span><span class="sxs-lookup"><span data-stu-id="938b4-145">In the **Component Designer**, double-click **timer1** to go to the `timer1_Tick` event for `ctlClock`.</span></span>

7. <span data-ttu-id="938b4-146">修改程式碼，使它類似下列程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="938b4-146">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="938b4-147">請確定將存取修飾詞從 `private` 變更為 `protected`。</span><span class="sxs-lookup"><span data-stu-id="938b4-147">Be sure to change the access modifier from `private` to `protected`.</span></span>

    ```csharp
    protected void timer1_Tick(object sender, System.EventArgs e)
    {
        // Causes the label to display the current time.
        lblDisplay.Text = DateTime.Now.ToLongTimeString();
    }
    ```

     <span data-ttu-id="938b4-148">此程式碼會造成目前時間在 `lblDisplay` 中顯示。</span><span class="sxs-lookup"><span data-stu-id="938b4-148">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="938b4-149">因為 `timer1` 的間隔設為 `1000`，每一千毫秒便會發生此事件，因此每秒會更新目前時間。</span><span class="sxs-lookup"><span data-stu-id="938b4-149">Because the interval of `timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>

8. <span data-ttu-id="938b4-150">修改方法為可使用 `virtual`關鍵字覆寫。</span><span class="sxs-lookup"><span data-stu-id="938b4-150">Modify the method to be overridable with the `virtual` keyword.</span></span> <span data-ttu-id="938b4-151">如需詳細資訊，請參閱以下的「從使用者控制項繼承」一節。</span><span class="sxs-lookup"><span data-stu-id="938b4-151">For more information, see the  "Inheriting from a User Control" section below.</span></span>

    ```csharp
    protected virtual void timer1_Tick(object sender, System.EventArgs e)
    ```

9. <span data-ttu-id="938b4-152">在 [檔案] 功能表上按一下 [全部儲存] 以儲存專案。</span><span class="sxs-lookup"><span data-stu-id="938b4-152">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="add-properties-to-the-composite-control"></a><span data-ttu-id="938b4-153">將屬性加入至複合控制項</span><span class="sxs-lookup"><span data-stu-id="938b4-153">Add Properties to the Composite Control</span></span>

<span data-ttu-id="938b4-154">您的時鐘控制項現在會<xref:System.Windows.Forms.Label>封裝控制項<xref:System.Windows.Forms.Timer>和元件, 每個都有自己的一組固有屬性。</span><span class="sxs-lookup"><span data-stu-id="938b4-154">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="938b4-155">雖然這些控制項的個別屬性無法供控制項的後續使用者存取，但是您可以建立並公開自訂屬性，方法是撰寫適當的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="938b4-155">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="938b4-156">在下列程序中，您會將屬性新增至控制項，讓使用者變更背景與文字的色彩。</span><span class="sxs-lookup"><span data-stu-id="938b4-156">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>

### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="938b4-157">若要將屬性新增至複合控制項</span><span class="sxs-lookup"><span data-stu-id="938b4-157">To add a property to your composite control</span></span>

1. <span data-ttu-id="938b4-158">在**方案總管**中, 以滑鼠右鍵按一下 [ **ctlClock.cs**], 然後按一下 [ **View Code**]。</span><span class="sxs-lookup"><span data-stu-id="938b4-158">In **Solution Explorer**, right-click **ctlClock.cs**, and then click **View Code**.</span></span>

     <span data-ttu-id="938b4-159">控制項的 [程式碼編輯器] 隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="938b4-159">The **Code Editor** for your control opens.</span></span>

2. <span data-ttu-id="938b4-160">尋找 `public partial class ctlClock` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="938b4-160">Locate the `public partial class ctlClock` statement.</span></span> <span data-ttu-id="938b4-161">在左大括號 (`{)` 底下，輸入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="938b4-161">Beneath the opening brace (`{)`, type the following code.</span></span>

    ```csharp
    private Color colFColor;
    private Color colBColor;
    ```

     <span data-ttu-id="938b4-162">這些陳述式會建立私用變數，您將用來儲存您即將建立之屬性的值。</span><span class="sxs-lookup"><span data-stu-id="938b4-162">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>

3. <span data-ttu-id="938b4-163">在步驟2的變數宣告底下, 輸入或貼上下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="938b4-163">Enter or paste the following code beneath the variable declarations from step 2.</span></span>

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

     <span data-ttu-id="938b4-164">上述程式碼會製作兩個自訂屬性，`ClockForeColor` 和 `ClockBackColor`，以供此控制項的後續使用者使用。</span><span class="sxs-lookup"><span data-stu-id="938b4-164">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control.</span></span> <span data-ttu-id="938b4-165">`get` 和 `set` 陳述式提供屬性值的儲存和擷取，以及用來實作適合該屬性之功能的程式碼。</span><span class="sxs-lookup"><span data-stu-id="938b4-165">The `get` and `set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>

4. <span data-ttu-id="938b4-166">在 [檔案] 功能表上按一下 [全部儲存] 以儲存專案。</span><span class="sxs-lookup"><span data-stu-id="938b4-166">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="test-the-control"></a><span data-ttu-id="938b4-167">測試控制項</span><span class="sxs-lookup"><span data-stu-id="938b4-167">Test the Control</span></span>

<span data-ttu-id="938b4-168">控制項不是獨立應用程式；它們必須裝載在容器中。</span><span class="sxs-lookup"><span data-stu-id="938b4-168">Controls are not stand-alone applications; they must be hosted in a container.</span></span> <span data-ttu-id="938b4-169">測試控制項的執行階段行為，並且使用 **UserControl 測試容器**執行其屬性。</span><span class="sxs-lookup"><span data-stu-id="938b4-169">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="938b4-170">如需詳細資訊，請參閱[如何：測試 UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)的執行時間行為。</span><span class="sxs-lookup"><span data-stu-id="938b4-170">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

### <a name="to-test-your-control"></a><span data-ttu-id="938b4-171">若要測試控制項</span><span class="sxs-lookup"><span data-stu-id="938b4-171">To test your control</span></span>

1. <span data-ttu-id="938b4-172">按**F5**以建立專案, 並在**UserControl 測試容器**中執行您的控制項。</span><span class="sxs-lookup"><span data-stu-id="938b4-172">Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span>

2. <span data-ttu-id="938b4-173">在測試容器的屬性方格中，尋找 `ClockBackColor` 屬性，然後選取屬性以顯示色彩調色盤。</span><span class="sxs-lookup"><span data-stu-id="938b4-173">In the test container's property grid, locate the `ClockBackColor` property, and then select the property to display the color palette.</span></span>

3. <span data-ttu-id="938b4-174">按一下它以選擇色彩。</span><span class="sxs-lookup"><span data-stu-id="938b4-174">Choose a color by clicking it.</span></span>

   <span data-ttu-id="938b4-175">控制項的背景色彩會變更為您所選取的色彩。</span><span class="sxs-lookup"><span data-stu-id="938b4-175">The background color of your control changes to the color you selected.</span></span>

4. <span data-ttu-id="938b4-176">使用類似的一連串事件，確認 `ClockForeColor` 屬性是否如預期運作。</span><span class="sxs-lookup"><span data-stu-id="938b4-176">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>

   <span data-ttu-id="938b4-177">在本節和先前的章節中，您已經知道元件和 Windows 控制項如何與程式碼合併並且封裝，以複合控制項的形式提供自訂功能。</span><span class="sxs-lookup"><span data-stu-id="938b4-177">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="938b4-178">您已經了解如何在您的複合控制項中公開屬性，以及如何在完成之後測試您的控制項。</span><span class="sxs-lookup"><span data-stu-id="938b4-178">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="938b4-179">在下一節中，您將學習如何使用 `ctlClock` 做為基底，建構繼承的複合控制項。</span><span class="sxs-lookup"><span data-stu-id="938b4-179">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>

## <a name="inherit-from-a-composite-control"></a><span data-ttu-id="938b4-180">繼承自複合控制項</span><span class="sxs-lookup"><span data-stu-id="938b4-180">Inherit from a Composite Control</span></span>

<span data-ttu-id="938b4-181">在先前章節中，您了解如何將 Windows 控制項、元件和程式碼合併成可重複使用的複合控制項。</span><span class="sxs-lookup"><span data-stu-id="938b4-181">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="938b4-182">複合控制項現在可以做為建置其他控制項的基底。</span><span class="sxs-lookup"><span data-stu-id="938b4-182">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="938b4-183">從基底類別衍生類別的處理序稱為「繼承」。</span><span class="sxs-lookup"><span data-stu-id="938b4-183">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="938b4-184">在本節中，您將建立稱為 `ctlAlarmClock` 的複合控制項。</span><span class="sxs-lookup"><span data-stu-id="938b4-184">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="938b4-185">這個控制項將會從其父控制項 (`ctlClock`) 衍生。</span><span class="sxs-lookup"><span data-stu-id="938b4-185">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="938b4-186">您將學習藉由覆寫父方法並且新增新方法和屬性，來擴充 `ctlClock` 的功能。</span><span class="sxs-lookup"><span data-stu-id="938b4-186">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>

<span data-ttu-id="938b4-187">建立繼承的控制項的第一個步驟是從其父代衍生。</span><span class="sxs-lookup"><span data-stu-id="938b4-187">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="938b4-188">這個動作會建立新的控制項，其中具有父控制項的所有屬性、方法和圖形特性，但是也可以做為基底，以新增新的或修改功能。</span><span class="sxs-lookup"><span data-stu-id="938b4-188">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>

### <a name="to-create-the-inherited-control"></a><span data-ttu-id="938b4-189">若要建立繼承的控制項</span><span class="sxs-lookup"><span data-stu-id="938b4-189">To create the inherited control</span></span>

1. <span data-ttu-id="938b4-190">在**方案總管**中, 以滑鼠右鍵按一下 [ **ctlClockLib**], 指向 [**新增**], 然後按一下 [**使用者控制項**]。</span><span class="sxs-lookup"><span data-stu-id="938b4-190">In **Solution Explorer**, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>

     <span data-ttu-id="938b4-191">[新增項目] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="938b4-191">The **Add New Item** dialog box opens.</span></span>

2. <span data-ttu-id="938b4-192">選取**繼承的使用者控制項**範本。</span><span class="sxs-lookup"><span data-stu-id="938b4-192">Select the **Inherited User Control** template.</span></span>

3. <span data-ttu-id="938b4-193">在 [名稱] 方塊中，輸入 `ctlAlarmClock.cs` 然後按一下 [新增]。</span><span class="sxs-lookup"><span data-stu-id="938b4-193">In the **Name** box, type `ctlAlarmClock.cs`, and then click **Add**.</span></span>

     <span data-ttu-id="938b4-194">[繼承選取器] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="938b4-194">The **Inheritance Picker** dialog box appears.</span></span>

4. <span data-ttu-id="938b4-195">在 [元件名稱] 底下，按兩下 [ctlClock]。</span><span class="sxs-lookup"><span data-stu-id="938b4-195">Under **Component Name**, double-click **ctlClock**.</span></span>

5. <span data-ttu-id="938b4-196">在**方案總管**中, 流覽目前的專案。</span><span class="sxs-lookup"><span data-stu-id="938b4-196">In **Solution Explorer**, browse through the current projects.</span></span>

    > [!NOTE]
    > <span data-ttu-id="938b4-197">名為 **ctlAlarmClock.cs** 的檔案已新增至目前的專案。</span><span class="sxs-lookup"><span data-stu-id="938b4-197">A file called **ctlAlarmClock.cs** has been added to the current project.</span></span>

### <a name="add-the-alarm-properties"></a><span data-ttu-id="938b4-198">新增警示屬性</span><span class="sxs-lookup"><span data-stu-id="938b4-198">Add the Alarm Properties</span></span>

<span data-ttu-id="938b4-199">屬性會以新增至複合控制項的相同方式，新增至繼承的控制項。</span><span class="sxs-lookup"><span data-stu-id="938b4-199">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="938b4-200">您現在會使用屬性宣告語法將兩個屬性新增至您的控制項︰`AlarmTime`，它將會儲存警示停止之日期和時間的值，以及 `AlarmSet`，它將會指示是否已設定警示。</span><span class="sxs-lookup"><span data-stu-id="938b4-200">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>

#### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="938b4-201">若要將屬性新增至複合控制項</span><span class="sxs-lookup"><span data-stu-id="938b4-201">To add properties to your composite control</span></span>

1. <span data-ttu-id="938b4-202">在**方案總管**中, 以滑鼠右鍵按一下  **ctlalarmclock**, 然後按一下  **View Code**。</span><span class="sxs-lookup"><span data-stu-id="938b4-202">In **Solution Explorer**, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>

2. <span data-ttu-id="938b4-203">尋找 `public class` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="938b4-203">Locate the `public class` statement.</span></span> <span data-ttu-id="938b4-204">請注意，您的控制項繼承自`ctlClockLib.ctlClock`。</span><span class="sxs-lookup"><span data-stu-id="938b4-204">Note that your control inherits from `ctlClockLib.ctlClock`.</span></span> <span data-ttu-id="938b4-205">在左大括號 (`{)` 陳述式底下，輸入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="938b4-205">Beneath the opening brace (`{)` statement, type the following code.</span></span>

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

### <a name="add-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="938b4-206">將加入至控制項的圖形化介面</span><span class="sxs-lookup"><span data-stu-id="938b4-206">Add to the Graphical Interface of the Control</span></span>

<span data-ttu-id="938b4-207">繼承的控制項具有視覺化介面，與它所繼承的控制項相同。</span><span class="sxs-lookup"><span data-stu-id="938b4-207">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="938b4-208">它擁有與其父控制項相同的組成控制項，但是無法使用組成控制項的屬性，除非特別公開。</span><span class="sxs-lookup"><span data-stu-id="938b4-208">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="938b4-209">您可以使用新增至任何複合控制項的相同方式，新增至繼承的複合控制項的圖形化介面。</span><span class="sxs-lookup"><span data-stu-id="938b4-209">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="938b4-210">若要繼續新增至警示時鐘的視覺化介面，您要新增標籤控制項，該控制項會在警示響起時閃爍。</span><span class="sxs-lookup"><span data-stu-id="938b4-210">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>

#### <a name="to-add-the-label-control"></a><span data-ttu-id="938b4-211">若要新增標籤控制項</span><span class="sxs-lookup"><span data-stu-id="938b4-211">To add the label control</span></span>

1. <span data-ttu-id="938b4-212">在**方案總管**中, 以滑鼠右鍵按一下  **ctlalarmclock**, 然後按一下 **視圖設計**工具。</span><span class="sxs-lookup"><span data-stu-id="938b4-212">In **Solution Explorer**, right-click **ctlAlarmClock**, and then click **View Designer**.</span></span>

     <span data-ttu-id="938b4-213">`ctlAlarmClock` 的設計工具隨即在主視窗中開啟。</span><span class="sxs-lookup"><span data-stu-id="938b4-213">The designer for `ctlAlarmClock` opens in the main window.</span></span>

2. <span data-ttu-id="938b4-214">按一下控制項的顯示部分，並檢視 [屬性] 視窗。</span><span class="sxs-lookup"><span data-stu-id="938b4-214">Click the display portion of the control, and view the Properties window.</span></span>

    > [!NOTE]
    > <span data-ttu-id="938b4-215">所有屬性顯示時，它們會以灰色顯示。</span><span class="sxs-lookup"><span data-stu-id="938b4-215">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="938b4-216">這表示這些屬性是 `lblDisplay` 的原生屬性，而且無法修改或在 [屬性] 視窗中存取。</span><span class="sxs-lookup"><span data-stu-id="938b4-216">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="938b4-217">根據預設，包含在複合控制項中的控制項是 `private`，而且其屬性無法使用任何方法存取。</span><span class="sxs-lookup"><span data-stu-id="938b4-217">By default, controls contained in a composite control are `private`, and their properties are not accessible by any means.</span></span>

    > [!NOTE]
    > <span data-ttu-id="938b4-218">如果您想要讓複合控制項的後續使用者可以存取其內部控制項，請將它們宣告為 `public` 或 `protected`。</span><span class="sxs-lookup"><span data-stu-id="938b4-218">If you want subsequent users of your composite control to have access to its internal controls, declare them as `public` or `protected`.</span></span> <span data-ttu-id="938b4-219">這可讓您使用適當的程式碼，設定及修改包含在複合控制項中的控制項屬性。</span><span class="sxs-lookup"><span data-stu-id="938b4-219">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>

3. <span data-ttu-id="938b4-220"><xref:System.Windows.Forms.Label>將控制項新增至您的複合控制項。</span><span class="sxs-lookup"><span data-stu-id="938b4-220">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>

4. <span data-ttu-id="938b4-221">使用滑鼠, 將<xref:System.Windows.Forms.Label>控制項拖曳到顯示方塊的正下方。</span><span class="sxs-lookup"><span data-stu-id="938b4-221">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="938b4-222">在 [屬性] 視窗中設定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="938b4-222">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="938b4-223">屬性</span><span class="sxs-lookup"><span data-stu-id="938b4-223">Property</span></span>|<span data-ttu-id="938b4-224">設定</span><span class="sxs-lookup"><span data-stu-id="938b4-224">Setting</span></span>|
    |--------------|-------------|
    |<span data-ttu-id="938b4-225">**名稱**</span><span class="sxs-lookup"><span data-stu-id="938b4-225">**Name**</span></span>|`lblAlarm`|
    |<span data-ttu-id="938b4-226">**Text**</span><span class="sxs-lookup"><span data-stu-id="938b4-226">**Text**</span></span>|<span data-ttu-id="938b4-227">**Alarm!**</span><span class="sxs-lookup"><span data-stu-id="938b4-227">**Alarm!**</span></span>|
    |<span data-ttu-id="938b4-228">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="938b4-228">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="938b4-229">**可見**</span><span class="sxs-lookup"><span data-stu-id="938b4-229">**Visible**</span></span>|`false`|

### <a name="add-the-alarm-functionality"></a><span data-ttu-id="938b4-230">新增鬧鐘功能</span><span class="sxs-lookup"><span data-stu-id="938b4-230">Add the Alarm Functionality</span></span>

<span data-ttu-id="938b4-231">在先前的程序中，您新增屬性和控制項，在您的複合控制項中啟用警示功能。</span><span class="sxs-lookup"><span data-stu-id="938b4-231">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="938b4-232">在此程序中，您將會新增程式碼以比較目前時間與警示時間，如果它們相同，則讓警示閃爍。</span><span class="sxs-lookup"><span data-stu-id="938b4-232">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to flash an alarm.</span></span> <span data-ttu-id="938b4-233">藉由覆寫 `ctlClock` 的 `timer1_Tick` 方法，並且將額外程式碼新增至其中，您就可以擴充 `ctlAlarmClock` 的功能，同時保留 `ctlClock` 的所有固有功能。</span><span class="sxs-lookup"><span data-stu-id="938b4-233">By overriding the `timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a><span data-ttu-id="938b4-234">若要覆寫 ctlClock 的 timer1_Tick 方法</span><span class="sxs-lookup"><span data-stu-id="938b4-234">To override the timer1_Tick method of ctlClock</span></span>

1. <span data-ttu-id="938b4-235">在 [程式碼編輯器] 中，尋找 `private bool blnAlarmSet;` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="938b4-235">In the **Code Editor**, locate the `private bool blnAlarmSet;` statement.</span></span> <span data-ttu-id="938b4-236">緊接著在其下新增下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="938b4-236">Immediately beneath it, add the following statement.</span></span>

    ```csharp
    private bool blnColorTicker;
    ```

2. <span data-ttu-id="938b4-237">在 [程式碼編輯器] 中，在類別結尾尋找右大括號 (`})`。</span><span class="sxs-lookup"><span data-stu-id="938b4-237">In the **Code Editor**, locate the closing brace (`})` at the end of the class.</span></span> <span data-ttu-id="938b4-238">緊接在大括號之前，新增下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="938b4-238">Just before the brace, add the following code.</span></span>

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

     <span data-ttu-id="938b4-239">新增這個程式碼會完成幾項工作。</span><span class="sxs-lookup"><span data-stu-id="938b4-239">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="938b4-240">`override` 陳述式會指示控制項使用這個方法來取代繼承自基底控制項的方法。</span><span class="sxs-lookup"><span data-stu-id="938b4-240">The `override` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="938b4-241">呼叫這個方法時，它會呼叫它藉由叫用 `base.timer1_Tick` 陳述式覆寫的方法，確保併入原始控制項的所有功能在此控制項中重現。</span><span class="sxs-lookup"><span data-stu-id="938b4-241">When this method is called, it calls the method it overrides by invoking the `base.timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="938b4-242">接著，它會執行其他程式碼以併入警示功能。</span><span class="sxs-lookup"><span data-stu-id="938b4-242">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="938b4-243">發生警示時，閃爍標籤控制項就會出現。</span><span class="sxs-lookup"><span data-stu-id="938b4-243">A flashing label control will appear when the alarm occurs.</span></span>

     <span data-ttu-id="938b4-244">警示時鐘控制項已接近完成。</span><span class="sxs-lookup"><span data-stu-id="938b4-244">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="938b4-245">唯一剩餘的事項是實作將它關閉的方式。</span><span class="sxs-lookup"><span data-stu-id="938b4-245">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="938b4-246">若要這樣做，您要將程式碼新增至 `lblAlarm_Click` 方法。</span><span class="sxs-lookup"><span data-stu-id="938b4-246">To do this, you will add code to the `lblAlarm_Click` method.</span></span>

#### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="938b4-247">若要實作關閉方法</span><span class="sxs-lookup"><span data-stu-id="938b4-247">To implement the shutoff method</span></span>

1. <span data-ttu-id="938b4-248">在**方案總管**中, 以滑鼠右鍵按一下 [ **ctlAlarmClock.cs**], 然後按一下 [**視圖設計**工具]。</span><span class="sxs-lookup"><span data-stu-id="938b4-248">In **Solution Explorer**, right-click **ctlAlarmClock.cs**, and then click **View Designer**.</span></span>

     <span data-ttu-id="938b4-249">設計工具隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="938b4-249">The designer opens.</span></span>

2. <span data-ttu-id="938b4-250">將按鈕新增至控制項。</span><span class="sxs-lookup"><span data-stu-id="938b4-250">Add a button to the control.</span></span> <span data-ttu-id="938b4-251">將按鈕的屬性設定如下。</span><span class="sxs-lookup"><span data-stu-id="938b4-251">Set the properties of the button as follows.</span></span>

    |<span data-ttu-id="938b4-252">屬性</span><span class="sxs-lookup"><span data-stu-id="938b4-252">Property</span></span>|<span data-ttu-id="938b4-253">值</span><span class="sxs-lookup"><span data-stu-id="938b4-253">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="938b4-254">**名稱**</span><span class="sxs-lookup"><span data-stu-id="938b4-254">**Name**</span></span>|`btnAlarmOff`|
    |<span data-ttu-id="938b4-255">**Text**</span><span class="sxs-lookup"><span data-stu-id="938b4-255">**Text**</span></span>|<span data-ttu-id="938b4-256">**停用警示**</span><span class="sxs-lookup"><span data-stu-id="938b4-256">**Disable Alarm**</span></span>|

3. <span data-ttu-id="938b4-257">在設計工具中，按兩下 [btnAlarmOff]。</span><span class="sxs-lookup"><span data-stu-id="938b4-257">In the designer, double-click **btnAlarmOff**.</span></span>

     <span data-ttu-id="938b4-258">[程式碼編輯器] 隨即開啟至 `private void btnAlarmOff_Click` 行。</span><span class="sxs-lookup"><span data-stu-id="938b4-258">The **Code Editor** opens to the `private void btnAlarmOff_Click` line.</span></span>

4. <span data-ttu-id="938b4-259">修改此方法，使它類似下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="938b4-259">Modify this method so that it resembles the following code.</span></span>

    ```csharp
    private void btnAlarmOff_Click(object sender, System.EventArgs e)
    {
        // Turns off the alarm.
        AlarmSet = false;
        // Hides the flashing label.
        lblAlarm.Visible = false;
    }
    ```

5. <span data-ttu-id="938b4-260">在 [檔案] 功能表上按一下 [全部儲存] 以儲存專案。</span><span class="sxs-lookup"><span data-stu-id="938b4-260">On the **File** menu, click **Save All** to save the project.</span></span>

### <a name="use-the-inherited-control-on-a-form"></a><span data-ttu-id="938b4-261">在表單上使用繼承的控制項</span><span class="sxs-lookup"><span data-stu-id="938b4-261">Use the Inherited Control on a Form</span></span>

<span data-ttu-id="938b4-262">您可以依照測試基類控制項`ctlClock`的相同方式來測試繼承的控制項:按**F5**以建立專案, 並在**UserControl 測試容器**中執行您的控制項。</span><span class="sxs-lookup"><span data-stu-id="938b4-262">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="938b4-263">如需詳細資訊，請參閱[如何：測試 UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)的執行時間行為。</span><span class="sxs-lookup"><span data-stu-id="938b4-263">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

<span data-ttu-id="938b4-264">若要使用控制項，您必須將它裝載在表單上。</span><span class="sxs-lookup"><span data-stu-id="938b4-264">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="938b4-265">如同標準複合控制項，繼承的複合控制項無法獨立存在，而且必須裝載在表單或其他容器。</span><span class="sxs-lookup"><span data-stu-id="938b4-265">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="938b4-266">由於 `ctlAlarmClock` 有更深入的功能，需要額外的程式碼來進行測試。</span><span class="sxs-lookup"><span data-stu-id="938b4-266">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="938b4-267">在此程序中，您將撰寫一個簡單的程式來測試 `ctlAlarmClock` 的功能。</span><span class="sxs-lookup"><span data-stu-id="938b4-267">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="938b4-268">您將撰寫程式碼以設定及顯示 `ctlAlarmClock` 的 `AlarmTime` 屬性，然後測試其固有功能。</span><span class="sxs-lookup"><span data-stu-id="938b4-268">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>

#### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="938b4-269">若要建置控制項並且新增至測試表單</span><span class="sxs-lookup"><span data-stu-id="938b4-269">To build and add your control to a test form</span></span>

1. <span data-ttu-id="938b4-270">在**方案總管**中, 以滑鼠右鍵按一下 [ **ctlClockLib**], 然後按一下 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="938b4-270">In **Solution Explorer**, right-click **ctlClockLib**, and then click **Build**.</span></span>

2. <span data-ttu-id="938b4-271">將新的**Windows 應用程式**專案新增至方案, 並將其命名為**Test**。</span><span class="sxs-lookup"><span data-stu-id="938b4-271">Add a new **Windows Application** project to the solution, and name it **Test**.</span></span>

3. <span data-ttu-id="938b4-272">在**方案總管**中, 以滑鼠右鍵按一下測試專案的 [**參考**] 節點。</span><span class="sxs-lookup"><span data-stu-id="938b4-272">In **Solution Explorer**, right-click the **References** node for your test project.</span></span> <span data-ttu-id="938b4-273">按一下 [加入參考]以顯示 [加入參考] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="938b4-273">Click **Add Reference** to display the **Add Reference** dialog box.</span></span> <span data-ttu-id="938b4-274">按一下標籤為 [專案] 的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="938b4-274">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="938b4-275">您的 `ctlClockLib` 專案會列在 [專案名稱] 底下。</span><span class="sxs-lookup"><span data-stu-id="938b4-275">Your `ctlClockLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="938b4-276">按兩下專案以將參考新增至測試專案。</span><span class="sxs-lookup"><span data-stu-id="938b4-276">Double-click the project to add the reference to the test project.</span></span>

4. <span data-ttu-id="938b4-277">在**方案總管**中, 以滑鼠右鍵按一下 [**測試**], 然後按一下 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="938b4-277">In **Solution Explorer**, right-click **Test**, and then click **Build**.</span></span>

5. <span data-ttu-id="938b4-278">在 [工具箱] 中，展開 [ctlClockLib 元件] 節點。</span><span class="sxs-lookup"><span data-stu-id="938b4-278">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>

6. <span data-ttu-id="938b4-279">按兩下 [ctlAlarmClock] 以將 `ctlAlarmClock` 的複本新增至表單。</span><span class="sxs-lookup"><span data-stu-id="938b4-279">Double-click **ctlAlarmClock** to add a copy of `ctlAlarmClock` to your form.</span></span>

7. <span data-ttu-id="938b4-280">在 [**工具箱**] 中, 找出並按兩下 [ **DateTimePicker** ] <xref:System.Windows.Forms.DateTimePicker>將控制項新增至<xref:System.Windows.Forms.Label>表單, 然後按兩下 [**標籤**] 來加入控制項。</span><span class="sxs-lookup"><span data-stu-id="938b4-280">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>

8. <span data-ttu-id="938b4-281">使用滑鼠將控制項放置在表單上方便的位置。</span><span class="sxs-lookup"><span data-stu-id="938b4-281">Use the mouse to position the controls in a convenient place on the form.</span></span>

9. <span data-ttu-id="938b4-282">以下列方式設定這些控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="938b4-282">Set the properties of these controls in the following manner.</span></span>

    |<span data-ttu-id="938b4-283">控制項</span><span class="sxs-lookup"><span data-stu-id="938b4-283">Control</span></span>|<span data-ttu-id="938b4-284">屬性</span><span class="sxs-lookup"><span data-stu-id="938b4-284">Property</span></span>|<span data-ttu-id="938b4-285">值</span><span class="sxs-lookup"><span data-stu-id="938b4-285">Value</span></span>|
    |-------------|--------------|-----------|
    |`label1`|<span data-ttu-id="938b4-286">**Text**</span><span class="sxs-lookup"><span data-stu-id="938b4-286">**Text**</span></span>|`(blank space)`|
    ||<span data-ttu-id="938b4-287">**名稱**</span><span class="sxs-lookup"><span data-stu-id="938b4-287">**Name**</span></span>|`lblTest`|
    |`dateTimePicker1`|<span data-ttu-id="938b4-288">**名稱**</span><span class="sxs-lookup"><span data-stu-id="938b4-288">**Name**</span></span>|`dtpTest`|
    ||<span data-ttu-id="938b4-289">**格式**</span><span class="sxs-lookup"><span data-stu-id="938b4-289">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

10. <span data-ttu-id="938b4-290">在設計工具中，按兩下 [dtpTest]。</span><span class="sxs-lookup"><span data-stu-id="938b4-290">In the designer, double-click **dtpTest**.</span></span>

     <span data-ttu-id="938b4-291">[程式碼編輯器] 隨即開啟至 `private void dtpTest_ValueChanged`。</span><span class="sxs-lookup"><span data-stu-id="938b4-291">The **Code Editor** opens to `private void dtpTest_ValueChanged`.</span></span>

11. <span data-ttu-id="938b4-292">修改此程式碼，使它類似下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="938b4-292">Modify the code so that it resembles the following.</span></span>

    ```csharp
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)
    {
        ctlAlarmClock1.AlarmTime = dtpTest.Value;
        ctlAlarmClock1.AlarmSet = true;
        lblTest.Text = "Alarm Time is " +
            ctlAlarmClock1.AlarmTime.ToShortTimeString();
    }
    ```

12. <span data-ttu-id="938b4-293">在**方案總管**中, 以滑鼠右鍵按一下 [**測試**], 然後按一下 [**設定為啟始專案**]。</span><span class="sxs-lookup"><span data-stu-id="938b4-293">In **Solution Explorer**, right-click **Test**, and then click **Set as StartUp Project**.</span></span>

13. <span data-ttu-id="938b4-294">按一下 [偵錯] 功能表上的 [開始偵錯]。</span><span class="sxs-lookup"><span data-stu-id="938b4-294">On the **Debug** menu, click **Start Debugging**.</span></span>

     <span data-ttu-id="938b4-295">測試程式隨即啟動。</span><span class="sxs-lookup"><span data-stu-id="938b4-295">The test program starts.</span></span> <span data-ttu-id="938b4-296">請注意, `ctlAlarmClock`控制項中的目前時間已更新, 而且開始時間會顯示<xref:System.Windows.Forms.DateTimePicker>在控制項中。</span><span class="sxs-lookup"><span data-stu-id="938b4-296">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>

14. <span data-ttu-id="938b4-297">按一下顯示<xref:System.Windows.Forms.DateTimePicker>該小時分鐘數的。</span><span class="sxs-lookup"><span data-stu-id="938b4-297">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>

15. <span data-ttu-id="938b4-298">使用鍵盤，將分鐘值設定為大於 `ctlAlarmClock` 顯示的目前時間一分鐘。</span><span class="sxs-lookup"><span data-stu-id="938b4-298">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>

     <span data-ttu-id="938b4-299">警示設定的時間會在 `lblTest` 中顯示。</span><span class="sxs-lookup"><span data-stu-id="938b4-299">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="938b4-300">等候顯示的時間達到警示設定時間。</span><span class="sxs-lookup"><span data-stu-id="938b4-300">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="938b4-301">當顯示的時間達到警示設定時間，則 `lblAlarm` 會閃爍。</span><span class="sxs-lookup"><span data-stu-id="938b4-301">When the displayed time reaches the time to which the alarm is set, the `lblAlarm` will flash.</span></span>

16. <span data-ttu-id="938b4-302">按一下 `btnAlarmOff` 來關閉警示。</span><span class="sxs-lookup"><span data-stu-id="938b4-302">Turn off the alarm by clicking `btnAlarmOff`.</span></span> <span data-ttu-id="938b4-303">您現在可以重設警示。</span><span class="sxs-lookup"><span data-stu-id="938b4-303">You may now reset the alarm.</span></span>

<span data-ttu-id="938b4-304">本文涵蓋數個重要概念。</span><span class="sxs-lookup"><span data-stu-id="938b4-304">This article has covered a number of key concepts.</span></span> <span data-ttu-id="938b4-305">您已經了解藉由將控制項和元件合併成複合控制項容器，來建立複合控制項。</span><span class="sxs-lookup"><span data-stu-id="938b4-305">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="938b4-306">您已經了解將屬性新增至您的控制項，以及撰寫程式碼來實作自訂功能。</span><span class="sxs-lookup"><span data-stu-id="938b4-306">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="938b4-307">在最後一節中，您會了解透過繼承擴充指定複合控制項的功能，並且藉由覆寫這些方法來變更主方法的功能。</span><span class="sxs-lookup"><span data-stu-id="938b4-307">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>

## <a name="see-also"></a><span data-ttu-id="938b4-308">另請參閱</span><span class="sxs-lookup"><span data-stu-id="938b4-308">See also</span></span>

- [<span data-ttu-id="938b4-309">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="938b4-309">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- <span data-ttu-id="938b4-310">[如何：在 [選擇工具箱專案] 對話方塊中顯示控制項](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span><span class="sxs-lookup"><span data-stu-id="938b4-310">[How to: Display a Control in the Choose Toolbox Items Dialog Box](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span></span>
- [<span data-ttu-id="938b4-311">逐步解說：使用視覺效果從 Windows Forms 控制項繼承C#</span><span class="sxs-lookup"><span data-stu-id="938b4-311">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
