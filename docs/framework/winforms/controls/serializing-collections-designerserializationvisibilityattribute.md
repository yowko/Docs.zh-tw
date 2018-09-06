---
title: 逐步解說：使用 DesignerSerializationVisibilityAttribute 序列化標準類型的集合
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- serialization [Windows Forms], collections
- standard types [Windows Forms], collections
- collections [Windows Forms], serializing
- collections [Windows Forms], standard types
ms.assetid: 020c9df4-fdc5-4dae-815a-963ecae5668c
ms.openlocfilehash: 54859b3065e8e9bb9680d8b6bf7946b393f73b9f
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43788077"
---
# <a name="walkthrough-serializing-collections-of-standard-types-with-the-designerserializationvisibilityattribute"></a><span data-ttu-id="55da0-102">逐步解說：使用 DesignerSerializationVisibilityAttribute 序列化標準類型的集合</span><span class="sxs-lookup"><span data-stu-id="55da0-102">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>
<span data-ttu-id="55da0-103">您的自訂控制項有時候會公開為屬性的集合。</span><span class="sxs-lookup"><span data-stu-id="55da0-103">Your custom controls will sometimes expose a collection as a property.</span></span> <span data-ttu-id="55da0-104">本逐步解說示範如何使用<xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>類別來控制如何在設計階段序列化集合。</span><span class="sxs-lookup"><span data-stu-id="55da0-104">This walkthrough demonstrates how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> class to control how a collection is serialized at design time.</span></span> <span data-ttu-id="55da0-105">套用<xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content>集合屬性的值可確保會序列化屬性。</span><span class="sxs-lookup"><span data-stu-id="55da0-105">Applying the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value to your collection property ensures that the property will be serialized.</span></span>  
  
 <span data-ttu-id="55da0-106">若要複製一份清單列出本主題中的程式碼，請參閱[如何： 序列化集合的標準類型使用 DesignerSerializationVisibilityAttribute](https://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)。</span><span class="sxs-lookup"><span data-stu-id="55da0-106">To copy the code in this topic as a single listing, see [How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](https://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55da0-107">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="55da0-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="55da0-108">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="55da0-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="55da0-109">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="55da0-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="55da0-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="55da0-110">Prerequisites</span></span>  
 <span data-ttu-id="55da0-111">若要完成這個逐步解說，您將需要：</span><span class="sxs-lookup"><span data-stu-id="55da0-111">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="55da0-112">若要能夠建立和安裝 Visual Studio 的電腦上執行 Windows Form 應用程式專案有足夠的權限。</span><span class="sxs-lookup"><span data-stu-id="55da0-112">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where Visual Studio is installed.</span></span>  
  
## <a name="creating-a-control-that-has-a-serializable-collection"></a><span data-ttu-id="55da0-113">建立控制項都有一個可序列化的集合</span><span class="sxs-lookup"><span data-stu-id="55da0-113">Creating a Control That Has a Serializable Collection</span></span>  
 <span data-ttu-id="55da0-114">第一個步驟是建立具有可序列化的集合，做為屬性的控制項。</span><span class="sxs-lookup"><span data-stu-id="55da0-114">The first step is to create a control that has a serializable collection as a property.</span></span> <span data-ttu-id="55da0-115">您可以編輯此集合使用的內容**集合編輯器**，您可以從存取**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="55da0-115">You can edit the contents of this collection using the **Collection Editor**, which you can access from the **Properties** window.</span></span>  
  
#### <a name="to-create-a-control-with-a-serializable-collection"></a><span data-ttu-id="55da0-116">若要建立具有可序列化集合的控制項</span><span class="sxs-lookup"><span data-stu-id="55da0-116">To create a control with a serializable collection</span></span>  
  
1.  <span data-ttu-id="55da0-117">建立 Windows 控制項程式庫專案，稱為`SerializationDemoControlLib`。</span><span class="sxs-lookup"><span data-stu-id="55da0-117">Create a Windows Control Library project called `SerializationDemoControlLib`.</span></span> <span data-ttu-id="55da0-118">如需詳細資訊，請參閱 < [Windows 控制項程式庫範本](https://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4)。</span><span class="sxs-lookup"><span data-stu-id="55da0-118">For more information, see [Windows Control Library Template](https://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span></span>  
  
2.  <span data-ttu-id="55da0-119">重新命名`UserControl1`至`SerializationDemoControl`。</span><span class="sxs-lookup"><span data-stu-id="55da0-119">Rename `UserControl1` to `SerializationDemoControl`.</span></span> <span data-ttu-id="55da0-120">如需詳細資訊，請參閱 <<c0> [ 如何： 重新命名識別項](https://msdn.microsoft.com/library/2430f732-2b70-4516-8cf6-a7bb71cc9724)。</span><span class="sxs-lookup"><span data-stu-id="55da0-120">For more information, see [How to: Rename Identifiers](https://msdn.microsoft.com/library/2430f732-2b70-4516-8cf6-a7bb71cc9724).</span></span>  
  
3.  <span data-ttu-id="55da0-121">在 **屬性**視窗中，設定的值<xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType>屬性設`10`。</span><span class="sxs-lookup"><span data-stu-id="55da0-121">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> property to `10`.</span></span>  
  
4.  <span data-ttu-id="55da0-122">地方<xref:System.Windows.Forms.TextBox>控制在`SerializationDemoControl`。</span><span class="sxs-lookup"><span data-stu-id="55da0-122">Place a <xref:System.Windows.Forms.TextBox> control in the `SerializationDemoControl`.</span></span>  
  
5.  <span data-ttu-id="55da0-123">選取 <xref:System.Windows.Forms.TextBox> 控制項。</span><span class="sxs-lookup"><span data-stu-id="55da0-123">Select the <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="55da0-124">在 [**屬性**] 視窗中，設定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="55da0-124">In the **Properties** window, set the following properties.</span></span>  
  
    |<span data-ttu-id="55da0-125">屬性</span><span class="sxs-lookup"><span data-stu-id="55da0-125">Property</span></span>|<span data-ttu-id="55da0-126">變更為</span><span class="sxs-lookup"><span data-stu-id="55da0-126">Change to</span></span>|  
    |--------------|---------------|  
    |<span data-ttu-id="55da0-127">**多行**</span><span class="sxs-lookup"><span data-stu-id="55da0-127">**Multiline**</span></span>|`true`|  
    |<span data-ttu-id="55da0-128">**停駐**</span><span class="sxs-lookup"><span data-stu-id="55da0-128">**Dock**</span></span>|<xref:System.Windows.Forms.DockStyle.Fill>|  
    |<span data-ttu-id="55da0-129">**捲軸**</span><span class="sxs-lookup"><span data-stu-id="55da0-129">**ScrollBars**</span></span>|<xref:System.Windows.Forms.ScrollBars.Vertical>|  
    |<span data-ttu-id="55da0-130">**ReadOnly**</span><span class="sxs-lookup"><span data-stu-id="55da0-130">**ReadOnly**</span></span>|`true`|  
  
6.  <span data-ttu-id="55da0-131">在 **程式碼編輯器**，宣告名為字串陣列欄位`stringsValue`在`SerializationDemoControl`。</span><span class="sxs-lookup"><span data-stu-id="55da0-131">In the **Code Editor**, declare a string array field named `stringsValue` in `SerializationDemoControl`.</span></span>  
  
     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]  
  
7.  <span data-ttu-id="55da0-132">定義`Strings`屬性上的`SerializationDemoControl`。</span><span class="sxs-lookup"><span data-stu-id="55da0-132">Define the `Strings` property on the `SerializationDemoControl`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55da0-133"><xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content>值用來啟用集合的序列化。</span><span class="sxs-lookup"><span data-stu-id="55da0-133">The <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value is used to enable serialization of the collection.</span></span>  
  
 [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
 [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
 [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]  
  
1.  <span data-ttu-id="55da0-134">按下 F5 鍵以建置專案，並且在 **UserControl 測試容器**中執行您的控制項。</span><span class="sxs-lookup"><span data-stu-id="55da0-134">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>  
  
2.  <span data-ttu-id="55da0-135">尋找`Strings`中的屬性<xref:System.Windows.Forms.PropertyGrid>的**UserControl 測試容器**。</span><span class="sxs-lookup"><span data-stu-id="55da0-135">Find the `Strings` property in the <xref:System.Windows.Forms.PropertyGrid> of the **UserControl Test Container**.</span></span> <span data-ttu-id="55da0-136">按一下 `Strings`屬性，然後按一下省略符號 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 按鈕，即可開啟**字串集合編輯器**.</span><span class="sxs-lookup"><span data-stu-id="55da0-136">Click the `Strings` property, then click the ellipsis (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **String Collection Editor**.</span></span>  
  
3.  <span data-ttu-id="55da0-137">輸入中的數個字串**字串集合編輯器**。</span><span class="sxs-lookup"><span data-stu-id="55da0-137">Enter several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="55da0-138">藉由按下 ENTER 鍵，每個字串的結尾分隔。</span><span class="sxs-lookup"><span data-stu-id="55da0-138">Separate them by pressing the ENTER key at the end of each string.</span></span> <span data-ttu-id="55da0-139">按一下 **確定**當您完成輸入字串。</span><span class="sxs-lookup"><span data-stu-id="55da0-139">Click **OK** when you are finished entering strings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55da0-140">您所輸入的字串會出現在<xref:System.Windows.Forms.TextBox>的`SerializationDemoControl`。</span><span class="sxs-lookup"><span data-stu-id="55da0-140">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>  
  
## <a name="serializing-a-collection-property"></a><span data-ttu-id="55da0-141">序列化集合屬性</span><span class="sxs-lookup"><span data-stu-id="55da0-141">Serializing a Collection Property</span></span>  
 <span data-ttu-id="55da0-142">若要測試您的控制項的序列化行為，您會將它放在表單上，並變更集合的內容**集合編輯器**。</span><span class="sxs-lookup"><span data-stu-id="55da0-142">To test the serialization behavior of your control, you will place it on a form and change the contents of the collection with the **Collection Editor**.</span></span> <span data-ttu-id="55da0-143">您可以看到序列化的集合的狀態，藉由查看特殊的設計工具檔案，其中**Windows Form 設計工具**會發出程式碼。</span><span class="sxs-lookup"><span data-stu-id="55da0-143">You can see the serialized collection state by looking at a special designer file, into which the **Windows Forms Designer** emits code.</span></span>  
  
#### <a name="to-serialize-a-collection"></a><span data-ttu-id="55da0-144">將序列化集合</span><span class="sxs-lookup"><span data-stu-id="55da0-144">To serialize a collection</span></span>  
  
1.  <span data-ttu-id="55da0-145">將 Windows 應用程式專案加入方案。</span><span class="sxs-lookup"><span data-stu-id="55da0-145">Add a Windows Application project to the solution.</span></span> <span data-ttu-id="55da0-146">將專案命名為 `SerializationDemoControlTest`。</span><span class="sxs-lookup"><span data-stu-id="55da0-146">Name the project `SerializationDemoControlTest`.</span></span>  
  
2.  <span data-ttu-id="55da0-147">在 **工具箱**，尋找名為  索引標籤**SerializationDemoControlLib 元件**。</span><span class="sxs-lookup"><span data-stu-id="55da0-147">In the **Toolbox**, find the tab named **SerializationDemoControlLib Components**.</span></span> <span data-ttu-id="55da0-148">在此索引標籤中，您會發現`SerializationDemoControl`。</span><span class="sxs-lookup"><span data-stu-id="55da0-148">In this tab, you will find the `SerializationDemoControl`.</span></span> <span data-ttu-id="55da0-149">如需詳細資訊，請參閱[逐步解說：自動將自訂元件填入工具箱](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)。</span><span class="sxs-lookup"><span data-stu-id="55da0-149">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
3.  <span data-ttu-id="55da0-150">位置`SerializationDemoControl`您的表單上。</span><span class="sxs-lookup"><span data-stu-id="55da0-150">Place a `SerializationDemoControl` on your form.</span></span>  
  
4.  <span data-ttu-id="55da0-151">尋找`Strings`中的屬性**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="55da0-151">Find the `Strings` property in the **Properties** window.</span></span> <span data-ttu-id="55da0-152">按一下 `Strings`屬性，然後按一下省略符號 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 按鈕，即可開啟**字串集合編輯器**.</span><span class="sxs-lookup"><span data-stu-id="55da0-152">Click the `Strings` property, then click the ellipsis (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **String Collection Editor**.</span></span>  
  
5.  <span data-ttu-id="55da0-153">輸入中的數個字串**字串集合編輯器**。</span><span class="sxs-lookup"><span data-stu-id="55da0-153">Type several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="55da0-154">藉由按下 ENTER 鍵，每個字串的結尾分隔。</span><span class="sxs-lookup"><span data-stu-id="55da0-154">Separate them by pressing the ENTER key at the end of each string.</span></span> <span data-ttu-id="55da0-155">按一下 **確定**當您完成輸入字串。</span><span class="sxs-lookup"><span data-stu-id="55da0-155">Click **OK** when you are finished entering strings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55da0-156">您所輸入的字串會出現在<xref:System.Windows.Forms.TextBox>的`SerializationDemoControl`。</span><span class="sxs-lookup"><span data-stu-id="55da0-156">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>  
  
1.  <span data-ttu-id="55da0-157">在方案總管中，按一下 [顯示所有檔案] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="55da0-157">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
2.  <span data-ttu-id="55da0-158">開啟**Form1**節點。</span><span class="sxs-lookup"><span data-stu-id="55da0-158">Open the **Form1** node.</span></span> <span data-ttu-id="55da0-159">這是檔案，呼叫的下方**Form1.Designer.cs**或是**Form1.Designer.vb**。</span><span class="sxs-lookup"><span data-stu-id="55da0-159">Beneath it is a file called **Form1.Designer.cs** or **Form1.Designer.vb**.</span></span> <span data-ttu-id="55da0-160">這是在其中的檔案**Windows Form 設計工具**會發出程式碼表示您的表單和其子控制項的設計階段狀態。</span><span class="sxs-lookup"><span data-stu-id="55da0-160">This is the file into which the **Windows Forms Designer** emits code representing the design-time state of your form and its child controls.</span></span> <span data-ttu-id="55da0-161">在 [程式碼編輯器] 中開啟此檔案。</span><span class="sxs-lookup"><span data-stu-id="55da0-161">Open this file in the **Code Editor**.</span></span>  
  
3.  <span data-ttu-id="55da0-162">開啟區域稱為**Windows 表單設計工具產生的程式碼**並尋找 [標記] 區段**serializationDemoControl1**。</span><span class="sxs-lookup"><span data-stu-id="55da0-162">Open the region called **Windows Form Designer generated code** and find the section labeled **serializationDemoControl1**.</span></span> <span data-ttu-id="55da0-163">此標籤之下是代表您控制項的序列化的狀態的程式碼。</span><span class="sxs-lookup"><span data-stu-id="55da0-163">Beneath this label is the code representing the serialized state of your control.</span></span> <span data-ttu-id="55da0-164">您在步驟 5 輸入的字串會出現在指派至`Strings`屬性。</span><span class="sxs-lookup"><span data-stu-id="55da0-164">The strings you typed in step 5 appear in an assignment to the `Strings` property.</span></span> <span data-ttu-id="55da0-165">C# 和 Visual Basic 中的下列程式碼範例顯示程式碼類似於您將會看到您輸入字串"red"、 「 橙色 」 和 「 黃色 」。</span><span class="sxs-lookup"><span data-stu-id="55da0-165">The following code examples in C# and Visual Basic, show code similar to what you will see if you typed the strings "red", "orange", and "yellow".</span></span>  
  
    ```csharp  
    this.serializationDemoControl1.Strings = new string[] {  
            "red",  
            "orange",  
            "yellow"};  
    ```  
    
    ```vb  
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}  
    ```
  
4.  <span data-ttu-id="55da0-166">在 **程式碼編輯器**，變更的值<xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>上`Strings`屬性設<xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>。</span><span class="sxs-lookup"><span data-stu-id="55da0-166">In the **Code Editor**, change the value of the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> on the `Strings` property to <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span></span>  
  
    ```csharp  
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]  
    ```  
    ```vb  
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _  
    ```  
  
5. <span data-ttu-id="55da0-167">重建方案，然後重複步驟 3 和 4。</span><span class="sxs-lookup"><span data-stu-id="55da0-167">Rebuild the solution and repeat steps 3 and 4.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55da0-168">在此情況下， **Windows Form 設計工具**不發出的任何指派`Strings`屬性。</span><span class="sxs-lookup"><span data-stu-id="55da0-168">In this case, the **Windows Forms Designer** emits no assignment to the `Strings` property.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="55da0-169">後續步驟</span><span class="sxs-lookup"><span data-stu-id="55da0-169">Next Steps</span></span>  
 <span data-ttu-id="55da0-170">一旦您知道如何序列化標準類型的集合，請考慮將您的自訂控制項更深入整合至設計階段環境。</span><span class="sxs-lookup"><span data-stu-id="55da0-170">Once you know how to serialize a collection of standard types, consider integrating your custom controls more deeply into the design-time environment.</span></span> <span data-ttu-id="55da0-171">下列主題說明如何增強您的自訂控制項的設計階段整合：</span><span class="sxs-lookup"><span data-stu-id="55da0-171">The following topics describe how to enhance the design-time integration of your custom controls:</span></span>  
  
-   [<span data-ttu-id="55da0-172">設計階段架構</span><span class="sxs-lookup"><span data-stu-id="55da0-172">Design-Time Architecture</span></span>](https://msdn.microsoft.com/library/4881917b-628f-4689-b872-472e4f8a4e3a)  
  
-   [<span data-ttu-id="55da0-173">Windows Forms 控制項中的屬性</span><span class="sxs-lookup"><span data-stu-id="55da0-173">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
  
-   [<span data-ttu-id="55da0-174">設計工具序列化概觀</span><span class="sxs-lookup"><span data-stu-id="55da0-174">Designer Serialization Overview</span></span>](https://msdn.microsoft.com/library/c342635a-aa5f-4281-915b-b013738af15a)  
  
-   [<span data-ttu-id="55da0-175">逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="55da0-175">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
  
## <a name="see-also"></a><span data-ttu-id="55da0-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55da0-176">See Also</span></span>  
 <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>  
 [<span data-ttu-id="55da0-177">設計工具序列化概觀</span><span class="sxs-lookup"><span data-stu-id="55da0-177">Designer Serialization Overview</span></span>](https://msdn.microsoft.com/library/c342635a-aa5f-4281-915b-b013738af15a)  
 [<span data-ttu-id="55da0-178">如何： 序列化標準類型使用 DesignerSerializationVisibilityAttribute 的集合</span><span class="sxs-lookup"><span data-stu-id="55da0-178">How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](https://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)  
 [<span data-ttu-id="55da0-179">逐步解說：自動將自訂元件填入工具箱</span><span class="sxs-lookup"><span data-stu-id="55da0-179">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
