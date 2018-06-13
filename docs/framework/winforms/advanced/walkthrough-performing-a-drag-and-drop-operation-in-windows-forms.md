---
title: 逐步解說：在 Windows Form 中執行拖放作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: 6c78a06e37de491e95d56d29c9d2f3e60b88e8ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529450"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a><span data-ttu-id="2a999-102">逐步解說：在 Windows Form 中執行拖放作業</span><span class="sxs-lookup"><span data-stu-id="2a999-102">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>
<span data-ttu-id="2a999-103">若要執行 windows 應用程式中的拖放作業，您必須處理的一系列事件，最值得注意的是<xref:System.Windows.Forms.Control.DragEnter>， <xref:System.Windows.Forms.Control.DragLeave>，和<xref:System.Windows.Forms.Control.DragDrop>事件。</span><span class="sxs-lookup"><span data-stu-id="2a999-103">To perform drag-and-drop operations within Windows-based applications you must handle a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span> <span data-ttu-id="2a999-104">使用這些事件的事件引數中所提供的資訊，即可輕鬆地運用拖放作業。</span><span class="sxs-lookup"><span data-stu-id="2a999-104">By working with the information available in the event arguments of these events, you can easily facilitate drag-and-drop operations.</span></span>  
  
## <a name="dragging-data"></a><span data-ttu-id="2a999-105">拖曳資料</span><span class="sxs-lookup"><span data-stu-id="2a999-105">Dragging Data</span></span>  
 <span data-ttu-id="2a999-106">所有拖放作業都是從拖曳開始。</span><span class="sxs-lookup"><span data-stu-id="2a999-106">All drag-and-drop operations begin with dragging.</span></span> <span data-ttu-id="2a999-107">中實作的功能，可讓資料收集開始拖曳時<xref:System.Windows.Forms.Control.DoDragDrop%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="2a999-107">The functionality to enable data to be collected when dragging begins is implemented in the <xref:System.Windows.Forms.Control.DoDragDrop%2A> method.</span></span>  
  
 <span data-ttu-id="2a999-108">在下列範例中，<xref:System.Windows.Forms.Control.MouseDown>事件可用來開始拖曳作業，因為它是最直覺 （大部分的拖放動作開頭所按下滑鼠按鈕）。</span><span class="sxs-lookup"><span data-stu-id="2a999-108">In the following example, the <xref:System.Windows.Forms.Control.MouseDown> event is used to start the drag operation because it is the most intuitive (most drag-and-drop actions begin with the mouse button being depressed).</span></span> <span data-ttu-id="2a999-109">不過，請記住，可以使用任何事件來啟始拖放程序。</span><span class="sxs-lookup"><span data-stu-id="2a999-109">However, remember that any event could be used to initiate a drag-and-drop procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a999-110">特定控制項會有自訂拖曳特定事件。</span><span class="sxs-lookup"><span data-stu-id="2a999-110">Certain controls have custom drag-specific events.</span></span> <span data-ttu-id="2a999-111"><xref:System.Windows.Forms.ListView>和<xref:System.Windows.Forms.TreeView>控制項，例如，具有<xref:System.Windows.Forms.TreeView.ItemDrag>事件。</span><span class="sxs-lookup"><span data-stu-id="2a999-111">The <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls, for example, have an <xref:System.Windows.Forms.TreeView.ItemDrag> event.</span></span>  
  
#### <a name="to-start-a-drag-operation"></a><span data-ttu-id="2a999-112">啟動拖曳作業</span><span class="sxs-lookup"><span data-stu-id="2a999-112">To start a drag operation</span></span>  
  
