---
title: 逐步解說：執行拖放作業
description: 瞭解如何藉由處理一連串的事件，在 Windows Forms 中執行拖放作業，最值得注意的是 System.windows.dragdrop.dragenter>、DragLeave 和 System.windows.dragdrop.drop> 事件。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: 83bfda875e2fdec3981bbcb8f8f7be00db342440
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325816"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a><span data-ttu-id="def0c-103">逐步解說：在 Windows Form 中執行拖放作業</span><span class="sxs-lookup"><span data-stu-id="def0c-103">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>
<span data-ttu-id="def0c-104">若要在以 Windows 為基礎的應用程式內執行拖放作業，您必須處理一連串的事件，最值得注意的是 <xref:System.Windows.Forms.Control.DragEnter> 、 <xref:System.Windows.Forms.Control.DragLeave> 和 <xref:System.Windows.Forms.Control.DragDrop> 事件。</span><span class="sxs-lookup"><span data-stu-id="def0c-104">To perform drag-and-drop operations within Windows-based applications you must handle a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span> <span data-ttu-id="def0c-105">使用這些事件的事件引數中所提供的資訊，即可輕鬆地運用拖放作業。</span><span class="sxs-lookup"><span data-stu-id="def0c-105">By working with the information available in the event arguments of these events, you can easily facilitate drag-and-drop operations.</span></span>  
  
## <a name="dragging-data"></a><span data-ttu-id="def0c-106">拖曳資料</span><span class="sxs-lookup"><span data-stu-id="def0c-106">Dragging Data</span></span>  
 <span data-ttu-id="def0c-107">所有拖放作業都是從拖曳開始。</span><span class="sxs-lookup"><span data-stu-id="def0c-107">All drag-and-drop operations begin with dragging.</span></span> <span data-ttu-id="def0c-108">在方法中實作為拖曳開始時，啟用收集資料的功能 <xref:System.Windows.Forms.Control.DoDragDrop%2A> 。</span><span class="sxs-lookup"><span data-stu-id="def0c-108">The functionality to enable data to be collected when dragging begins is implemented in the <xref:System.Windows.Forms.Control.DoDragDrop%2A> method.</span></span>  
  
 <span data-ttu-id="def0c-109">在下列範例中，會 <xref:System.Windows.Forms.Control.MouseDown> 使用事件來啟動拖曳作業，因為它是最直覺化的（大部分的拖放動作都是以按下滑鼠按鍵的方式開始）。</span><span class="sxs-lookup"><span data-stu-id="def0c-109">In the following example, the <xref:System.Windows.Forms.Control.MouseDown> event is used to start the drag operation because it is the most intuitive (most drag-and-drop actions begin with the mouse button being depressed).</span></span> <span data-ttu-id="def0c-110">不過，請記住，可以使用任何事件來啟始拖放程序。</span><span class="sxs-lookup"><span data-stu-id="def0c-110">However, remember that any event could be used to initiate a drag-and-drop procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="def0c-111">特定控制項會有自訂拖曳特定事件。</span><span class="sxs-lookup"><span data-stu-id="def0c-111">Certain controls have custom drag-specific events.</span></span> <span data-ttu-id="def0c-112"><xref:System.Windows.Forms.ListView> <xref:System.Windows.Forms.TreeView> 例如，和控制項有 <xref:System.Windows.Forms.TreeView.ItemDrag> 事件。</span><span class="sxs-lookup"><span data-stu-id="def0c-112">The <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls, for example, have an <xref:System.Windows.Forms.TreeView.ItemDrag> event.</span></span>  
  
#### <a name="to-start-a-drag-operation"></a><span data-ttu-id="def0c-113">啟動拖曳作業</span><span class="sxs-lookup"><span data-stu-id="def0c-113">To start a drag operation</span></span>  
  
