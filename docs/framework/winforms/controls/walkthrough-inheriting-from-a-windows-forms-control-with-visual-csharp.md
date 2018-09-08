---
title: 逐步解說：使用 Visual C# 繼承自 Windows Form 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: 09476da0-8d4c-4a4c-b969-649519dfb438
ms.openlocfilehash: cad15b8fb89ec17e45b0f6cfed22f3109551fc2c
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44130889"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-c"></a><span data-ttu-id="3c7a0-102">逐步解說：使用 Visual C# 繼承自 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="3c7a0-102">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span> #
<span data-ttu-id="3c7a0-103">使用 [!INCLUDE[csprcslong](../../../../includes/csprcslong-md.md)]，您可以透過「繼承」建立功能強大的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-103">With [!INCLUDE[csprcslong](../../../../includes/csprcslong-md.md)], you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="3c7a0-104">您可以透過繼承建立控制項，不僅保留標準 Windows Forms 控制項的所有固有功能，同時也納入自訂功能。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="3c7a0-105">在本逐步解說中，您將會建立簡單的繼承控制項，名為 `ValueButton`。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="3c7a0-106">此按鈕會繼承標準 Windows Form 的功能<xref:System.Windows.Forms.Button>控制項，並會公開 （expose） 的自訂屬性，稱為`ButtonValue`。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3c7a0-107">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="3c7a0-108">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="3c7a0-109">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="3c7a0-110">建立專案</span><span class="sxs-lookup"><span data-stu-id="3c7a0-110">Creating the Project</span></span>  
 <span data-ttu-id="3c7a0-111">當您建立新的專案時，您會指定其名稱以設定根命名空間、組件名稱和專案名稱，並且確定預設元件將會在正確的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-111">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="3c7a0-112">若要建立 ValueButtonLib 控制項程式庫和 ValueButton 控制項</span><span class="sxs-lookup"><span data-stu-id="3c7a0-112">To create the ValueButtonLib control library and the ValueButton control</span></span>  
  
1.  <span data-ttu-id="3c7a0-113">在 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]，開啟 [新增專案] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-113">On the **File** menu, point to **New** and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="3c7a0-114">選取 [ **Windows Form 控制項程式庫**專案範本，從清單中的 Visual C# 專案，然後輸入`ValueButtonLib`中**名稱**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-114">Select the **Windows Forms Control Library** project template from the list of Visual C# Projects, and type `ValueButtonLib` in the **Name** box.</span></span>  
  
     <span data-ttu-id="3c7a0-115">專案名稱，`ValueButtonLib`，預設也會指派給根命名空間。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-115">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="3c7a0-116">根命名空間是用來限定組件中的元件名稱。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-116">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="3c7a0-117">例如，如果兩個組件提供元件，名為 `ValueButton`，您可以使用 `ValueButtonLib.ValueButton` 指定您的 `ValueButton` 元件。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-117">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="3c7a0-118">如需詳細資訊，請參閱[命名空間](../../../csharp/programming-guide/namespaces/index.md)。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-118">For more information, see [Namespaces](../../../csharp/programming-guide/namespaces/index.md).</span></span>  
  
3.  <span data-ttu-id="3c7a0-119">在 [方案總管] 中，以滑鼠右鍵按一下 [UserControl1.cs]，然後從捷徑功能表選擇 [重新命名]。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-119">In **Solution Explorer**, right-click **UserControl1.cs**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="3c7a0-120">將檔案名稱變更為 `ValueButton.cs`。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-120">Change the file name to `ValueButton.cs`.</span></span> <span data-ttu-id="3c7a0-121">當系統詢問您是否要重新命名程式碼元素 '`UserControl1`' 的所有參考時，按一下 [是]按鈕。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-121">Click the **Yes** button when you are asked if you want to rename all references to the code element '`UserControl1`'.</span></span>  
  
4.  <span data-ttu-id="3c7a0-122">在 [方案總管] 中，以滑鼠右鍵按一下 [ValueButton.cs]，然後選取 [檢視程式碼]。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-122">In **Solution Explorer**, right-click **ValueButton.cs** and select **View Code**.</span></span>  
  
