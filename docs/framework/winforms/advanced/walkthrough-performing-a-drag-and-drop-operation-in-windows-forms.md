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
ms.openlocfilehash: 664c78ce3fff9651acf6ad720360cdb077f23108
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715239"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>逐步解說：在 Windows Form 中執行拖放作業
若要執行以 Windows 為基礎的應用程式中的拖放作業，您必須處理一系列的事件，最值得注意的是<xref:System.Windows.Forms.Control.DragEnter>， <xref:System.Windows.Forms.Control.DragLeave>，和<xref:System.Windows.Forms.Control.DragDrop>事件。 使用這些事件的事件引數中所提供的資訊，即可輕鬆地運用拖放作業。  
  
## <a name="dragging-data"></a>拖曳資料  
 所有拖放作業都是從拖曳開始。 若要啟用在拖曳開始時收集資料的功能實作中<xref:System.Windows.Forms.Control.DoDragDrop%2A>方法。  
  
 在下列範例中，<xref:System.Windows.Forms.Control.MouseDown>事件用來啟動拖曳作業，因為它是最直覺式 （按下滑鼠按鈕以開頭大部分的拖放動作）。 不過，請記住，可以使用任何事件來啟始拖放程序。  
  
> [!NOTE]
>  特定控制項會有自訂拖曳特定事件。 <xref:System.Windows.Forms.ListView>並<xref:System.Windows.Forms.TreeView>控制項，例如，有<xref:System.Windows.Forms.TreeView.ItemDrag>事件。  
  
#### <a name="to-start-a-drag-operation"></a>啟動拖曳作業  
  
1.  在 <xref:System.Windows.Forms.Control.MouseDown>拖曳開始處，使用的控制項事件`DoDragDrop`方法來設定要拖曳的資料，以及允許拖曳的效果都可以。 如需詳細資訊，請參閱 <xref:System.Windows.Forms.DragEventArgs.Data%2A> 與 <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>。  
  
     下列範例示範如何啟始拖曳作業。 開始拖曳的控制項<xref:System.Windows.Forms.Button>控制項，正在拖曳的資料是字串，表示<xref:System.Windows.Forms.Control.Text%2A>屬性<xref:System.Windows.Forms.Button>控制項，以及允許的效果是複製或移動。  
  
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
    >  任何資料可用來當做中的參數`DoDragDrop`方法; 在上述範例<xref:System.Windows.Forms.Control.Text%2A>屬性<xref:System.Windows.Forms.Button>控制項已使用 （而不是硬式編碼值，或從資料集擷取資料） 因為屬性與相關從被拖曳的位置 (<xref:System.Windows.Forms.Button>控制項)。 當您將拖放作業併入 Windows 應用程式時，請記住這點。  
  
 在拖曳作業生效時，您可以處理<xref:System.Windows.Forms.Control.QueryContinueDrag>事件，以 「 要求權限 」 的系統繼續拖曳作業。 處理這個方法時，也為您呼叫將會有影響拖曳作業，例如擴充方法的適當時間點<xref:System.Windows.Forms.TreeNode>在<xref:System.Windows.Forms.TreeView>控制當游標停留在其上方。  
  
## <a name="dropping-data"></a>卸除資料  
 當您開始將資料從某個位置拖曳至 Windows Forms 或控制項時，當然會想要將它卸除到某個位置。 游標在通過已正確設定可卸除資料的表單或控制項的某個區域時會變更。 Windows 表單或控制項內的任何區域也能藉由設定接受置放的資料<xref:System.Windows.Forms.Control.AllowDrop%2A>屬性和處理<xref:System.Windows.Forms.Control.DragEnter>和<xref:System.Windows.Forms.Control.DragDrop>事件。  
  
#### <a name="to-perform-a-drop"></a>執行卸除  
  
1.  設定<xref:System.Windows.Forms.Control.AllowDrop%2A>屬性設為 true。  
  
2.  在 `DragEnter`事件，其中將進行卸除，控制項可讓您確保所拖曳的資料屬於可接受的類型 (在此情況下， <xref:System.Windows.Forms.Control.Text%2A>)。 程式碼會設定下拉式清單中的值時，會發生的效果<xref:System.Windows.Forms.DragDropEffects>列舉型別。 如需詳細資訊，請參閱<xref:System.Windows.Forms.DragEventArgs.Effect%2A>。  
  
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
    >  您也可以定義自己<xref:System.Windows.Forms.DataFormats>藉由指定您自己的物件做為<xref:System.Object>參數<xref:System.Windows.Forms.DataObject.SetData%2A>方法。 這麼做時，請確定可序列化所指定的物件。 如需詳細資訊，請參閱<xref:System.Runtime.Serialization.ISerializable>。  
  
3.  在 <xref:System.Windows.Forms.Control.DragDrop>事件，其中將進行卸除，控制項使用<xref:System.Windows.Forms.DataObject.GetData%2A>方法來擷取正在拖曳的資料。 如需詳細資訊，請參閱<xref:System.Security.Cryptography.Xml.DataObject.Data%2A>。  
  
     在下列範例中，<xref:System.Windows.Forms.TextBox>控制項是控制項拖曳至 （其中將進行卸除）。 程式碼集<xref:System.Windows.Forms.Control.Text%2A>屬性<xref:System.Windows.Forms.TextBox>控制等於所拖曳的資料。  
  
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
    >  此外，您可以使用<xref:System.Windows.Forms.DragEventArgs.KeyState%2A>屬性，以便根據索引鍵按下拖放作業期間，會發生特定效果 （例如，它是標準，以在按下 CTRL 鍵時，複製所拖曳的資料）。  
  
## <a name="see-also"></a>另請參閱
- [如何：將資料加入至剪貼簿](how-to-add-data-to-the-clipboard.md)
- [如何：從剪貼簿擷取資料](how-to-retrieve-data-from-the-clipboard.md)
- [拖放作業和剪貼簿支援](drag-and-drop-operations-and-clipboard-support.md)