1. <span data-ttu-id="def0c-114">在將 <xref:System.Windows.Forms.Control.MouseDown> 開始拖曳之控制項的事件中，使用 `DoDragDrop` 方法來設定要拖曳的資料，而允許的效果將會有。</span><span class="sxs-lookup"><span data-stu-id="def0c-114">In the <xref:System.Windows.Forms.Control.MouseDown> event for the control where the drag will begin, use the `DoDragDrop` method to set the data to be dragged and the allowed effect dragging will have.</span></span> <span data-ttu-id="def0c-115">如需詳細資訊，請參閱 <xref:System.Windows.Forms.DragEventArgs.Data%2A> 和 <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>。</span><span class="sxs-lookup"><span data-stu-id="def0c-115">For more information, see <xref:System.Windows.Forms.DragEventArgs.Data%2A> and <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span></span>  
  
     <span data-ttu-id="def0c-116">下列範例示範如何啟始拖曳作業。</span><span class="sxs-lookup"><span data-stu-id="def0c-116">The following example shows how to initiate a drag operation.</span></span> <span data-ttu-id="def0c-117">拖曳開始位置為控制項的控制項，所拖曳 <xref:System.Windows.Forms.Button> 的資料是代表 <xref:System.Windows.Forms.Control.Text%2A> 控制項屬性的字串 <xref:System.Windows.Forms.Button> ，而允許的效果可能是複製或移動。</span><span class="sxs-lookup"><span data-stu-id="def0c-117">The control where the drag begins is a <xref:System.Windows.Forms.Button> control, the data being dragged is the string representing the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control, and the allowed effects are either copying or moving.</span></span>  
  
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
    > <span data-ttu-id="def0c-118">任何資料都可以做為方法中的參數 `DoDragDrop` 。在上述範例中，會 <xref:System.Windows.Forms.Control.Text%2A> 使用控制項的屬性 <xref:System.Windows.Forms.Button> （而不是將值硬式編碼或從資料集抓取資料），因為屬性與從拖曳的位置（ <xref:System.Windows.Forms.Button> 控制項）有關。</span><span class="sxs-lookup"><span data-stu-id="def0c-118">Any data can be used as a parameter in the `DoDragDrop` method; in the example above, the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control was used (rather than hard-coding a value or retrieving data from a dataset) because the property was related to the location being dragged from (the <xref:System.Windows.Forms.Button> control).</span></span> <span data-ttu-id="def0c-119">當您將拖放作業併入 Windows 應用程式時，請記住這點。</span><span class="sxs-lookup"><span data-stu-id="def0c-119">Keep this in mind as you incorporate drag-and-drop operations into your Windows-based applications.</span></span>  
  
 <span data-ttu-id="def0c-120">當拖曳作業生效時，您可以處理 <xref:System.Windows.Forms.Control.QueryContinueDrag> 事件，這會「詢問」系統的許可權，以繼續拖曳操作。</span><span class="sxs-lookup"><span data-stu-id="def0c-120">While a drag operation is in effect, you can handle the <xref:System.Windows.Forms.Control.QueryContinueDrag> event, which "asks permission" of the system to continue the drag operation.</span></span> <span data-ttu-id="def0c-121">處理這個方法時，您也可以呼叫將會影響拖曳作業的方法，例如， <xref:System.Windows.Forms.TreeNode> 當游標停留在控制項上時，展開控制項中的 <xref:System.Windows.Forms.TreeView> 。</span><span class="sxs-lookup"><span data-stu-id="def0c-121">When handling this method, it is also the appropriate point for you to call methods that will have an effect on the drag operation, such as expanding a <xref:System.Windows.Forms.TreeNode> in a <xref:System.Windows.Forms.TreeView> control when the cursor hovers over it.</span></span>  
  
## <a name="dropping-data"></a><span data-ttu-id="def0c-122">卸除資料</span><span class="sxs-lookup"><span data-stu-id="def0c-122">Dropping Data</span></span>  
 <span data-ttu-id="def0c-123">當您開始將資料從某個位置拖曳至 Windows Forms 或控制項時，當然會想要將它卸除到某個位置。</span><span class="sxs-lookup"><span data-stu-id="def0c-123">Once you have begun dragging data from a location on a Windows Form or control, you will naturally want to drop it somewhere.</span></span> <span data-ttu-id="def0c-124">游標在通過已正確設定可卸除資料的表單或控制項的某個區域時會變更。</span><span class="sxs-lookup"><span data-stu-id="def0c-124">The cursor will change when it crosses an area of a form or control that is correctly configured for dropping data.</span></span> <span data-ttu-id="def0c-125">您可以藉由設定 <xref:System.Windows.Forms.Control.AllowDrop%2A> 屬性和處理 <xref:System.Windows.Forms.Control.DragEnter> 和事件，讓 Windows Form 或控制項內的任何區域接受已捨棄的資料 <xref:System.Windows.Forms.Control.DragDrop> 。</span><span class="sxs-lookup"><span data-stu-id="def0c-125">Any area within a Windows Form or control can be made to accept dropped data by setting the <xref:System.Windows.Forms.Control.AllowDrop%2A> property and handling the <xref:System.Windows.Forms.Control.DragEnter> and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
#### <a name="to-perform-a-drop"></a><span data-ttu-id="def0c-126">執行卸除</span><span class="sxs-lookup"><span data-stu-id="def0c-126">To perform a drop</span></span>  
  
1. <span data-ttu-id="def0c-127">將 <xref:System.Windows.Forms.Control.AllowDrop%2A> 屬性設定為 true。</span><span class="sxs-lookup"><span data-stu-id="def0c-127">Set the <xref:System.Windows.Forms.Control.AllowDrop%2A> property to true.</span></span>  
  