5.  <span data-ttu-id="3c7a0-123">找出`class`陳述式行`public partial class ValueButton`，並將變更從這個控制項繼承的型別<xref:System.Windows.Forms.UserControl>至<xref:System.Windows.Forms.Button>。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-123">Locate the `class` statement line, `public partial class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="3c7a0-124">這可讓繼承的控制項繼承的所有功能<xref:System.Windows.Forms.Button>控制項。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-124">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>  
  
6.  <span data-ttu-id="3c7a0-125">在 [方案總管] 中，開啟 [ValueButton.cs] 節點以顯示設計工具產生的程式碼檔案，**ValueButton.Designer.cs**。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-125">In **Solution Explorer**, open the **ValueButton.cs** node to display the designer-generated code file, **ValueButton.Designer.cs**.</span></span> <span data-ttu-id="3c7a0-126">在 [程式碼編輯器] 中開啟此檔案。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-126">Open this file in the **Code Editor**.</span></span>  
  
7.  <span data-ttu-id="3c7a0-127">找出`InitializeComponent`方法，並移除行，該指派<xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-127">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="3c7a0-128">這個屬性不存在於<xref:System.Windows.Forms.Button>控制項。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-128">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>  
  
8.  <span data-ttu-id="3c7a0-129">從 [檔案] 功能表選擇 [全部儲存] 以儲存專案。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-129">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3c7a0-130">視覺化設計工具再也無法使用。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-130">A visual designer is no longer available.</span></span> <span data-ttu-id="3c7a0-131">因為<xref:System.Windows.Forms.Button>控制項沒有自己的繪製，您就無法修改其外觀的設計工具中。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-131">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="3c7a0-132">其視覺表示將會完全與它所繼承之類別的相同 (也就是<xref:System.Windows.Forms.Button>) 除非修改程式碼中。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-132">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span> <span data-ttu-id="3c7a0-133">您仍然可以將元件 (其中沒有任何 UI 元素) 新增至設計介面。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-133">You can still add components, which have no UI elements, to the design surface.</span></span>  
  
## <a name="adding-a-property-to-your-inherited-control"></a><span data-ttu-id="3c7a0-134">將屬性新增至繼承的控制項</span><span class="sxs-lookup"><span data-stu-id="3c7a0-134">Adding a Property to Your Inherited Control</span></span>  
 <span data-ttu-id="3c7a0-135">繼承 Windows Forms 控制項的可能用法之一是建立外觀及操作與標準的 Windows Forms 控制項相同的控制項，但是公開自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-135">One possible use of inherited Windows Forms controls is the creation of controls that are identical in look and feel of standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="3c7a0-136">在本節中，您會將名為 `ButtonValue` 的屬性新增至您的控制項。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-136">In this section, you will add a property called `ButtonValue` to your control.</span></span>  
  
#### <a name="to-add-the-value-property"></a><span data-ttu-id="3c7a0-137">若要新增 Value 屬性</span><span class="sxs-lookup"><span data-stu-id="3c7a0-137">To add the Value property</span></span>  
  
