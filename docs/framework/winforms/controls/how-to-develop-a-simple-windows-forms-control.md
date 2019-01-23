---
title: HOW TO：開發簡單的 Windows Forms 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms]
- custom controls [Windows Forms], creating simple controls using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 86cbe435-45b7-4cb4-9b5a-47418369758d
ms.openlocfilehash: 4afa4b9e2c92569df4c8023d7dbfdfb025bf94b5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527623"
---
# <a name="how-to-develop-a-simple-windows-forms-control"></a><span data-ttu-id="385f5-102">HOW TO：開發簡單的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="385f5-102">How to: Develop a Simple Windows Forms Control</span></span>
<span data-ttu-id="385f5-103">本節將逐步引導您完成撰寫自訂 Windows Forms 控制項的重要步驟。</span><span class="sxs-lookup"><span data-stu-id="385f5-103">This section walks you through the key steps for authoring a custom Windows Forms control.</span></span> <span data-ttu-id="385f5-104">在本逐步解說中開發的簡單控制項允許的對齊方式與其<xref:System.Windows.Forms.Control.Text%2A>来變更屬性。</span><span class="sxs-lookup"><span data-stu-id="385f5-104">The simple control developed in this walkthrough allows the alignment of its <xref:System.Windows.Forms.Control.Text%2A> property to be changed.</span></span> <span data-ttu-id="385f5-105">它不會引發或處理事件。</span><span class="sxs-lookup"><span data-stu-id="385f5-105">It does not raise or handle events.</span></span>  
  
### <a name="to-create-a-simple-custom-control"></a><span data-ttu-id="385f5-106">建立簡單自訂控制項</span><span class="sxs-lookup"><span data-stu-id="385f5-106">To create a simple custom control</span></span>  
  
1.  <span data-ttu-id="385f5-107">定義衍生自 <xref:System.Windows.Forms.Control?displayProperty=nameWithType> 的類別。</span><span class="sxs-lookup"><span data-stu-id="385f5-107">Define a class that derives from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
    ```vb  
    Public Class FirstControl  
       Inherits Control  
  
    End Class  
    ```  
  
    ```csharp  
    public class FirstControl:Control {}  
    ```  
  
2.  <span data-ttu-id="385f5-108">定義屬性。</span><span class="sxs-lookup"><span data-stu-id="385f5-108">Define properties.</span></span> <span data-ttu-id="385f5-109">(您不需要定義屬性，因為控制項繼承許多屬性，從<xref:System.Windows.Forms.Control>類別，但大部分的自訂控制項通常會定義其他屬性。)下列程式碼片段會定義名為的屬性`TextAlignment`所`FirstControl`使用的顯示格式<xref:System.Windows.Forms.Control.Text%2A>屬性繼承自<xref:System.Windows.Forms.Control>。</span><span class="sxs-lookup"><span data-stu-id="385f5-109">(You are not required to define properties, because a control inherits many properties from the <xref:System.Windows.Forms.Control> class, but most custom controls generally do define additional properties.) The following code fragment defines a property named `TextAlignment` that `FirstControl` uses to format the display of the <xref:System.Windows.Forms.Control.Text%2A> property inherited from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="385f5-110">如需有關定義屬性的詳細資訊，請參閱[屬性概觀](https://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52)。</span><span class="sxs-lookup"><span data-stu-id="385f5-110">For more information about defining properties, see [Properties Overview](https://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]  
  
     <span data-ttu-id="385f5-111">當您設定可變更控制項的視覺顯示屬性時，您必須叫用<xref:System.Windows.Forms.Control.Invalidate%2A>方法來重繪控制項。</span><span class="sxs-lookup"><span data-stu-id="385f5-111">When you set a property that changes the visual display of the control, you must invoke the <xref:System.Windows.Forms.Control.Invalidate%2A> method to redraw the control.</span></span> <span data-ttu-id="385f5-112"><xref:System.Windows.Forms.Control.Invalidate%2A> 定義於基底類別<xref:System.Windows.Forms.Control>。</span><span class="sxs-lookup"><span data-stu-id="385f5-112"><xref:System.Windows.Forms.Control.Invalidate%2A> is defined in the base class <xref:System.Windows.Forms.Control>.</span></span>  
  
3.  <span data-ttu-id="385f5-113">覆寫受保護<xref:System.Windows.Forms.Control.OnPaint%2A>方法繼承自<xref:System.Windows.Forms.Control>提供呈現邏輯移至您的控制項。</span><span class="sxs-lookup"><span data-stu-id="385f5-113">Override the protected <xref:System.Windows.Forms.Control.OnPaint%2A> method inherited from <xref:System.Windows.Forms.Control> to provide rendering logic to your control.</span></span> <span data-ttu-id="385f5-114">如果您不會覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>，您的控制項將無法繪製本身。</span><span class="sxs-lookup"><span data-stu-id="385f5-114">If you do not override <xref:System.Windows.Forms.Control.OnPaint%2A>, your control will not be able to draw itself.</span></span> <span data-ttu-id="385f5-115">在下列程式碼片段中，<xref:System.Windows.Forms.Control.OnPaint%2A>方法會顯示<xref:System.Windows.Forms.Control.Text%2A>屬性繼承自<xref:System.Windows.Forms.Control>所指定的對齊`alignmentValue`欄位。</span><span class="sxs-lookup"><span data-stu-id="385f5-115">In the following code fragment, the <xref:System.Windows.Forms.Control.OnPaint%2A> method displays the <xref:System.Windows.Forms.Control.Text%2A> property inherited from <xref:System.Windows.Forms.Control> with the alignment specified by the `alignmentValue` field.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]  
  
