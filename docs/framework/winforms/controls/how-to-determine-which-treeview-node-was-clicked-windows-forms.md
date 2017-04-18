---
title: "如何：判斷按下哪個 TreeView 節點 (Windows Form) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TreeNode"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "範例 [Windows Form], TreeView 控制項"
  - "TreeView 控制項中的樹狀節點, 決定按下的節點"
  - "TreeView 控制項 [Windows Form], 決定按下的節點"
ms.assetid: 06a4a191-d918-42af-9f49-956c93eff261
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：判斷按下哪個 TreeView 節點 (Windows Form)
使用 Windows Form <xref:System.Windows.Forms.TreeView> 控制項時，會有個常見的工作就是需要判斷按下哪個節點，並適當地回應。  
  
### 若要判斷按下哪個 TreeView 節點  
  
1.  使用 <xref:System.EventArgs> 物件傳回按下節點物件的參考。  
  
2.  利用檢查 <xref:System.Windows.Forms.TreeViewEventArgs> 類別判斷按了哪一個節點，這個類別包含事件的相關資料。  
  
    ```vb  
    Private Sub TreeView1_AfterSelect(ByVal sender As System.Object, _  
    ByVal e As System.Windows.Forms.TreeViewEventArgs) Handles TreeView1.AfterSelect  
       ' Determine by checking the Node property of the TreeViewEventArgs.  
       MessageBox.Show(e.Node.Text)  
    End Sub  
  
    ```  
  
    ```csharp  
    protected void treeView1_AfterSelect (object sender,   
    System.Windows.Forms.TreeViewEventArgs e)  
    {  
       // Determine by checking the Text property.  
       MessageBox.Show(e.Node.Text);  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void treeView1_AfterSelect(System::Object ^  sender,  
          System::Windows::Forms::TreeViewEventArgs ^  e)  
       {  
          // Determine by checking the Text property.  
          MessageBox::Show(e->Node->Text);  
       }  
    ```  
  
    > [!NOTE]
    >  另一個替代的方法，是使用 <xref:System.Windows.Forms.Control.MouseDown> 或 <xref:System.Windows.Forms.Control.MouseUp> 事件的 <xref:System.Windows.Forms.MouseEventArgs>，取得使用者按過的 <xref:System.Drawing.Point> 之 <xref:System.Drawing.Point.X%2A> 和 <xref:System.Drawing.Point.Y%2A> 座標值。  然後，使用 <xref:System.Windows.Forms.TreeView> 控制項的 <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> 方法，判斷已按過哪一個節點。  
  
## 請參閱  
 [TreeView 控制項](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)