1.  <span data-ttu-id="3c7a0-138">在 [方案總管] 中，以滑鼠右鍵按一下 [ValueButton.cs]，然後從捷徑功能表按一下 [檢視程式碼]。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-138">In **Solution Explorer**, right-click **ValueButton.cs**, and then click **View Code** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="3c7a0-139">尋找 `class` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-139">Locate the `class` statement.</span></span> <span data-ttu-id="3c7a0-140">緊接在 `{` 後面，輸入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="3c7a0-140">Immediately after the `{`, type the following code:</span></span>  
  
    ```csharp  
    // Creates the private variable that will store the value of your   
    // property.  
    private int varValue;  
    // Declares the property.  
    public int ButtonValue  
    {  
       // Sets the method for retrieving the value of your property.  
       get  
       {  
          return varValue;  
       }  
       // Sets the method for setting the value of your property.  
       set  
       {  
          varValue = value;  
       }  
    }  
    ```  
  
     <span data-ttu-id="3c7a0-141">此程式碼會設定方法，系統會使用該方法來儲存和擷取 `ButtonValue` 屬性。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-141">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="3c7a0-142">`get` 陳述式會將傳回值設為儲存在私用變數 `varValue` 的值，而 `set` 陳述式會使用 `value` 關鍵字設定私用變數的值。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-142">The `get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `set` statement sets the value of the private variable by use of the `value` keyword.</span></span>  
  
3.  <span data-ttu-id="3c7a0-143">從 [檔案] 功能表選擇 [全部儲存] 以儲存專案。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-143">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
## <a name="testing-your-control"></a><span data-ttu-id="3c7a0-144">測試您的控制項</span><span class="sxs-lookup"><span data-stu-id="3c7a0-144">Testing Your Control</span></span>  
 <span data-ttu-id="3c7a0-145">控制項不是獨立專案；它們必須裝載在容器中。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-145">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="3c7a0-146">若要測試您的控制項，您必須提供測試專案讓控制項在其中執行。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-146">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="3c7a0-147">您也必須藉由建置 (編譯) 控制項，讓控制項可供測試專案存取。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-147">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="3c7a0-148">在本節中，您將會建置您的控制項，並且在 Windows Form 中進行測試。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-148">In this section, you will build your control and test it in a Windows Form.</span></span>  
  
#### <a name="to-build-your-control"></a><span data-ttu-id="3c7a0-149">若要建置您的控制項</span><span class="sxs-lookup"><span data-stu-id="3c7a0-149">To build your control</span></span>  
  
1.  <span data-ttu-id="3c7a0-150">在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-150">On the **Build** menu, click **Build Solution**.</span></span>  
  
     <span data-ttu-id="3c7a0-151">建置應該會成功，沒有編譯器錯誤或警告。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-151">The build should be successful with no compiler errors or warnings.</span></span>  
  
#### <a name="to-create-a-test-project"></a><span data-ttu-id="3c7a0-152">若要建立測試專案</span><span class="sxs-lookup"><span data-stu-id="3c7a0-152">To create a test project</span></span>  
  
1.  <span data-ttu-id="3c7a0-153">在 [檔案] 功能表上，指向 [新增]，然後選取 [新增專案]，以開啟 [加入新的專案]對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-153">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="3c7a0-154">選取 [Visual C#] 節點下方的 [Windows] 節點，然後按一下 [Windows Forms 應用程式]。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-154">Select the **Windows** node, beneath the **Visual C#** node, and click **Windows Forms Application**.</span></span>  
  
3.  <span data-ttu-id="3c7a0-155">在 [名稱] 方塊中，輸入 `Test`。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-155">In the **Name** box, type `Test`.</span></span>  
  
4.  <span data-ttu-id="3c7a0-156">在 [方案總管] 中，以滑鼠右鍵按一下測試專案的 [參考] 節點，然後從捷徑功能表選取 [加入參考]，以顯示 [加入參考] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-156">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>  
  
5.  <span data-ttu-id="3c7a0-157">按一下標籤為 [專案] 的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-157">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="3c7a0-158">您的 `ValueButtonLib` 專案會列在 [專案名稱] 底下。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-158">Your `ValueButtonLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="3c7a0-159">按兩下專案以將參考新增至測試專案。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-159">Double-click the project to add the reference to the test project.</span></span>  
  
6.  <span data-ttu-id="3c7a0-160">在 [方案總管] 中，以滑鼠右鍵按一下 [測試]，然後選取 [建置]。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-160">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>  
  
#### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="3c7a0-161">若要將控制項新增至表單</span><span class="sxs-lookup"><span data-stu-id="3c7a0-161">To add your control to the form</span></span>  
  
1.  <span data-ttu-id="3c7a0-162">在 [方案總管] 中，以滑鼠右鍵按一下 [Form1.cs]，然後從捷徑功能表選擇 [檢視表設計工具]。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-162">In **Solution Explorer**, right-click **Form1.cs** and choose **View Designer** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="3c7a0-163">在 [工具箱] 中，按一下 [ValueButtonLib 元件]。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-163">In the **Toolbox**, click **ValueButtonLib Components**.</span></span> <span data-ttu-id="3c7a0-164">按兩下 [ValueButton]。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-164">Double-click **ValueButton**.</span></span>  
  
     <span data-ttu-id="3c7a0-165">[ValueButton] 隨即出現在表單上。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-165">A **ValueButton** appears on the form.</span></span>  
  
