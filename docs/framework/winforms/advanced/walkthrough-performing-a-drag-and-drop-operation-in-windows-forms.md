---
title: "逐步解說：在 Windows Form 中執行拖放作業 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "拖放, Windows Form"
  - "Windows Form, 拖放作業"
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 逐步解說：在 Windows Form 中執行拖放作業
若要在 Windows 架構應用程式中執行拖放作業，您必須處理一系列的事件，尤其是 <xref:System.Windows.Forms.Control.DragEnter>、<xref:System.Windows.Forms.Control.DragLeave> 和 <xref:System.Windows.Forms.Control.DragDrop> 事件。  藉由使用這些事件的事件引數中所提供的資訊，您可以輕易地運用拖放作業。  
  
## 拖曳資料  
 所有拖放作業都是以拖曳開始的。  在拖曳開始時，啟用資料收集的功能是在 <xref:System.Windows.Forms.Control.DoDragDrop%2A> 方法中實作的。  
  
 以下範例利用 <xref:System.Windows.Forms.Control.MouseDown> 事件來啟動拖曳作業，因為這是最直覺的 \(大多數拖放動作都以按下滑鼠按鍵來啟動\)。  然而，請記住：任何事件都可用來啟始拖放程序。  
  
> [!NOTE]
>  某些控制項具有自訂的特定拖曳事件。  例如，<xref:System.Windows.Forms.ListView> 和 <xref:System.Windows.Forms.TreeView> 控制項具有 <xref:System.Windows.Forms.TreeView.ItemDrag> 事件。  
  
#### 若要啟動拖曳作業  
  
1.  在<xref:System.Windows.Forms.Control.MouseDown>中開始拖曳，控制項使用事件`DoDragDrop`方法，以設定要拖曳的資料和允許的效果拖曳。  如需詳細資訊，請參閱 <xref:System.Windows.Forms.DragEventArgs.Data%2A> 和 <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>。  
  
     以下範例顯示啟始拖曳作業的方法。  開始進行拖曳時所在的控制項是 <xref:System.Windows.Forms.Button> 控制項，被拖曳的資料是代表 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Text%2A> 屬性的字串，而允許產生的效果則是複製或移動。  
  
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
    >  任何資料都可用來當做 `DoDragDrop` 方法中的參數；上例中使用 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Text%2A> 屬性 \(而非將值寫成程式碼或自資料集擷取資料\)，因為其屬性與拖曳開始所在的位置相關 \(<xref:System.Windows.Forms.Button> 控制項\)。  當您在 Windows 架構應用程式中加入拖曳作業時，請留意這一點。  
  
 當拖曳作業執行時，您可處理 <xref:System.Windows.Forms.Control.QueryContinueDrag> 事件，該事件會向系統「要求使用權限」來繼續執行拖曳作業。  處理這個方法時，也正是呼叫會影響拖曳作業的方法的適當時機，例如在游標停留於 <xref:System.Windows.Forms.TreeView> 控制項中的 <xref:System.Windows.Forms.TreeNode> 上方時，將它展開。  
  
## 置放資料  
 一旦開始從 Windows Form 或控制項的某一位置拖曳資料後，您自然就會想把它置放在某處。  游標經過表單或控制項已正確設定成可置放資料的某區域時，會改變形狀。  Windows Form 或控制項中的任何區域，都可以接受置放的資料，只要設定好 <xref:System.Windows.Forms.Control.AllowDrop%2A> 屬性並處理好 <xref:System.Windows.Forms.Control.DragEnter> 和 <xref:System.Windows.Forms.Control.DragDrop> 事件即可。  
  
#### 若要執行置放  
  
1.  將 <xref:System.Windows.Forms.Control.AllowDrop%2A> 屬性設定為 true。  
  
2.  在會發生置放作業的控制項的 `DragEnter` 事件中，請確保所拖曳的資料是屬於可接受的型別 \(在本案例中，是 <xref:System.Windows.Forms.Control.Text%2A>\)。  接著程式碼會將置放發生時出現的效果設定為 <xref:System.Windows.Forms.DragDropEffects> 列舉型別中的值。  如需詳細資訊，請參閱 <xref:System.Windows.Forms.DragEventArgs.Effect%2A>。  
  
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
    >  您可以將自己的物件指定為 <xref:System.Windows.Forms.DataObject.SetData%2A> 方法的 <xref:System.Object> 參數，藉此定義自己的 <xref:System.Windows.Forms.DataFormats>。  同時請確定所指定的物件是可序列化的。  如需詳細資訊，請參閱 [ISerializable 介面](frlrfSystemRuntimeSerializationISerializableClassTopic)。  
  
3.  在置放將發生的控制項的 <xref:System.Windows.Forms.Control.DragDrop> 事件中，使用 <xref:System.Windows.Forms.DataObject.GetData%2A> 方法以擷取被拖曳的資料。  如需詳細資訊，請參閱 [DtaObject.Data Property](frlrfSystemSecurityCryptographyXmlDataObjectClassDataTopic)。  
  
     在以下範例中，<xref:System.Windows.Forms.TextBox> 控制項是物件拖曳的目的地 \(將發生置放的地方\)。  程式碼會把 <xref:System.Windows.Forms.TextBox> 控制項的 <xref:System.Windows.Forms.Control.Text%2A> 屬性設成等於所拖曳的資料。  
  
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
    >  另外，您還可以使用 <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> 屬性，以根據拖放作業時所按的按鍵來產生特定效果 \(例如，在按下 CTRL 鍵時複製所拖曳的資料，這是常用的標準程序\)。  
  
## 請參閱  
 [如何：將資料加入至剪貼簿](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)   
 [如何：從剪貼簿擷取資料](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)   
 [拖放作業和剪貼簿支援](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)