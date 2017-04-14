---
title: "如何：將自訂資訊加入 TreeView 或 ListView 控制項 (Windows Form) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ListItem"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "範例 [Windows Form], ListView 控制項"
  - "範例 [Windows Form], TreeView 控制項"
  - "ListView 控制項 [Windows Form], 加入自訂資訊"
  - "Tag 屬性"
  - "TreeView 控制項 [Windows Form], 加入自訂資訊"
ms.assetid: 68be11de-1d5b-430e-901f-cfbe48d14b19
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：將自訂資訊加入 TreeView 或 ListView 控制項 (Windows Form)
您可以在 Windows Form <xref:System.Windows.Forms.TreeView> 控制項或 <xref:System.Windows.Forms.ListView> 控制項的衍生項目中，建立衍生節點。  衍生讓您可以加入任何所需的欄位，以及處理它們的自訂方法和建構函式。  此功能的用法之一是將 Customer 物件附加至每個樹狀節點或清單項目。  這裡是 <xref:System.Windows.Forms.TreeView> 控制項的範例，但是 <xref:System.Windows.Forms.ListView> 控制項也可以使用相同的方式。  
  
### 若要衍生樹狀節點  
  
-   建立衍生自 <xref:System.Windows.Forms.TreeNode> 類別的新節點類別，此類別具有可以記錄檔案路徑的自訂欄位。  
  
    ```vb  
    Class myTreeNode  
       Inherits TreeNode  
  
       Public FilePath As String  
  
       Sub New(ByVal fp As String)  
          MyBase.New()  
          FilePath = fp  
          Me.Text = fp.Substring(fp.LastIndexOf("\"))  
       End Sub  
    End Class  
  
    ```  
  
    ```csharp  
    class myTreeNode : TreeNode  
    {  
       public string FilePath;  
  
       public myTreeNode(string fp)  
       {  
          FilePath = fp;  
          this.Text = fp.Substring(fp.LastIndexOf("\\"));  
       }  
    }  
  
    ```  
  
    ```cpp  
    ref class myTreeNode : public TreeNode  
    {  
    public:  
       System::String ^ FilePath;  
  
       myTreeNode(System::String ^ fp)  
       {  
          FilePath = fp;  
          this->Text = fp->Substring(fp->LastIndexOf("\\"));  
       }  
    };  
    ```  
  
### 若要使用衍生的樹狀節點  
  
1.  您可以使用新衍生的樹狀節點做為函式呼叫 \(Function Call\) 的參數。  
  
     在以下範例中，為文字檔位置所設定的路徑為 \[我的文件\] 資料夾。  這是可以做到的，因為您可預測到大部分執行 Windows 作業系統的電腦都會包含這個目錄。  這也可讓使用者以最基本的系統存取層級，便可安全執行應用程式。  
  
    ```vb  
    ' You should replace the bold text file   
    ' in the sample below with a text file of your own choosing.  
    TreeView1.Nodes.Add(New myTreeNode (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\ TextFile.txt ") )  
  
    ```  
  
    ```csharp  
    // You should replace the bold text file   
    // in the sample below with a text file of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    treeView1.Nodes.Add(new myTreeNode (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       + @"\TextFile.txt") );  
  
    ```  
  
    ```cpp  
    // You should replace the bold text file   
    // in the sample below with a text file of your own choosing.  
    treeView1->Nodes->Add(new myTreeNode(String::Concat(  
       System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\TextFile.txt")));  
    ```  
  
2.  如果您傳遞的是型別為 <xref:System.Windows.Forms.TreeNode> 類別的樹狀節點，則必須將它強制轉型 \(Cast\) 為衍生類別。  強制轉型是將某個型別的物件明確轉換為另一個型別的物件。  如需強制轉型的詳細資訊，請參閱[Implicit and Explicit Conversions](../Topic/Implicit%20and%20Explicit%20Conversions%20\(Visual%20Basic\).md) \([!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]\)、[\(\) 運算子](../Topic/\(\)%20Operator%20\(C%23%20Reference\).md) \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]\) 或 [轉型運算子：\(\)](../../../../amples/snippets/visualbasic/VS_Snippets_Wpf/DocumentStructure/visualbasic/spec_withstructure-xps/_rels/.rels) \([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\)。  
  
    ```vb  
    Public Sub TreeView1_AfterSelect(ByVal sender As Object, ByVal e As System.Windows.Forms.TreeViewEventArgs) Handles TreeView1.AfterSelect  
       Dim mynode As myTreeNode  
       mynode = CType(e.node, myTreeNode)  
       MessageBox.Show("Node selected is " & mynode.filepath)  
    End Sub  
  
    ```  
  
    ```csharp  
    protected void treeView1_AfterSelect (object sender,  
    System.Windows.Forms.TreeViewEventArgs e)  
    {  
       myTreeNode myNode = (myTreeNode)e.Node;  
       MessageBox.Show("Node selected is " + myNode.FilePath);  
    }  
  
    ```  
  
    ```cpp  
    private:  
       System::Void treeView1_AfterSelect(System::Object ^  sender,  
          System::Windows::Forms::TreeViewEventArgs ^  e)  
       {  
          myTreeNode ^ myNode = safe_cast<myTreeNode^>(e->Node);  
          MessageBox::Show(String::Concat("Node selected is ",   
             myNode->FilePath));  
       }  
    ```  
  
## 請參閱  
 [TreeView 控制項](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)   
 [ListView 控制項](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)