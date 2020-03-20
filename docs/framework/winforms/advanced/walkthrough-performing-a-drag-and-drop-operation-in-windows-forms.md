---
title: 演練：執行拖放操作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: b5e4bf753733cb9bd010672f40e8fbeb0cf036bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182436"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a><span data-ttu-id="2f6d7-102">逐步解說：在 Windows Form 中執行拖放作業</span><span class="sxs-lookup"><span data-stu-id="2f6d7-102">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>
<span data-ttu-id="2f6d7-103">要在基於 Windows 的應用程式中執行拖放操作，必須處理一系列事件，其中最著名的是<xref:System.Windows.Forms.Control.DragEnter>，<xref:System.Windows.Forms.Control.DragLeave>和<xref:System.Windows.Forms.Control.DragDrop>事件。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-103">To perform drag-and-drop operations within Windows-based applications you must handle a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span> <span data-ttu-id="2f6d7-104">使用這些事件的事件引數中所提供的資訊，即可輕鬆地運用拖放作業。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-104">By working with the information available in the event arguments of these events, you can easily facilitate drag-and-drop operations.</span></span>  
  
## <a name="dragging-data"></a><span data-ttu-id="2f6d7-105">拖曳資料</span><span class="sxs-lookup"><span data-stu-id="2f6d7-105">Dragging Data</span></span>  
 <span data-ttu-id="2f6d7-106">所有拖放作業都是從拖曳開始。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-106">All drag-and-drop operations begin with dragging.</span></span> <span data-ttu-id="2f6d7-107">在<xref:System.Windows.Forms.Control.DoDragDrop%2A>方法中實現了在方法中實現在拖動開始時啟用收集資料的功能。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-107">The functionality to enable data to be collected when dragging begins is implemented in the <xref:System.Windows.Forms.Control.DoDragDrop%2A> method.</span></span>  
  
 <span data-ttu-id="2f6d7-108">在下面的示例中，<xref:System.Windows.Forms.Control.MouseDown>該事件用於啟動拖動操作，因為它是最直觀的（大多數拖放操作從按下滑鼠按鍵開始）。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-108">In the following example, the <xref:System.Windows.Forms.Control.MouseDown> event is used to start the drag operation because it is the most intuitive (most drag-and-drop actions begin with the mouse button being depressed).</span></span> <span data-ttu-id="2f6d7-109">不過，請記住，可以使用任何事件來啟始拖放程序。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-109">However, remember that any event could be used to initiate a drag-and-drop procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f6d7-110">特定控制項會有自訂拖曳特定事件。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-110">Certain controls have custom drag-specific events.</span></span> <span data-ttu-id="2f6d7-111"><xref:System.Windows.Forms.ListView>和<xref:System.Windows.Forms.TreeView>控制項，例如，有一個<xref:System.Windows.Forms.TreeView.ItemDrag>事件。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-111">The <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls, for example, have an <xref:System.Windows.Forms.TreeView.ItemDrag> event.</span></span>  
  
#### <a name="to-start-a-drag-operation"></a><span data-ttu-id="2f6d7-112">啟動拖曳作業</span><span class="sxs-lookup"><span data-stu-id="2f6d7-112">To start a drag operation</span></span>  
  