4.  <span data-ttu-id="385f5-116">為您的控制項提供屬性 (attribute)。</span><span class="sxs-lookup"><span data-stu-id="385f5-116">Provide attributes for your control.</span></span> <span data-ttu-id="385f5-117">屬性可讓視覺化設計工具在設計階段適當地顯示您的控制項及其屬性與事件。</span><span class="sxs-lookup"><span data-stu-id="385f5-117">Attributes enable a visual designer to display your control and its properties and events appropriately at design time.</span></span> <span data-ttu-id="385f5-118">下列程式碼片段會將屬性 (attribute) 套用至 `TextAlignment` 屬性 (property)。</span><span class="sxs-lookup"><span data-stu-id="385f5-118">The following code fragment applies attributes to the `TextAlignment` property.</span></span> <span data-ttu-id="385f5-119">Visual Studio 中，例如設計工具中<xref:System.ComponentModel.CategoryAttribute.Category%2A>屬性 （如程式碼片段所示） 會造成屬性會顯示在邏輯類別之下。</span><span class="sxs-lookup"><span data-stu-id="385f5-119">In a designer such as Visual Studio, the <xref:System.ComponentModel.CategoryAttribute.Category%2A> attribute (shown in the code fragment) causes the property to be displayed under a logical category.</span></span> <span data-ttu-id="385f5-120"><xref:System.ComponentModel.DescriptionAttribute.Description%2A>屬性會造成描述性字串顯示在底部**屬性** 視窗時`TextAlignment`選取屬性。</span><span class="sxs-lookup"><span data-stu-id="385f5-120">The <xref:System.ComponentModel.DescriptionAttribute.Description%2A> attribute causes a descriptive string to be displayed at the bottom of the **Properties** window when the `TextAlignment` property is selected.</span></span> <span data-ttu-id="385f5-121">如需屬性的詳細資訊，請參閱[元件的設計階段屬性](https://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)。</span><span class="sxs-lookup"><span data-stu-id="385f5-121">For more information about attributes, see [Design-Time Attributes for Components](https://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]  
  
5.  <span data-ttu-id="385f5-122">(選擇性) 為您的控制項提供資源。</span><span class="sxs-lookup"><span data-stu-id="385f5-122">(optional) Provide resources for your control.</span></span> <span data-ttu-id="385f5-123">您可以使用編譯器選項 (`/res` 適用於 C#) 來封裝資源與您的控制項，為您的控制項提供資源 (例如點陣圖)。</span><span class="sxs-lookup"><span data-stu-id="385f5-123">You can provide a resource, such as a bitmap, for your control by using a compiler option (`/res` for C#) to package resources with your control.</span></span> <span data-ttu-id="385f5-124">在執行階段，資源可以使用擷取的方法<xref:System.Resources.ResourceManager>類別。</span><span class="sxs-lookup"><span data-stu-id="385f5-124">At run time, the resource can be retrieved using the methods of the <xref:System.Resources.ResourceManager> class.</span></span> <span data-ttu-id="385f5-125">如需有關建立和使用資源的詳細資訊，請參閱[桌面應用程式中的資源](../../../../docs/framework/resources/index.md)。</span><span class="sxs-lookup"><span data-stu-id="385f5-125">For more information about creating and using resources, see the [Resources in Desktop Apps](../../../../docs/framework/resources/index.md).</span></span>  
  
6.  <span data-ttu-id="385f5-126">編譯及部署您的控制項。</span><span class="sxs-lookup"><span data-stu-id="385f5-126">Compile and deploy your control.</span></span> <span data-ttu-id="385f5-127">若要編譯及部署 `FirstControl,`，請執行下列步驟︰</span><span class="sxs-lookup"><span data-stu-id="385f5-127">To compile and deploy `FirstControl,` execute the following steps:</span></span>  
  
    1.  <span data-ttu-id="385f5-128">將下列範例中的程式碼儲存至原始程式檔 (SimpleForm.cs 或 SimpleForms.vb)。</span><span class="sxs-lookup"><span data-stu-id="385f5-128">Save the code in the following sample to a source file (such as FirstControl.cs or FirstControl.vb).</span></span>  
  
    2.  <span data-ttu-id="385f5-129">將原始程式碼編譯成組件，並將它儲存在您應用程式的目錄中。</span><span class="sxs-lookup"><span data-stu-id="385f5-129">Compile the source code into an assembly and save it in your application's directory.</span></span> <span data-ttu-id="385f5-130">若要達成此目的，請從包含原始程式檔的目錄執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="385f5-130">To accomplish this, execute the following command from the directory that contains the source file.</span></span>  
  
        ```console  
        vbc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.vb  
        ```  
  
        ```console 
        csc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.cs  
        ```  
  
         <span data-ttu-id="385f5-131">`/t:library` 編譯器選項會告知編譯器您所建立的組件是程式庫 (而不是可執行檔)。</span><span class="sxs-lookup"><span data-stu-id="385f5-131">The `/t:library` compiler option tells the compiler that the assembly you are creating is a library (and not an executable).</span></span> <span data-ttu-id="385f5-132">`/out` 選項指定組件的路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="385f5-132">The `/out` option specifies the path and name of the assembly.</span></span> <span data-ttu-id="385f5-133">`/r` 選項會提供您的程式碼所參考的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="385f5-133">The`/r` option provides the name of the assemblies that are referenced by your code.</span></span> <span data-ttu-id="385f5-134">在此範例中，您會建立只有您的應用程式可以使用的私人組件。</span><span class="sxs-lookup"><span data-stu-id="385f5-134">In this example, you create a private assembly that only your applications can use.</span></span> <span data-ttu-id="385f5-135">因此，您必須將它儲存在您應用程式的目錄中。</span><span class="sxs-lookup"><span data-stu-id="385f5-135">Hence, you have to save it in your application's directory.</span></span> <span data-ttu-id="385f5-136">如需有關封裝和部署控制項以供散發的詳細資訊，請參閱[部署](../../../../docs/framework/deployment/index.md)。</span><span class="sxs-lookup"><span data-stu-id="385f5-136">For more information about packaging and deploying a control for distribution, see [Deployment](../../../../docs/framework/deployment/index.md).</span></span>  
  
 <span data-ttu-id="385f5-137">下列範例顯示 `FirstControl` 的程式碼。</span><span class="sxs-lookup"><span data-stu-id="385f5-137">The following sample shows the code for `FirstControl`.</span></span> <span data-ttu-id="385f5-138">控制項會包含在 `CustomWinControls` 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="385f5-138">The control is enclosed in the namespace `CustomWinControls`.</span></span> <span data-ttu-id="385f5-139">命名空間會提供相關類型的邏輯分組。</span><span class="sxs-lookup"><span data-stu-id="385f5-139">A namespace provides a logical grouping of related types.</span></span> <span data-ttu-id="385f5-140">您可以在新的或現有命名空間中建立您的控制項。</span><span class="sxs-lookup"><span data-stu-id="385f5-140">You can create your control in a new or existing namespace.</span></span> <span data-ttu-id="385f5-141">在 C# 中，`using` 宣告 (在 Visual Basic 中為 `Imports`) 允許從命名空間存取類型，而不需使用完整的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="385f5-141">In C#, the `using` declaration (in Visual Basic, `Imports`) allows types to be accessed from a namespace without using the fully qualified name of the type.</span></span> <span data-ttu-id="385f5-142">在下列範例中，`using`宣告可讓程式碼，以存取該類別<xref:System.Windows.Forms.Control>從<xref:System.Windows.Forms?displayProperty=nameWithType>只要<xref:System.Windows.Forms.Control>而不需使用完整格式的名稱<xref:System.Windows.Forms.Control?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="385f5-142">In the following example, the `using` declaration allows code to access the class <xref:System.Windows.Forms.Control> from <xref:System.Windows.Forms?displayProperty=nameWithType> as simply <xref:System.Windows.Forms.Control> instead of having to use the fully qualified name <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
 [!code-vb[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]  
  
## <a name="using-the-custom-control-on-a-form"></a><span data-ttu-id="385f5-143">在表單上使用自訂控制項</span><span class="sxs-lookup"><span data-stu-id="385f5-143">Using the Custom Control on a Form</span></span>  
 <span data-ttu-id="385f5-144">下列範例顯示一個使用 `FirstControl` 的簡單表單。</span><span class="sxs-lookup"><span data-stu-id="385f5-144">The following example shows a simple form that uses `FirstControl`.</span></span> <span data-ttu-id="385f5-145">它會建立三個 `FirstControl` 執行個體，各有不同的 `TextAlignment` 值。</span><span class="sxs-lookup"><span data-stu-id="385f5-145">It creates three instances of `FirstControl`, each with a different value for the `TextAlignment` property.</span></span>  
  
#### <a name="to-compile-and-run-this-sample"></a><span data-ttu-id="385f5-146">若要編譯和執行這個範例</span><span class="sxs-lookup"><span data-stu-id="385f5-146">To compile and run this sample</span></span>  
  
1.  <span data-ttu-id="385f5-147">將下列範例中的程式碼儲存至原始程式檔 (SimpleForm.cs 或 SimpleForms.vb)。</span><span class="sxs-lookup"><span data-stu-id="385f5-147">Save the code in the following example to a source file (SimpleForm.cs or SimpleForms.vb).</span></span>  
  
2.  <span data-ttu-id="385f5-148">從包含原始程式檔的目錄執行下列命令，將原始程式檔編譯成可執行檔的組件。</span><span class="sxs-lookup"><span data-stu-id="385f5-148">Compile the source code into an executable assembly by executing the following command from the directory that contains the source file.</span></span>  
  
    ```console  
    vbc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.vb  
    ```  
  
    ```console 
    csc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.cs  
    ```  
  
     <span data-ttu-id="385f5-149">CustomWinControls.dll 是包含類別的組件`FirstControl`。</span><span class="sxs-lookup"><span data-stu-id="385f5-149">CustomWinControls.dll is the assembly that contains the class `FirstControl`.</span></span> <span data-ttu-id="385f5-150">此組件所在的目錄必須與存取該組件之表單的原始程式檔 (SimpleForm.cs 或 SimpleForms.vb) 相同。</span><span class="sxs-lookup"><span data-stu-id="385f5-150">This assembly must be in the same directory as the source file for the form that accesses it (SimpleForm.cs or SimpleForms.vb).</span></span>  
  
3.  <span data-ttu-id="385f5-151">使用下列命令執行 SimpleForm.exe。</span><span class="sxs-lookup"><span data-stu-id="385f5-151">Execute SimpleForm.exe using the following command.</span></span>  
  
    ```console
    SimpleForm  
    ```  
  
 [!code-csharp[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
 [!code-vb[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="385f5-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="385f5-152">See also</span></span>
- [<span data-ttu-id="385f5-153">Windows Forms 控制項中的屬性</span><span class="sxs-lookup"><span data-stu-id="385f5-153">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
- [<span data-ttu-id="385f5-154">Windows Forms 控制項中的事件</span><span class="sxs-lookup"><span data-stu-id="385f5-154">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)