1.  <span data-ttu-id="2a999-113">在<xref:System.Windows.Forms.Control.MouseDown>控制項位置將會開始拖曳，請使用事件`DoDragDrop`方法，以設定要拖曳的資料和允許的效果拖曳所擁有。</span><span class="sxs-lookup"><span data-stu-id="2a999-113">In the <xref:System.Windows.Forms.Control.MouseDown> event for the control where the drag will begin, use the `DoDragDrop` method to set the data to be dragged and the allowed effect dragging will have.</span></span> <span data-ttu-id="2a999-114">如需詳細資訊，請參閱 <xref:System.Windows.Forms.DragEventArgs.Data%2A> 與 <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>。</span><span class="sxs-lookup"><span data-stu-id="2a999-114">For more information, see <xref:System.Windows.Forms.DragEventArgs.Data%2A> and <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span></span>  
  
     <span data-ttu-id="2a999-115">下列範例示範如何啟始拖曳作業。</span><span class="sxs-lookup"><span data-stu-id="2a999-115">The following example shows how to initiate a drag operation.</span></span> <span data-ttu-id="2a999-116">拖曳的開始位置的控制項是<xref:System.Windows.Forms.Button>控制項，正在拖曳的資料字串，其代表<xref:System.Windows.Forms.Control.Text%2A>屬性<xref:System.Windows.Forms.Button>控制項，以及允許的效果可能是複製或移動。</span><span class="sxs-lookup"><span data-stu-id="2a999-116">The control where the drag begins is a <xref:System.Windows.Forms.Button> control, the data being dragged is the string representing the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control, and the allowed effects are either copying or moving.</span></span>  
  
    ```vb  
    Private Sub Button1_MouseDown(ByVal sender As Object, ByVal e As System.Windows.Forms.MouseEventArgs) Handles Button1.MouseDown  
       Button1.DoDragDrop(Button1.Text, DragDropEffects.Copy Or DragDropEffects.Move)  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_MouseDown(object sender,   
    System.Windows.Forms.MouseEventArgs e)  
    {  
       button1.DoDragDrop(button1.Text, DragDropEffects.Copy |   
          DragDropEffects.Move);  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="2a999-117">任何資料可用做為參數`DoDragDrop`方法; 在上述範例<xref:System.Windows.Forms.Control.Text%2A>屬性<xref:System.Windows.Forms.Button>控制項使用 （而不是硬式編碼值，或從資料集擷取資料） 因為屬性已與相關從被拖曳的位置 (<xref:System.Windows.Forms.Button>控制項)。</span><span class="sxs-lookup"><span data-stu-id="2a999-117">Any data can be used as a parameter in the `DoDragDrop` method; in the example above, the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control was used (rather than hard-coding a value or retrieving data from a dataset) because the property was related to the location being dragged from (the <xref:System.Windows.Forms.Button> control).</span></span> <span data-ttu-id="2a999-118">當您將拖放作業併入 Windows 應用程式時，請記住這點。</span><span class="sxs-lookup"><span data-stu-id="2a999-118">Keep this in mind as you incorporate drag-and-drop operations into your Windows-based applications.</span></span>  
  
 <span data-ttu-id="2a999-119">拖曳作業時作用中，您可以處理<xref:System.Windows.Forms.Control.QueryContinueDrag>事件，「 要求權限 」 的系統上，以繼續拖曳作業。</span><span class="sxs-lookup"><span data-stu-id="2a999-119">While a drag operation is in effect, you can handle the <xref:System.Windows.Forms.Control.QueryContinueDrag> event, which "asks permission" of the system to continue the drag operation.</span></span> <span data-ttu-id="2a999-120">處理這個方法時，也的適當點，您才能呼叫方法，將會影響在拖曳作業，例如<xref:System.Windows.Forms.TreeNode>中<xref:System.Windows.Forms.TreeView>控制當游標停留它。</span><span class="sxs-lookup"><span data-stu-id="2a999-120">When handling this method, it is also the appropriate point for you to call methods that will have an effect on the drag operation, such as expanding a <xref:System.Windows.Forms.TreeNode> in a <xref:System.Windows.Forms.TreeView> control when the cursor hovers over it.</span></span>  
  
## <a name="dropping-data"></a><span data-ttu-id="2a999-121">卸除資料</span><span class="sxs-lookup"><span data-stu-id="2a999-121">Dropping Data</span></span>  
 <span data-ttu-id="2a999-122">當您開始將資料從某個位置拖曳至 Windows Forms 或控制項時，當然會想要將它卸除到某個位置。</span><span class="sxs-lookup"><span data-stu-id="2a999-122">Once you have begun dragging data from a location on a Windows Form or control, you will naturally want to drop it somewhere.</span></span> <span data-ttu-id="2a999-123">游標在通過已正確設定可卸除資料的表單或控制項的某個區域時會變更。</span><span class="sxs-lookup"><span data-stu-id="2a999-123">The cursor will change when it crosses an area of a form or control that is correctly configured for dropping data.</span></span> <span data-ttu-id="2a999-124">在 Windows Form 或控制項內的任何區域，可以藉由接受已卸除的資料，藉由設定<xref:System.Windows.Forms.Control.AllowDrop%2A>屬性和處理<xref:System.Windows.Forms.Control.DragEnter>和<xref:System.Windows.Forms.Control.DragDrop>事件。</span><span class="sxs-lookup"><span data-stu-id="2a999-124">Any area within a Windows Form or control can be made to accept dropped data by setting the <xref:System.Windows.Forms.Control.AllowDrop%2A> property and handling the <xref:System.Windows.Forms.Control.DragEnter> and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
#### <a name="to-perform-a-drop"></a><span data-ttu-id="2a999-125">執行卸除</span><span class="sxs-lookup"><span data-stu-id="2a999-125">To perform a drop</span></span>  
  
1.  <span data-ttu-id="2a999-126">設定<xref:System.Windows.Forms.Control.AllowDrop%2A>屬性設定為 true。</span><span class="sxs-lookup"><span data-stu-id="2a999-126">Set the <xref:System.Windows.Forms.Control.AllowDrop%2A> property to true.</span></span>  
  
2.  <span data-ttu-id="2a999-127">在`DragEnter`控制項位置下拉式清單，就會發生的事件可讓您確認正在拖曳的資料是屬於可接受的類型 (在此情況下， <xref:System.Windows.Forms.Control.Text%2A>)。</span><span class="sxs-lookup"><span data-stu-id="2a999-127">In the `DragEnter` event for the control where the drop will occur, ensure that the data being dragged is of an acceptable type (in this case, <xref:System.Windows.Forms.Control.Text%2A>).</span></span> <span data-ttu-id="2a999-128">程式碼會設定下拉式清單中的值，就會發生時將發生情況的效果<xref:System.Windows.Forms.DragDropEffects>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="2a999-128">The code then sets the effect that will happen when the drop occurs to a value in the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span> <span data-ttu-id="2a999-129">如需詳細資訊，請參閱<xref:System.Windows.Forms.DragEventArgs.Effect%2A>。</span><span class="sxs-lookup"><span data-stu-id="2a999-129">For more information, see <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span></span>  
  
    ```vb  
    Private Sub TextBox1_DragEnter(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragEnter  
       If (e.Data.GetDataPresent(DataFormats.Text)) Then  
         e.Effect = DragDropEffects.Copy  
       Else  
         e.Effect = DragDropEffects.None  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragEnter(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       if (e.Data.GetDataPresent(DataFormats.Text))   
          e.Effect = DragDropEffects.Copy;  
       else  
          e.Effect = DragDropEffects.None;  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="2a999-130">您可以定義自己<xref:System.Windows.Forms.DataFormats>藉由指定您自己的物件做為<xref:System.Object>參數<xref:System.Windows.Forms.DataObject.SetData%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="2a999-130">You can define your own <xref:System.Windows.Forms.DataFormats> by specifying your own object as the <xref:System.Object> parameter of the <xref:System.Windows.Forms.DataObject.SetData%2A> method.</span></span> <span data-ttu-id="2a999-131">這麼做時，請確定可序列化所指定的物件。</span><span class="sxs-lookup"><span data-stu-id="2a999-131">Be sure, when doing this, that the object specified is serializable.</span></span> <span data-ttu-id="2a999-132">如需詳細資訊，請參閱<xref:System.Runtime.Serialization.ISerializable>。</span><span class="sxs-lookup"><span data-stu-id="2a999-132">For more information, see <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
3.  <span data-ttu-id="2a999-133">在<xref:System.Windows.Forms.Control.DragDrop>位置下拉式清單，就會發生的控制項使用事件<xref:System.Windows.Forms.DataObject.GetData%2A>方法來擷取正在拖曳的資料。</span><span class="sxs-lookup"><span data-stu-id="2a999-133">In the <xref:System.Windows.Forms.Control.DragDrop> event for the control where the drop will occur, use the <xref:System.Windows.Forms.DataObject.GetData%2A> method to retrieve the data being dragged.</span></span> <span data-ttu-id="2a999-134">如需詳細資訊，請參閱<xref:System.Security.Cryptography.Xml.DataObject.Data%2A>。</span><span class="sxs-lookup"><span data-stu-id="2a999-134">For more information, see <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span></span>  
  
     <span data-ttu-id="2a999-135">在下列範例中，<xref:System.Windows.Forms.TextBox>控制項為正在拖曳到 （其中將會卸除） 控制項。</span><span class="sxs-lookup"><span data-stu-id="2a999-135">In the example below, a <xref:System.Windows.Forms.TextBox> control is the control being dragged to (where the drop will occur).</span></span> <span data-ttu-id="2a999-136">程式碼集<xref:System.Windows.Forms.Control.Text%2A>屬性<xref:System.Windows.Forms.TextBox>控制等於正在拖曳的資料。</span><span class="sxs-lookup"><span data-stu-id="2a999-136">The code sets the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.TextBox> control equal to the data being dragged.</span></span>  
  
    ```vb  
    Private Sub TextBox1_DragDrop(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragDrop  
       TextBox1.Text = e.Data.GetData(DataFormats.Text).ToString  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragDrop(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       textBox1.Text = e.Data.GetData(DataFormats.Text).ToString();  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="2a999-137">此外，您可以使用<xref:System.Windows.Forms.DragEventArgs.KeyState%2A>屬性，以便根據索引鍵按下拖放作業期間，某些效果發生 （例如，它位於標準時按下 CTRL 鍵，複製拖曳的資料）。</span><span class="sxs-lookup"><span data-stu-id="2a999-137">Additionally, you can work with the <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> property, so that, depending on keys depressed during the drag-and-drop operation, certain effects occur (for example, it is standard to copy the dragged data when the CTRL key is pressed).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a999-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a999-138">See Also</span></span>  
 [<span data-ttu-id="2a999-139">操作說明：將資料新增至剪貼簿</span><span class="sxs-lookup"><span data-stu-id="2a999-139">How to: Add Data to the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 [<span data-ttu-id="2a999-140">操作說明：從剪貼簿擷取資料</span><span class="sxs-lookup"><span data-stu-id="2a999-140">How to: Retrieve Data from the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 [<span data-ttu-id="2a999-141">拖放作業和剪貼簿支援</span><span class="sxs-lookup"><span data-stu-id="2a999-141">Drag-and-Drop Operations and Clipboard Support</span></span>](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)