1. <span data-ttu-id="2f6d7-113">對於將開始<xref:System.Windows.Forms.Control.MouseDown>拖動的控制項，使用`DoDragDrop`方法設置要拖動的資料，並且允許的效果拖動將具有。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-113">In the <xref:System.Windows.Forms.Control.MouseDown> event for the control where the drag will begin, use the `DoDragDrop` method to set the data to be dragged and the allowed effect dragging will have.</span></span> <span data-ttu-id="2f6d7-114">如需詳細資訊，請參閱 <xref:System.Windows.Forms.DragEventArgs.Data%2A> 和 <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-114">For more information, see <xref:System.Windows.Forms.DragEventArgs.Data%2A> and <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span></span>  
  
     <span data-ttu-id="2f6d7-115">下列範例示範如何啟始拖曳作業。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-115">The following example shows how to initiate a drag operation.</span></span> <span data-ttu-id="2f6d7-116">拖動開始的控制項是<xref:System.Windows.Forms.Button>控制項，要拖動的資料是表示控制項<xref:System.Windows.Forms.Control.Text%2A>屬性的<xref:System.Windows.Forms.Button>字串，允許的效果是複製或移動。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-116">The control where the drag begins is a <xref:System.Windows.Forms.Button> control, the data being dragged is the string representing the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control, and the allowed effects are either copying or moving.</span></span>  
  
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
    > <span data-ttu-id="2f6d7-117">任何資料都可以用作`DoDragDrop`方法中的參數;在上面的示例中，使用了<xref:System.Windows.Forms.Control.Text%2A><xref:System.Windows.Forms.Button>控制項的屬性（而不是硬編碼值或從資料集檢索資料），因為該屬性與從中拖動的位置（<xref:System.Windows.Forms.Button>控制項）相關。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-117">Any data can be used as a parameter in the `DoDragDrop` method; in the example above, the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control was used (rather than hard-coding a value or retrieving data from a dataset) because the property was related to the location being dragged from (the <xref:System.Windows.Forms.Button> control).</span></span> <span data-ttu-id="2f6d7-118">當您將拖放作業併入 Windows 應用程式時，請記住這點。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-118">Keep this in mind as you incorporate drag-and-drop operations into your Windows-based applications.</span></span>  
  
 <span data-ttu-id="2f6d7-119">當拖動操作有效時，您可以處理<xref:System.Windows.Forms.Control.QueryContinueDrag>事件，該事件"請求"系統的許可權以繼續拖動操作。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-119">While a drag operation is in effect, you can handle the <xref:System.Windows.Forms.Control.QueryContinueDrag> event, which "asks permission" of the system to continue the drag operation.</span></span> <span data-ttu-id="2f6d7-120">處理此方法時，調用對拖動操作有影響的方法也是適當的點，例如當游標懸停在<xref:System.Windows.Forms.TreeNode><xref:System.Windows.Forms.TreeView>控制項上時展開 控制項中的 。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-120">When handling this method, it is also the appropriate point for you to call methods that will have an effect on the drag operation, such as expanding a <xref:System.Windows.Forms.TreeNode> in a <xref:System.Windows.Forms.TreeView> control when the cursor hovers over it.</span></span>  
  
## <a name="dropping-data"></a><span data-ttu-id="2f6d7-121">卸除資料</span><span class="sxs-lookup"><span data-stu-id="2f6d7-121">Dropping Data</span></span>  
 <span data-ttu-id="2f6d7-122">當您開始將資料從某個位置拖曳至 Windows Forms 或控制項時，當然會想要將它卸除到某個位置。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-122">Once you have begun dragging data from a location on a Windows Form or control, you will naturally want to drop it somewhere.</span></span> <span data-ttu-id="2f6d7-123">游標在通過已正確設定可卸除資料的表單或控制項的某個區域時會變更。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-123">The cursor will change when it crosses an area of a form or control that is correctly configured for dropping data.</span></span> <span data-ttu-id="2f6d7-124">可以通過設置<xref:System.Windows.Forms.Control.AllowDrop%2A>屬性和處理<xref:System.Windows.Forms.Control.DragEnter>和<xref:System.Windows.Forms.Control.DragDrop>事件來使 Windows 表單或控制項中的任何區域接受丟棄的資料。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-124">Any area within a Windows Form or control can be made to accept dropped data by setting the <xref:System.Windows.Forms.Control.AllowDrop%2A> property and handling the <xref:System.Windows.Forms.Control.DragEnter> and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
#### <a name="to-perform-a-drop"></a><span data-ttu-id="2f6d7-125">執行卸除</span><span class="sxs-lookup"><span data-stu-id="2f6d7-125">To perform a drop</span></span>  
  
1. <span data-ttu-id="2f6d7-126">將<xref:System.Windows.Forms.Control.AllowDrop%2A>屬性設置為 true。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-126">Set the <xref:System.Windows.Forms.Control.AllowDrop%2A> property to true.</span></span>  
  
