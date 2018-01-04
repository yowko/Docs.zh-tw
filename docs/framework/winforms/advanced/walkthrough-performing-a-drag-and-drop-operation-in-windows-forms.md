---
title: "逐步解說：在 Windows Form 中執行拖放作業"
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
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 173af57f1ec5d9ed14afc0ef5d6ddd391e15d534
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>逐步解說：在 Windows Form 中執行拖放作業
若要執行 windows 應用程式中的拖放作業，您必須處理的一系列事件，最值得注意的是<xref:System.Windows.Forms.Control.DragEnter>， <xref:System.Windows.Forms.Control.DragLeave>，和<xref:System.Windows.Forms.Control.DragDrop>事件。 使用這些事件的事件引數中所提供的資訊，即可輕鬆地運用拖放作業。  
  
## <a name="dragging-data"></a>拖曳資料  
 所有拖放作業都是從拖曳開始。 中實作的功能，可讓資料收集開始拖曳時<xref:System.Windows.Forms.Control.DoDragDrop%2A>方法。  
  
 在下列範例中，<xref:System.Windows.Forms.Control.MouseDown>事件可用來開始拖曳作業，因為它是最直覺 （大部分的拖放動作開頭所按下滑鼠按鈕）。 不過，請記住，可以使用任何事件來啟始拖放程序。  
  
> [!NOTE]
>  特定控制項會有自訂拖曳特定事件。 <xref:System.Windows.Forms.ListView>和<xref:System.Windows.Forms.TreeView>控制項，例如，具有<xref:System.Windows.Forms.TreeView.ItemDrag>事件。  
  
#### <a name="to-start-a-drag-operation"></a>啟動拖曳作業  
  
1.  在<xref:System.Windows.Forms.Control.MouseDown>控制項位置將會開始拖曳，請使用事件`DoDragDrop`方法，以設定要拖曳的資料和允許的效果拖曳所擁有。 如需詳細資訊，請參閱 <xref:System.Windows.Forms.DragEventArgs.Data%2A> 與 <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>。  
  
     下列範例示範如何啟始拖曳作業。 拖曳的開始位置的控制項是<xref:System.Windows.Forms.Button>控制項，正在拖曳的資料字串，其代表<xref:System.Windows.Forms.Control.Text%2A>屬性<xref:System.Windows.Forms.Button>控制項，以及允許的效果可能是複製或移動。  
  
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
    >  任何資料可用做為參數`DoDragDrop`方法; 在上述範例<xref:System.Windows.Forms.Control.Text%2A>屬性<xref:System.Windows.Forms.Button>控制項使用 （而不是硬式編碼值，或從資料集擷取資料） 因為屬性已與相關從被拖曳的位置 (<xref:System.Windows.Forms.Button>控制項)。 當您將拖放作業併入 Windows 應用程式時，請記住這點。  
  
 拖曳作業時作用中，您可以處理<xref:System.Windows.Forms.Control.QueryContinueDrag>事件，「 要求權限 」 的系統上，以繼續拖曳作業。 處理這個方法時，也的適當點，您才能呼叫方法，將會影響在拖曳作業，例如<xref:System.Windows.Forms.TreeNode>中<xref:System.Windows.Forms.TreeView>控制當游標停留它。  
  
## <a name="dropping-data"></a>卸除資料  
 當您開始將資料從某個位置拖曳至 Windows Forms 或控制項時，當然會想要將它卸除到某個位置。 游標在通過已正確設定可卸除資料的表單或控制項的某個區域時會變更。 在 Windows Form 或控制項內的任何區域，可以藉由接受已卸除的資料，藉由設定<xref:System.Windows.Forms.Control.AllowDrop%2A>屬性和處理<xref:System.Windows.Forms.Control.DragEnter>和<xref:System.Windows.Forms.Control.DragDrop>事件。  
  
#### <a name="to-perform-a-drop"></a>執行卸除  
  
1.  設定<xref:System.Windows.Forms.Control.AllowDrop%2A>屬性設定為 true。  
  
2.  在`DragEnter`控制項位置下拉式清單，就會發生的事件可讓您確認正在拖曳的資料是屬於可接受的類型 (在此情況下， <xref:System.Windows.Forms.Control.Text%2A>)。 程式碼會設定下拉式清單中的值，就會發生時將發生情況的效果<xref:System.Windows.Forms.DragDropEffects>列舉型別。 如需詳細資訊，請參閱<xref:System.Windows.Forms.DragEventArgs.Effect%2A>。  
  
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
    >  您可以定義自己<xref:System.Windows.Forms.DataFormats>藉由指定您自己的物件做為<xref:System.Object>參數<xref:System.Windows.Forms.DataObject.SetData%2A>方法。 這麼做時，請確定可序列化所指定的物件。 如需詳細資訊，請參閱<xref:System.Runtime.Serialization.ISerializable>。  
  
3.  在<xref:System.Windows.Forms.Control.DragDrop>位置下拉式清單，就會發生的控制項使用事件<xref:System.Windows.Forms.DataObject.GetData%2A>方法來擷取正在拖曳的資料。 如需詳細資訊，請參閱<xref:System.Security.Cryptography.Xml.DataObject.Data%2A>。  
  
     在下列範例中，<xref:System.Windows.Forms.TextBox>控制項為正在拖曳到 （其中將會卸除） 控制項。 程式碼集<xref:System.Windows.Forms.Control.Text%2A>屬性<xref:System.Windows.Forms.TextBox>控制等於正在拖曳的資料。  
  
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
    >  此外，您可以使用<xref:System.Windows.Forms.DragEventArgs.KeyState%2A>屬性，以便根據索引鍵按下拖放作業期間，某些效果發生 （例如，它位於標準時按下 CTRL 鍵，複製拖曳的資料）。  
  
## <a name="see-also"></a>請參閱  
 [操作說明：將資料新增至剪貼簿](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 [操作說明：從剪貼簿擷取資料](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 [拖放作業和剪貼簿支援](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)