3.  <span data-ttu-id="3c7a0-166">以滑鼠右鍵按一下 [ValueButton]，然後從捷徑功能表選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-166">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>  
  
4.  <span data-ttu-id="3c7a0-167">在 [屬性] 視窗中，檢查此控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-167">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="3c7a0-168">請注意，它們與標準按鈕所公開的屬性相同，不同之處是有一個額外屬性，`ButtonValue`。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-168">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, `ButtonValue`.</span></span>  
  
5.  <span data-ttu-id="3c7a0-169">將 `ButtonValue` 屬性設定為 `5`。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-169">Set the `ButtonValue` property to `5`.</span></span>  
  
6.  <span data-ttu-id="3c7a0-170">在**所有的 Windows Form**索引標籤**工具箱**，按兩下**標籤**新增<xref:System.Windows.Forms.Label>控制項至表單。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-170">In the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>  
  
7.  <span data-ttu-id="3c7a0-171">重新將標籤放置在表單的中央。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-171">Relocate the label to the center of the form.</span></span>  
  
8.  <span data-ttu-id="3c7a0-172">按兩下 `valueButton1`。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-172">Double-click `valueButton1`.</span></span>  
  
     <span data-ttu-id="3c7a0-173">在 [程式碼編輯器] 中開啟至 `valueButton1_Click` 事件。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-173">The **Code Editor** opens to the `valueButton1_Click` event.</span></span>  
  
9. <span data-ttu-id="3c7a0-174">插入下列程式碼行。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-174">Insert the following line of code.</span></span>  
  
    ```csharp  
    label1.Text = valueButton1.ButtonValue.ToString();  
    ```  
  
10. <span data-ttu-id="3c7a0-175">在 [方案總管] 中，以滑鼠右鍵按一下 [測試]，然後從捷徑功能表選擇 [設定為啟始專案]。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-175">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>  
  
11. <span data-ttu-id="3c7a0-176">從 [偵錯] 功能表中，選取 [開始偵錯]。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-176">From the **Debug** menu, select **Start Debugging**.</span></span>  
  
     <span data-ttu-id="3c7a0-177">`Form1` 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-177">`Form1` appears.</span></span>  
  
12. <span data-ttu-id="3c7a0-178">按一下 `valueButton1`。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-178">Click `valueButton1`.</span></span>  
  
     <span data-ttu-id="3c7a0-179">數字 '5' 會顯示在 `label1` 中，示範繼承的控制項之 `ButtonValue` 屬性已透過 `valueButton1_Click` 方法傳遞至 `label1`。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-179">The numeral '5' is displayed in `label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `label1` through the `valueButton1_Click` method.</span></span> <span data-ttu-id="3c7a0-180">因此，`ValueButton` 控制項會繼承標準 Windows Forms 按鈕的所有功能，但是會公開額外的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="3c7a0-180">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c7a0-181">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c7a0-181">See Also</span></span>  
 [<span data-ttu-id="3c7a0-182">使用元件進行程式設計</span><span class="sxs-lookup"><span data-stu-id="3c7a0-182">Programming with Components</span></span>](https://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)  
 [<span data-ttu-id="3c7a0-183">元件撰寫逐步解說</span><span class="sxs-lookup"><span data-stu-id="3c7a0-183">Component Authoring Walkthroughs</span></span>](https://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 [<span data-ttu-id="3c7a0-184">操作說明：在選擇工具箱項目對話方塊中顯示控制項</span><span class="sxs-lookup"><span data-stu-id="3c7a0-184">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [<span data-ttu-id="3c7a0-185">逐步解說：使用 Visual C# 撰寫複合控制項</span><span class="sxs-lookup"><span data-stu-id="3c7a0-185">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)