2. <span data-ttu-id="2f6d7-127">對於`DragEnter`發生丟棄的控制項，請確保拖動的資料是可接受的類型（在本例中為<xref:System.Windows.Forms.Control.Text%2A>）。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-127">In the `DragEnter` event for the control where the drop will occur, ensure that the data being dragged is of an acceptable type (in this case, <xref:System.Windows.Forms.Control.Text%2A>).</span></span> <span data-ttu-id="2f6d7-128">然後，代碼設置在枚舉中<xref:System.Windows.Forms.DragDropEffects>放置到值時將發生的效果。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-128">The code then sets the effect that will happen when the drop occurs to a value in the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span> <span data-ttu-id="2f6d7-129">如需詳細資訊，請參閱 <xref:System.Windows.Forms.DragEventArgs.Effect%2A>。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-129">For more information, see <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span></span>  
  
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
    > <span data-ttu-id="2f6d7-130">可以通過將自己的物件指定<xref:System.Windows.Forms.DataFormats>為方法的<xref:System.Object>參數來<xref:System.Windows.Forms.DataObject.SetData%2A>定義您自己的物件。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-130">You can define your own <xref:System.Windows.Forms.DataFormats> by specifying your own object as the <xref:System.Object> parameter of the <xref:System.Windows.Forms.DataObject.SetData%2A> method.</span></span> <span data-ttu-id="2f6d7-131">這麼做時，請確定可序列化所指定的物件。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-131">Be sure, when doing this, that the object specified is serializable.</span></span> <span data-ttu-id="2f6d7-132">如需詳細資訊，請參閱 <xref:System.Runtime.Serialization.ISerializable>。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-132">For more information, see <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
3. <span data-ttu-id="2f6d7-133">對於<xref:System.Windows.Forms.Control.DragDrop>發生放置的控制項，使用 方法<xref:System.Windows.Forms.DataObject.GetData%2A>檢索要拖動的資料。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-133">In the <xref:System.Windows.Forms.Control.DragDrop> event for the control where the drop will occur, use the <xref:System.Windows.Forms.DataObject.GetData%2A> method to retrieve the data being dragged.</span></span> <span data-ttu-id="2f6d7-134">如需詳細資訊，請參閱 <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-134">For more information, see <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span></span>  
  
     <span data-ttu-id="2f6d7-135">在下面的示例中，<xref:System.Windows.Forms.TextBox>控制項是拖動到（將發生丟棄的位置）的控制項。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-135">In the example below, a <xref:System.Windows.Forms.TextBox> control is the control being dragged to (where the drop will occur).</span></span> <span data-ttu-id="2f6d7-136">代碼設置控制項<xref:System.Windows.Forms.Control.Text%2A>的屬性<xref:System.Windows.Forms.TextBox>等於要拖動的資料。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-136">The code sets the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.TextBox> control equal to the data being dragged.</span></span>  
  
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
    > <span data-ttu-id="2f6d7-137">此外，您可以使用 該<xref:System.Windows.Forms.DragEventArgs.KeyState%2A>屬性，以便根據拖放操作期間按下的鍵，會發生某些效果（例如，在按下 CTRL 鍵時複製拖動的資料是標準）。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-137">Additionally, you can work with the <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> property, so that, depending on keys depressed during the drag-and-drop operation, certain effects occur (for example, it is standard to copy the dragged data when the CTRL key is pressed).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f6d7-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f6d7-138">See also</span></span>

- [<span data-ttu-id="2f6d7-139">如何：將資料加入至剪貼簿</span><span class="sxs-lookup"><span data-stu-id="2f6d7-139">How to: Add Data to the Clipboard</span></span>](how-to-add-data-to-the-clipboard.md)
- [<span data-ttu-id="2f6d7-140">如何：從剪貼簿擷取資料</span><span class="sxs-lookup"><span data-stu-id="2f6d7-140">How to: Retrieve Data from the Clipboard</span></span>](how-to-retrieve-data-from-the-clipboard.md)
- [<span data-ttu-id="2f6d7-141">拖放作業和剪貼簿支援</span><span class="sxs-lookup"><span data-stu-id="2f6d7-141">Drag-and-Drop Operations and Clipboard Support</span></span>](drag-and-drop-operations-and-clipboard-support.md)