2. <span data-ttu-id="def0c-128">在 `DragEnter` 發生卸載之控制項的事件中，請確定所拖曳的資料是可接受的類型（在此案例中為 <xref:System.Windows.Forms.Control.Text%2A> ）。</span><span class="sxs-lookup"><span data-stu-id="def0c-128">In the `DragEnter` event for the control where the drop will occur, ensure that the data being dragged is of an acceptable type (in this case, <xref:System.Windows.Forms.Control.Text%2A>).</span></span> <span data-ttu-id="def0c-129">然後，此程式碼會設定當 drop 發生于列舉值中時，將會發生的效果 <xref:System.Windows.Forms.DragDropEffects> 。</span><span class="sxs-lookup"><span data-stu-id="def0c-129">The code then sets the effect that will happen when the drop occurs to a value in the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span> <span data-ttu-id="def0c-130">如需詳細資訊，請參閱 <xref:System.Windows.Forms.DragEventArgs.Effect%2A> 。</span><span class="sxs-lookup"><span data-stu-id="def0c-130">For more information, see <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span></span>  
  
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
    > <span data-ttu-id="def0c-131">您可以指定自己的 <xref:System.Windows.Forms.DataFormats> 物件做為方法的參數，藉以定義自己的物件 <xref:System.Object> <xref:System.Windows.Forms.DataObject.SetData%2A> 。</span><span class="sxs-lookup"><span data-stu-id="def0c-131">You can define your own <xref:System.Windows.Forms.DataFormats> by specifying your own object as the <xref:System.Object> parameter of the <xref:System.Windows.Forms.DataObject.SetData%2A> method.</span></span> <span data-ttu-id="def0c-132">這麼做時，請確定可序列化所指定的物件。</span><span class="sxs-lookup"><span data-stu-id="def0c-132">Be sure, when doing this, that the object specified is serializable.</span></span> <span data-ttu-id="def0c-133">如需詳細資訊，請參閱 <xref:System.Runtime.Serialization.ISerializable> 。</span><span class="sxs-lookup"><span data-stu-id="def0c-133">For more information, see <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
3. <span data-ttu-id="def0c-134">在發生卸載之 <xref:System.Windows.Forms.Control.DragDrop> 控制項的事件中，使用方法來抓取要拖曳 <xref:System.Windows.Forms.DataObject.GetData%2A> 的資料。</span><span class="sxs-lookup"><span data-stu-id="def0c-134">In the <xref:System.Windows.Forms.Control.DragDrop> event for the control where the drop will occur, use the <xref:System.Windows.Forms.DataObject.GetData%2A> method to retrieve the data being dragged.</span></span> <span data-ttu-id="def0c-135">如需詳細資訊，請參閱 <xref:System.Security.Cryptography.Xml.DataObject.Data%2A> 。</span><span class="sxs-lookup"><span data-stu-id="def0c-135">For more information, see <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span></span>  
  
     <span data-ttu-id="def0c-136">在下列範例中， <xref:System.Windows.Forms.TextBox> 控制項是要拖曳至的控制項（將會在其中進行卸載）。</span><span class="sxs-lookup"><span data-stu-id="def0c-136">In the example below, a <xref:System.Windows.Forms.TextBox> control is the control being dragged to (where the drop will occur).</span></span> <span data-ttu-id="def0c-137">程式碼會將 <xref:System.Windows.Forms.Control.Text%2A> 控制項的屬性設定 <xref:System.Windows.Forms.TextBox> 為等於所拖曳的資料。</span><span class="sxs-lookup"><span data-stu-id="def0c-137">The code sets the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.TextBox> control equal to the data being dragged.</span></span>  
  
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
    > <span data-ttu-id="def0c-138">此外，您可以使用 <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> 屬性，如此一來，根據拖放作業期間所按下的按鍵，就會發生某些效果（例如，在按下 CTRL 鍵時，複製拖曳的資料的標準）。</span><span class="sxs-lookup"><span data-stu-id="def0c-138">Additionally, you can work with the <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> property, so that, depending on keys depressed during the drag-and-drop operation, certain effects occur (for example, it is standard to copy the dragged data when the CTRL key is pressed).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="def0c-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="def0c-139">See also</span></span>

- [<span data-ttu-id="def0c-140">如何：將資料加入至剪貼簿</span><span class="sxs-lookup"><span data-stu-id="def0c-140">How to: Add Data to the Clipboard</span></span>](how-to-add-data-to-the-clipboard.md)
- [<span data-ttu-id="def0c-141">如何：從剪貼簿擷取資料</span><span class="sxs-lookup"><span data-stu-id="def0c-141">How to: Retrieve Data from the Clipboard</span></span>](how-to-retrieve-data-from-the-clipboard.md)
- [<span data-ttu-id="def0c-142">拖放作業和剪貼簿支援</span><span class="sxs-lookup"><span data-stu-id="def0c-142">Drag-and-Drop Operations and Clipboard Support</span></span>](drag-and-drop-operations-and-clipboard-support.md)
