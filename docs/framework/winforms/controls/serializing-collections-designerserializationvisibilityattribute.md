---
title: "逐步解說：使用 DesignerSerializationVisibilityAttribute 序列化標準類型的集合"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0267020f7e7a52e92b05a0bda0ee397e5c3393fc
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-serializing-collections-of-standard-types-with-the-designerserializationvisibilityattribute"></a><span data-ttu-id="b5561-102">逐步解說：使用 DesignerSerializationVisibilityAttribute 序列化標準類型的集合</span><span class="sxs-lookup"><span data-stu-id="b5561-102">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>
<span data-ttu-id="b5561-103">您的自訂控制項有時會公開為屬性的集合。</span><span class="sxs-lookup"><span data-stu-id="b5561-103">Your custom controls will sometimes expose a collection as a property.</span></span> <span data-ttu-id="b5561-104">本逐步解說示範如何使用<xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>類別來控制如何在設計階段序列化集合。</span><span class="sxs-lookup"><span data-stu-id="b5561-104">This walkthrough demonstrates how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> class to control how a collection is serialized at design time.</span></span> <span data-ttu-id="b5561-105">套用<xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content>集合屬性的值可確保屬性會序列化。</span><span class="sxs-lookup"><span data-stu-id="b5561-105">Applying the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value to your collection property ensures that the property will be serialized.</span></span>  
  
 <span data-ttu-id="b5561-106">若要為單一列出本主題中複製的程式碼，請參閱[How to： 序列化集合的標準類型使用 designerserializationvisibilityattribute 序列化](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)。</span><span class="sxs-lookup"><span data-stu-id="b5561-106">To copy the code in this topic as a single listing, see [How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5561-107">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="b5561-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b5561-108">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="b5561-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="b5561-109">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="b5561-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b5561-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="b5561-110">Prerequisites</span></span>  
 <span data-ttu-id="b5561-111">若要完成這個逐步解說，您將需要：</span><span class="sxs-lookup"><span data-stu-id="b5561-111">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="b5561-112">若要能夠建立及安裝 Visual Studio 的電腦上執行 Windows Form 應用程式專案有足夠的權限。</span><span class="sxs-lookup"><span data-stu-id="b5561-112">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where Visual Studio is installed.</span></span>  
  
## <a name="creating-a-control-that-has-a-serializable-collection"></a><span data-ttu-id="b5561-113">建立控制項具有可序列化集合</span><span class="sxs-lookup"><span data-stu-id="b5561-113">Creating a Control That Has a Serializable Collection</span></span>  
 <span data-ttu-id="b5561-114">第一個步驟是建立具有可序列化的集合，做為屬性的控制項。</span><span class="sxs-lookup"><span data-stu-id="b5561-114">The first step is to create a control that has a serializable collection as a property.</span></span> <span data-ttu-id="b5561-115">您可以編輯此集合使用的內容**集合編輯器**，您可以從存取**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="b5561-115">You can edit the contents of this collection using the **Collection Editor**, which you can access from the **Properties** window.</span></span>  
  
#### <a name="to-create-a-control-with-a-serializable-collection"></a><span data-ttu-id="b5561-116">若要建立具有可序列化集合的控制項</span><span class="sxs-lookup"><span data-stu-id="b5561-116">To create a control with a serializable collection</span></span>  
  
1.  <span data-ttu-id="b5561-117">建立 Windows 控制項程式庫專案，稱為`SerializationDemoControlLib`。</span><span class="sxs-lookup"><span data-stu-id="b5561-117">Create a Windows Control Library project called `SerializationDemoControlLib`.</span></span> <span data-ttu-id="b5561-118">如需詳細資訊，請參閱[Windows 控制項程式庫範本](http://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4)。</span><span class="sxs-lookup"><span data-stu-id="b5561-118">For more information, see [Windows Control Library Template](http://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span></span>  
  
2.  <span data-ttu-id="b5561-119">重新命名`UserControl1`至`SerializationDemoControl`。</span><span class="sxs-lookup"><span data-stu-id="b5561-119">Rename `UserControl1` to `SerializationDemoControl`.</span></span> <span data-ttu-id="b5561-120">如需詳細資訊，請參閱[如何： 重新命名識別項](http://msdn.microsoft.com/library/2430f732-2b70-4516-8cf6-a7bb71cc9724)。</span><span class="sxs-lookup"><span data-stu-id="b5561-120">For more information, see [How to: Rename Identifiers](http://msdn.microsoft.com/library/2430f732-2b70-4516-8cf6-a7bb71cc9724).</span></span>  
  
3.  <span data-ttu-id="b5561-121">在**屬性**視窗中，設定的值<xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType>屬性`10`。</span><span class="sxs-lookup"><span data-stu-id="b5561-121">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> property to `10`.</span></span>  
  
4.  <span data-ttu-id="b5561-122">位置<xref:System.Windows.Forms.TextBox>控制`SerializationDemoControl`。</span><span class="sxs-lookup"><span data-stu-id="b5561-122">Place a <xref:System.Windows.Forms.TextBox> control in the `SerializationDemoControl`.</span></span>  
  
5.  <span data-ttu-id="b5561-123">選取 <xref:System.Windows.Forms.TextBox> 控制項。</span><span class="sxs-lookup"><span data-stu-id="b5561-123">Select the <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="b5561-124">在**屬性**視窗中，設定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="b5561-124">In the **Properties** window, set the following properties.</span></span>  
  
    |<span data-ttu-id="b5561-125">屬性</span><span class="sxs-lookup"><span data-stu-id="b5561-125">Property</span></span>|<span data-ttu-id="b5561-126">變更為</span><span class="sxs-lookup"><span data-stu-id="b5561-126">Change to</span></span>|  
    |--------------|---------------|  
    |<span data-ttu-id="b5561-127">**多行**</span><span class="sxs-lookup"><span data-stu-id="b5561-127">**Multiline**</span></span>|`true`|  
    |<span data-ttu-id="b5561-128">**Dock**</span><span class="sxs-lookup"><span data-stu-id="b5561-128">**Dock**</span></span>|<xref:System.Windows.Forms.DockStyle.Fill>|  
    |<span data-ttu-id="b5561-129">**捲軸**</span><span class="sxs-lookup"><span data-stu-id="b5561-129">**ScrollBars**</span></span>|<xref:System.Windows.Forms.ScrollBars.Vertical>|  
    |<span data-ttu-id="b5561-130">**ReadOnly**</span><span class="sxs-lookup"><span data-stu-id="b5561-130">**ReadOnly**</span></span>|`true`|  
  
6.  <span data-ttu-id="b5561-131">在**程式碼編輯器**，宣告名為字串陣列欄位`stringsValue`中`SerializationDemoControl`。</span><span class="sxs-lookup"><span data-stu-id="b5561-131">In the **Code Editor**, declare a string array field named `stringsValue` in `SerializationDemoControl`.</span></span>  
  
     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]  
  
7.  <span data-ttu-id="b5561-132">定義`Strings`屬性`SerializationDemoControl`。</span><span class="sxs-lookup"><span data-stu-id="b5561-132">Define the `Strings` property on the `SerializationDemoControl`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5561-133"><xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content>值用來啟用的集合序列化。</span><span class="sxs-lookup"><span data-stu-id="b5561-133">The <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value is used to enable serialization of the collection.</span></span>  
  
 [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
 [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
 [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]  
  
1.  <span data-ttu-id="b5561-134">按下 F5 鍵以建置專案，並且在 **UserControl 測試容器**中執行您的控制項。</span><span class="sxs-lookup"><span data-stu-id="b5561-134">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>  
  
2.  <span data-ttu-id="b5561-135">尋找`Strings`屬性<xref:System.Windows.Forms.PropertyGrid>的**UserControl Test Container**。</span><span class="sxs-lookup"><span data-stu-id="b5561-135">Find the `Strings` property in the <xref:System.Windows.Forms.PropertyGrid> of the **UserControl Test Container**.</span></span> <span data-ttu-id="b5561-136">按一下`Strings`屬性，然後按一下省略符號 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 按鈕來開啟**的字串集合編輯器**.</span><span class="sxs-lookup"><span data-stu-id="b5561-136">Click the `Strings` property, then click the ellipsis (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **String Collection Editor**.</span></span>  
  
3.  <span data-ttu-id="b5561-137">輸入中的數個字串**字串集合編輯器**。</span><span class="sxs-lookup"><span data-stu-id="b5561-137">Enter several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="b5561-138">按 ENTER 鍵，每個字串的結尾分隔。</span><span class="sxs-lookup"><span data-stu-id="b5561-138">Separate them by pressing the ENTER key at the end of each string.</span></span> <span data-ttu-id="b5561-139">按一下**確定**當您完成輸入字串。</span><span class="sxs-lookup"><span data-stu-id="b5561-139">Click **OK** when you are finished entering strings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5561-140">您輸入的字串會出現在<xref:System.Windows.Forms.TextBox>的`SerializationDemoControl`。</span><span class="sxs-lookup"><span data-stu-id="b5561-140">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>  
  
## <a name="serializing-a-collection-property"></a><span data-ttu-id="b5561-141">序列化集合屬性</span><span class="sxs-lookup"><span data-stu-id="b5561-141">Serializing a Collection Property</span></span>  
 <span data-ttu-id="b5561-142">若要測試您的控制項的序列化行為，您會將它放在表單上，並變更與集合的內容**集合編輯器**。</span><span class="sxs-lookup"><span data-stu-id="b5561-142">To test the serialization behavior of your control, you will place it on a form and change the contents of the collection with the **Collection Editor**.</span></span> <span data-ttu-id="b5561-143">您可以藉由查看到其中的一種特殊的設計工具檔案，查看序列化的集合狀態**Windows Form 設計工具**會發出程式碼。</span><span class="sxs-lookup"><span data-stu-id="b5561-143">You can see the serialized collection state by looking at a special designer file, into which the **Windows Forms Designer** emits code.</span></span>  
  
#### <a name="to-serialize-a-collection"></a><span data-ttu-id="b5561-144">將序列化集合</span><span class="sxs-lookup"><span data-stu-id="b5561-144">To serialize a collection</span></span>  
  
1.  <span data-ttu-id="b5561-145">將 Windows 應用程式專案加入方案。</span><span class="sxs-lookup"><span data-stu-id="b5561-145">Add a Windows Application project to the solution.</span></span> <span data-ttu-id="b5561-146">將專案命名為 `SerializationDemoControlTest`。</span><span class="sxs-lookup"><span data-stu-id="b5561-146">Name the project `SerializationDemoControlTest`.</span></span>  
  
2.  <span data-ttu-id="b5561-147">在**工具箱**，尋找名為 [] 索引標籤**SerializationDemoControlLib 元件**。</span><span class="sxs-lookup"><span data-stu-id="b5561-147">In the **Toolbox**, find the tab named **SerializationDemoControlLib Components**.</span></span> <span data-ttu-id="b5561-148">在此索引標籤上，您會發現`SerializationDemoControl`。</span><span class="sxs-lookup"><span data-stu-id="b5561-148">In this tab, you will find the `SerializationDemoControl`.</span></span> <span data-ttu-id="b5561-149">如需詳細資訊，請參閱[逐步解說：自動將自訂元件填入工具箱](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)。</span><span class="sxs-lookup"><span data-stu-id="b5561-149">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
3.  <span data-ttu-id="b5561-150">位置`SerializationDemoControl`表單上。</span><span class="sxs-lookup"><span data-stu-id="b5561-150">Place a `SerializationDemoControl` on your form.</span></span>  
  
4.  <span data-ttu-id="b5561-151">尋找`Strings`屬性**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="b5561-151">Find the `Strings` property in the **Properties** window.</span></span> <span data-ttu-id="b5561-152">按一下`Strings`屬性，然後按一下省略符號 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 按鈕來開啟**的字串集合編輯器**.</span><span class="sxs-lookup"><span data-stu-id="b5561-152">Click the `Strings` property, then click the ellipsis (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **String Collection Editor**.</span></span>  
  
5.  <span data-ttu-id="b5561-153">輸入中的數個字串**字串集合編輯器**。</span><span class="sxs-lookup"><span data-stu-id="b5561-153">Type several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="b5561-154">按 ENTER 鍵，每個字串的結尾分隔。</span><span class="sxs-lookup"><span data-stu-id="b5561-154">Separate them by pressing the ENTER key at the end of each string.</span></span> <span data-ttu-id="b5561-155">按一下**確定**當您完成輸入字串。</span><span class="sxs-lookup"><span data-stu-id="b5561-155">Click **OK** when you are finished entering strings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5561-156">您輸入的字串會出現在<xref:System.Windows.Forms.TextBox>的`SerializationDemoControl`。</span><span class="sxs-lookup"><span data-stu-id="b5561-156">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>  
  
1.  <span data-ttu-id="b5561-157">在方案總管中，按一下 [顯示所有檔案] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b5561-157">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
2.  <span data-ttu-id="b5561-158">開啟**Form1**節點。</span><span class="sxs-lookup"><span data-stu-id="b5561-158">Open the **Form1** node.</span></span> <span data-ttu-id="b5561-159">它是名為的檔案的下方**Form1.Designer.cs**或**Form1.Designer.vb**。</span><span class="sxs-lookup"><span data-stu-id="b5561-159">Beneath it is a file called **Form1.Designer.cs** or **Form1.Designer.vb**.</span></span> <span data-ttu-id="b5561-160">這是到其中的檔案**Windows Form 設計工具**會發出程式碼表示您的表單和其子控制項的設計階段狀態。</span><span class="sxs-lookup"><span data-stu-id="b5561-160">This is the file into which the **Windows Forms Designer** emits code representing the design-time state of your form and its child controls.</span></span> <span data-ttu-id="b5561-161">在 [程式碼編輯器] 中開啟此檔案。</span><span class="sxs-lookup"><span data-stu-id="b5561-161">Open this file in the **Code Editor**.</span></span>  
  
3.  <span data-ttu-id="b5561-162">開啟呼叫區域**Windows Form 設計工具產生的程式碼**和尋找標示為區段**serializationDemoControl1**。</span><span class="sxs-lookup"><span data-stu-id="b5561-162">Open the region called **Windows Form Designer generated code** and find the section labeled **serializationDemoControl1**.</span></span> <span data-ttu-id="b5561-163">此標籤之下是控制項的代表序列化的狀態的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b5561-163">Beneath this label is the code representing the serialized state of your control.</span></span> <span data-ttu-id="b5561-164">您在步驟 5 中輸入的字串會出現在指派至`Strings`屬性。</span><span class="sxs-lookup"><span data-stu-id="b5561-164">The strings you typed in step 5 appear in an assignment to the `Strings` property.</span></span> <span data-ttu-id="b5561-165">在 C# 和 Visual Basic 中的下列程式碼範例顯示程式碼類似於您將會看到您輸入字串"red"、"橙色 」 和 「 黃色 」。</span><span class="sxs-lookup"><span data-stu-id="b5561-165">The following code examples in C# and Visual Basic, show code similar to what you will see if you typed the strings "red", "orange", and "yellow".</span></span>  
  
    ```csharp  
    this.serializationDemoControl1.Strings = new string[] {  
            "red",  
            "orange",  
            "yellow"};  
    ```  
    
    ```vb  
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}  
    ```
  
4.  <span data-ttu-id="b5561-166">在**程式碼編輯器**，變更的值<xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>上`Strings`屬性<xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>。</span><span class="sxs-lookup"><span data-stu-id="b5561-166">In the **Code Editor**, change the value of the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> on the `Strings` property to <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span></span>  
  
    ```csharp  
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]  
    ```  
    ```vb  
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _  
    ```  
  
5. <span data-ttu-id="b5561-167">重建方案和重複步驟 3 和 4。</span><span class="sxs-lookup"><span data-stu-id="b5561-167">Rebuild the solution and repeat steps 3 and 4.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5561-168">在此情況下， **Windows Form 設計工具**不發出的任何指派`Strings`屬性。</span><span class="sxs-lookup"><span data-stu-id="b5561-168">In this case, the **Windows Forms Designer** emits no assignment to the `Strings` property.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b5561-169">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b5561-169">Next Steps</span></span>  
 <span data-ttu-id="b5561-170">一旦您知道如何序列化標準類型的集合，請考慮將您的自訂控制項更深入整合至設計階段環境。</span><span class="sxs-lookup"><span data-stu-id="b5561-170">Once you know how to serialize a collection of standard types, consider integrating your custom controls more deeply into the design-time environment.</span></span> <span data-ttu-id="b5561-171">下列主題描述如何加強您的自訂控制項的設計階段整合：</span><span class="sxs-lookup"><span data-stu-id="b5561-171">The following topics describe how to enhance the design-time integration of your custom controls:</span></span>  
  
-   [<span data-ttu-id="b5561-172">設計階段架構</span><span class="sxs-lookup"><span data-stu-id="b5561-172">Design-Time Architecture</span></span>](http://msdn.microsoft.com/library/4881917b-628f-4689-b872-472e4f8a4e3a)  
  
-   [<span data-ttu-id="b5561-173">Windows Forms 控制項中的屬性</span><span class="sxs-lookup"><span data-stu-id="b5561-173">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
  
-   [<span data-ttu-id="b5561-174">設計工具序列化概觀</span><span class="sxs-lookup"><span data-stu-id="b5561-174">Designer Serialization Overview</span></span>](http://msdn.microsoft.com/library/c342635a-aa5f-4281-915b-b013738af15a)  
  
-   [<span data-ttu-id="b5561-175">逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="b5561-175">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
  
## <a name="see-also"></a><span data-ttu-id="b5561-176">請參閱</span><span class="sxs-lookup"><span data-stu-id="b5561-176">See Also</span></span>  
 <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>  
 [<span data-ttu-id="b5561-177">設計工具序列化概觀</span><span class="sxs-lookup"><span data-stu-id="b5561-177">Designer Serialization Overview</span></span>](http://msdn.microsoft.com/library/c342635a-aa5f-4281-915b-b013738af15a)  
 [<span data-ttu-id="b5561-178">如何： 使用 designerserializationvisibilityattribute 序列化標準類型的序列化</span><span class="sxs-lookup"><span data-stu-id="b5561-178">How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)  
 [<span data-ttu-id="b5561-179">逐步解說：自動將自訂元件填入工具箱</span><span class="sxs-lookup"><span data-stu-id="b5561-179">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
