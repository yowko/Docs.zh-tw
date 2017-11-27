---
title: "逐步解說：使用 Visual C# 繼承自 Windows Form 控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: 09476da0-8d4c-4a4c-b969-649519dfb438
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 668dd3624d06f916b23ec16dd8268d2bae4ffcf7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-c"></a><span data-ttu-id="b0d05-102">逐步解說：使用 Visual C# 繼承自 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="b0d05-102">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span> #
<span data-ttu-id="b0d05-103">使用 [!INCLUDE[csprcslong](../../../../includes/csprcslong-md.md)]，您可以透過「繼承」建立功能強大的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="b0d05-103">With [!INCLUDE[csprcslong](../../../../includes/csprcslong-md.md)], you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="b0d05-104">您可以透過繼承建立控制項，不僅保留標準 Windows Forms 控制項的所有固有功能，同時也納入自訂功能。</span><span class="sxs-lookup"><span data-stu-id="b0d05-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="b0d05-105">在本逐步解說中，您將會建立簡單的繼承控制項，名為 `ValueButton`。</span><span class="sxs-lookup"><span data-stu-id="b0d05-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="b0d05-106">這個按鈕就會繼承標準 Windows Form 功能<xref:System.Windows.Forms.Button>控制項，然後將公開名為的自訂屬性`ButtonValue`。</span><span class="sxs-lookup"><span data-stu-id="b0d05-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0d05-107">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="b0d05-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b0d05-108">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="b0d05-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="b0d05-109">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="b0d05-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="b0d05-110">建立專案</span><span class="sxs-lookup"><span data-stu-id="b0d05-110">Creating the Project</span></span>  
 <span data-ttu-id="b0d05-111">當您建立新的專案時，您會指定其名稱以設定根命名空間、組件名稱和專案名稱，並且確定預設元件將會在正確的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="b0d05-111">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="b0d05-112">若要建立 ValueButtonLib 控制項程式庫和 ValueButton 控制項</span><span class="sxs-lookup"><span data-stu-id="b0d05-112">To create the ValueButtonLib control library and the ValueButton control</span></span>  
  
1.  <span data-ttu-id="b0d05-113">在 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]，開啟 [新增專案] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b0d05-113">On the **File** menu, point to **New** and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="b0d05-114">從 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 專案的清單中選取 **Windows Forms 控制項程式庫**專案範本，在 [名稱] 方塊中輸入 `ValueButtonLib`。</span><span class="sxs-lookup"><span data-stu-id="b0d05-114">Select the **Windows Forms Control Library** project template from the list of [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] Projects, and type `ValueButtonLib` in the **Name** box.</span></span>  
  
     <span data-ttu-id="b0d05-115">專案名稱，`ValueButtonLib`，預設也會指派給根命名空間。</span><span class="sxs-lookup"><span data-stu-id="b0d05-115">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="b0d05-116">根命名空間是用來限定組件中的元件名稱。</span><span class="sxs-lookup"><span data-stu-id="b0d05-116">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="b0d05-117">例如，如果兩個組件提供元件，名為 `ValueButton`，您可以使用 `ValueButtonLib.ValueButton` 指定您的 `ValueButton` 元件。</span><span class="sxs-lookup"><span data-stu-id="b0d05-117">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="b0d05-118">如需詳細資訊，請參閱[命名空間](../../../csharp/programming-guide/namespaces/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b0d05-118">For more information, see [Namespaces](../../../csharp/programming-guide/namespaces/index.md).</span></span>  
  
3.  <span data-ttu-id="b0d05-119">在 [方案總管] 中，以滑鼠右鍵按一下 [UserControl1.cs]，然後從捷徑功能表選擇 [重新命名]。</span><span class="sxs-lookup"><span data-stu-id="b0d05-119">In **Solution Explorer**, right-click **UserControl1.cs**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="b0d05-120">將檔案名稱變更為 `ValueButton.cs`。</span><span class="sxs-lookup"><span data-stu-id="b0d05-120">Change the file name to `ValueButton.cs`.</span></span> <span data-ttu-id="b0d05-121">當系統詢問您是否要重新命名程式碼元素 '`UserControl1`' 的所有參考時，按一下 [是]按鈕。</span><span class="sxs-lookup"><span data-stu-id="b0d05-121">Click the **Yes** button when you are asked if you want to rename all references to the code element '`UserControl1`'.</span></span>  
  
4.  <span data-ttu-id="b0d05-122">在 [方案總管] 中，以滑鼠右鍵按一下 [ValueButton.cs]，然後選取 [檢視程式碼]。</span><span class="sxs-lookup"><span data-stu-id="b0d05-122">In **Solution Explorer**, right-click **ValueButton.cs** and select **View Code**.</span></span>  
  
5.  <span data-ttu-id="b0d05-123">找出`class`陳述式行`public partial class ValueButton`，並將變更從這個控制項繼承的類型<xref:System.Windows.Forms.UserControl>至<xref:System.Windows.Forms.Button>。</span><span class="sxs-lookup"><span data-stu-id="b0d05-123">Locate the `class` statement line, `public partial class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="b0d05-124">這可讓繼承的控制項可以繼承的所有功能<xref:System.Windows.Forms.Button>控制項。</span><span class="sxs-lookup"><span data-stu-id="b0d05-124">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>  
  
6.  <span data-ttu-id="b0d05-125">在 [方案總管] 中，開啟 [ValueButton.cs] 節點以顯示設計工具產生的程式碼檔案，**ValueButton.Designer.cs**。</span><span class="sxs-lookup"><span data-stu-id="b0d05-125">In **Solution Explorer**, open the **ValueButton.cs** node to display the designer-generated code file, **ValueButton.Designer.cs**.</span></span> <span data-ttu-id="b0d05-126">在 [程式碼編輯器] 中開啟此檔案。</span><span class="sxs-lookup"><span data-stu-id="b0d05-126">Open this file in the **Code Editor**.</span></span>  
  
7.  <span data-ttu-id="b0d05-127">找出`InitializeComponent`方法並移除指定的行<xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="b0d05-127">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="b0d05-128">這個屬性不存在於<xref:System.Windows.Forms.Button>控制項。</span><span class="sxs-lookup"><span data-stu-id="b0d05-128">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>  
  
8.  <span data-ttu-id="b0d05-129">從 [檔案] 功能表選擇 [全部儲存] 以儲存專案。</span><span class="sxs-lookup"><span data-stu-id="b0d05-129">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b0d05-130">視覺化設計工具再也無法使用。</span><span class="sxs-lookup"><span data-stu-id="b0d05-130">A visual designer is no longer available.</span></span> <span data-ttu-id="b0d05-131">因為<xref:System.Windows.Forms.Button>控制項沒有自己的繪製，您就無法修改其設計工具中的外觀。</span><span class="sxs-lookup"><span data-stu-id="b0d05-131">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="b0d05-132">其視覺表示法將會完全與它所繼承的類別相同 (也就是<xref:System.Windows.Forms.Button>) 除非修改程式碼中。</span><span class="sxs-lookup"><span data-stu-id="b0d05-132">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span> <span data-ttu-id="b0d05-133">您仍然可以將元件 (其中沒有任何 UI 元素) 新增至設計介面。</span><span class="sxs-lookup"><span data-stu-id="b0d05-133">You can still add components, which have no UI elements, to the design surface.</span></span>  
  
## <a name="adding-a-property-to-your-inherited-control"></a><span data-ttu-id="b0d05-134">將屬性新增至繼承的控制項</span><span class="sxs-lookup"><span data-stu-id="b0d05-134">Adding a Property to Your Inherited Control</span></span>  
 <span data-ttu-id="b0d05-135">繼承 Windows Forms 控制項的可能用法之一是建立外觀及操作與標準的 Windows Forms 控制項相同的控制項，但是公開自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="b0d05-135">One possible use of inherited Windows Forms controls is the creation of controls that are identical in look and feel of standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="b0d05-136">在本節中，您會將名為 `ButtonValue` 的屬性新增至您的控制項。</span><span class="sxs-lookup"><span data-stu-id="b0d05-136">In this section, you will add a property called `ButtonValue` to your control.</span></span>  
  
#### <a name="to-add-the-value-property"></a><span data-ttu-id="b0d05-137">若要新增 Value 屬性</span><span class="sxs-lookup"><span data-stu-id="b0d05-137">To add the Value property</span></span>  
  
1.  <span data-ttu-id="b0d05-138">在 [方案總管] 中，以滑鼠右鍵按一下 [ValueButton.cs]，然後從捷徑功能表按一下 [檢視程式碼]。</span><span class="sxs-lookup"><span data-stu-id="b0d05-138">In **Solution Explorer**, right-click **ValueButton.cs**, and then click **View Code** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="b0d05-139">尋找 `class` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b0d05-139">Locate the `class` statement.</span></span> <span data-ttu-id="b0d05-140">緊接在 `{` 後面，輸入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="b0d05-140">Immediately after the `{`, type the following code:</span></span>  
  
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
  
     <span data-ttu-id="b0d05-141">此程式碼會設定方法，系統會使用該方法來儲存和擷取 `ButtonValue` 屬性。</span><span class="sxs-lookup"><span data-stu-id="b0d05-141">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="b0d05-142">`get` 陳述式會將傳回值設為儲存在私用變數 `varValue` 的值，而 `set` 陳述式會使用 `value` 關鍵字設定私用變數的值。</span><span class="sxs-lookup"><span data-stu-id="b0d05-142">The `get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `set` statement sets the value of the private variable by use of the `value` keyword.</span></span>  
  
3.  <span data-ttu-id="b0d05-143">從 [檔案] 功能表選擇 [全部儲存] 以儲存專案。</span><span class="sxs-lookup"><span data-stu-id="b0d05-143">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
## <a name="testing-your-control"></a><span data-ttu-id="b0d05-144">測試您的控制項</span><span class="sxs-lookup"><span data-stu-id="b0d05-144">Testing Your Control</span></span>  
 <span data-ttu-id="b0d05-145">控制項不是獨立專案；它們必須裝載在容器中。</span><span class="sxs-lookup"><span data-stu-id="b0d05-145">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="b0d05-146">若要測試您的控制項，您必須提供測試專案讓控制項在其中執行。</span><span class="sxs-lookup"><span data-stu-id="b0d05-146">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="b0d05-147">您也必須藉由建置 (編譯) 控制項，讓控制項可供測試專案存取。</span><span class="sxs-lookup"><span data-stu-id="b0d05-147">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="b0d05-148">在本節中，您將會建置您的控制項，並且在 Windows Form 中進行測試。</span><span class="sxs-lookup"><span data-stu-id="b0d05-148">In this section, you will build your control and test it in a Windows Form.</span></span>  
  
#### <a name="to-build-your-control"></a><span data-ttu-id="b0d05-149">若要建置您的控制項</span><span class="sxs-lookup"><span data-stu-id="b0d05-149">To build your control</span></span>  
  
1.  <span data-ttu-id="b0d05-150">在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。</span><span class="sxs-lookup"><span data-stu-id="b0d05-150">On the **Build** menu, click **Build Solution**.</span></span>  
  
     <span data-ttu-id="b0d05-151">建置應該會成功，沒有編譯器錯誤或警告。</span><span class="sxs-lookup"><span data-stu-id="b0d05-151">The build should be successful with no compiler errors or warnings.</span></span>  
  
#### <a name="to-create-a-test-project"></a><span data-ttu-id="b0d05-152">若要建立測試專案</span><span class="sxs-lookup"><span data-stu-id="b0d05-152">To create a test project</span></span>  
  
1.  <span data-ttu-id="b0d05-153">在 [檔案] 功能表上，指向 [新增]，然後選取 [新增專案]，以開啟 [加入新的專案]對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b0d05-153">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="b0d05-154">選取 [Visual C#] 節點下方的 [Windows] 節點，然後按一下 [Windows Forms 應用程式]。</span><span class="sxs-lookup"><span data-stu-id="b0d05-154">Select the **Windows** node, beneath the **Visual C#** node, and click **Windows Forms Application**.</span></span>  
  
3.  <span data-ttu-id="b0d05-155">在 [名稱] 方塊中，輸入 `Test`。</span><span class="sxs-lookup"><span data-stu-id="b0d05-155">In the **Name** box, type `Test`.</span></span>  
  
4.  <span data-ttu-id="b0d05-156">在 [方案總管] 中，以滑鼠右鍵按一下測試專案的 [參考] 節點，然後從捷徑功能表選取 [加入參考]，以顯示 [加入參考] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b0d05-156">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>  
  
5.  <span data-ttu-id="b0d05-157">按一下標籤為 [專案] 的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b0d05-157">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="b0d05-158">您的 `ValueButtonLib` 專案會列在 [專案名稱] 底下。</span><span class="sxs-lookup"><span data-stu-id="b0d05-158">Your `ValueButtonLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="b0d05-159">按兩下專案以將參考新增至測試專案。</span><span class="sxs-lookup"><span data-stu-id="b0d05-159">Double-click the project to add the reference to the test project.</span></span>  
  
6.  <span data-ttu-id="b0d05-160">在 [方案總管] 中，以滑鼠右鍵按一下 [測試]，然後選取 [建置]。</span><span class="sxs-lookup"><span data-stu-id="b0d05-160">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>  
  
#### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="b0d05-161">若要將控制項新增至表單</span><span class="sxs-lookup"><span data-stu-id="b0d05-161">To add your control to the form</span></span>  
  
1.  <span data-ttu-id="b0d05-162">在 [方案總管] 中，以滑鼠右鍵按一下 [Form1.cs]，然後從捷徑功能表選擇 [檢視表設計工具]。</span><span class="sxs-lookup"><span data-stu-id="b0d05-162">In **Solution Explorer**, right-click **Form1.cs** and choose **View Designer** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="b0d05-163">在 [工具箱] 中，按一下 [ValueButtonLib 元件]。</span><span class="sxs-lookup"><span data-stu-id="b0d05-163">In the **Toolbox**, click **ValueButtonLib Components**.</span></span> <span data-ttu-id="b0d05-164">按兩下 [ValueButton]。</span><span class="sxs-lookup"><span data-stu-id="b0d05-164">Double-click **ValueButton**.</span></span>  
  
     <span data-ttu-id="b0d05-165">[ValueButton] 隨即出現在表單上。</span><span class="sxs-lookup"><span data-stu-id="b0d05-165">A **ValueButton** appears on the form.</span></span>  
  
3.  <span data-ttu-id="b0d05-166">以滑鼠右鍵按一下 [ValueButton]，然後從捷徑功能表選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="b0d05-166">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>  
  
4.  <span data-ttu-id="b0d05-167">在 [屬性] 視窗中，檢查此控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="b0d05-167">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="b0d05-168">請注意，它們與標準按鈕所公開的屬性相同，不同之處是有一個額外屬性，`ButtonValue`。</span><span class="sxs-lookup"><span data-stu-id="b0d05-168">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, `ButtonValue`.</span></span>  
  
5.  <span data-ttu-id="b0d05-169">將 `ButtonValue` 屬性設定為 `5`。</span><span class="sxs-lookup"><span data-stu-id="b0d05-169">Set the `ButtonValue` property to `5`.</span></span>  
  
6.  <span data-ttu-id="b0d05-170">在**所有 Windows Form**  索引標籤**工具箱**，連按兩下**標籤**新增<xref:System.Windows.Forms.Label>控制項加入至表單。</span><span class="sxs-lookup"><span data-stu-id="b0d05-170">In the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>  
  
7.  <span data-ttu-id="b0d05-171">重新將標籤放置在表單的中央。</span><span class="sxs-lookup"><span data-stu-id="b0d05-171">Relocate the label to the center of the form.</span></span>  
  
8.  <span data-ttu-id="b0d05-172">按兩下 `valueButton1`。</span><span class="sxs-lookup"><span data-stu-id="b0d05-172">Double-click `valueButton1`.</span></span>  
  
     <span data-ttu-id="b0d05-173">在 [程式碼編輯器] 中開啟至 `valueButton1_Click` 事件。</span><span class="sxs-lookup"><span data-stu-id="b0d05-173">The **Code Editor** opens to the `valueButton1_Click` event.</span></span>  
  
9. <span data-ttu-id="b0d05-174">插入下列程式碼行。</span><span class="sxs-lookup"><span data-stu-id="b0d05-174">Insert the following line of code.</span></span>  
  
    ```csharp  
    label1.Text = valueButton1.ButtonValue.ToString();  
    ```  
  
10. <span data-ttu-id="b0d05-175">在 [方案總管] 中，以滑鼠右鍵按一下 [測試]，然後從捷徑功能表選擇 [設定為啟始專案]。</span><span class="sxs-lookup"><span data-stu-id="b0d05-175">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>  
  
11. <span data-ttu-id="b0d05-176">從 [偵錯] 功能表中，選取 [開始偵錯]。</span><span class="sxs-lookup"><span data-stu-id="b0d05-176">From the **Debug** menu, select **Start Debugging**.</span></span>  
  
     <span data-ttu-id="b0d05-177">`Form1` 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="b0d05-177">`Form1` appears.</span></span>  
  
12. <span data-ttu-id="b0d05-178">按一下 `valueButton1`。</span><span class="sxs-lookup"><span data-stu-id="b0d05-178">Click `valueButton1`.</span></span>  
  
     <span data-ttu-id="b0d05-179">數字 '5' 會顯示在 `label1` 中，示範繼承的控制項之 `ButtonValue` 屬性已透過 `valueButton1_Click` 方法傳遞至 `label1`。</span><span class="sxs-lookup"><span data-stu-id="b0d05-179">The numeral '5' is displayed in `label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `label1` through the `valueButton1_Click` method.</span></span> <span data-ttu-id="b0d05-180">因此，`ValueButton` 控制項會繼承標準 Windows Forms 按鈕的所有功能，但是會公開額外的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="b0d05-180">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0d05-181">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0d05-181">See Also</span></span>  
 [<span data-ttu-id="b0d05-182">使用元件進行程式設計</span><span class="sxs-lookup"><span data-stu-id="b0d05-182">Programming with Components</span></span>](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)  
 [<span data-ttu-id="b0d05-183">元件撰寫逐步解說</span><span class="sxs-lookup"><span data-stu-id="b0d05-183">Component Authoring Walkthroughs</span></span>](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 [<span data-ttu-id="b0d05-184">操作說明：在選擇工具箱項目對話方塊中顯示控制項</span><span class="sxs-lookup"><span data-stu-id="b0d05-184">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [<span data-ttu-id="b0d05-185">逐步解說：使用 Visual C# 撰寫複合控制項</span><span class="sxs-lookup"><span data-stu-id="b0d05-185">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)
