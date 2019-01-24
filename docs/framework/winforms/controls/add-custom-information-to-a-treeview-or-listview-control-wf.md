---
title: HOW TO：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Form)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- ListItem
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- examples [Windows Forms], ListView control
- ListView control [Windows Forms], adding custom information
- TreeView control [Windows Forms], adding custom information
ms.assetid: 68be11de-1d5b-430e-901f-cfbe48d14b19
ms.openlocfilehash: 8120f35f866c353ae1493515bed3d216776ede23
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694590"
---
# <a name="how-to-add-custom-information-to-a-treeview-or-listview-control-windows-forms"></a><span data-ttu-id="731b2-102">HOW TO：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="731b2-102">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>
<span data-ttu-id="731b2-103">您可以在 Windows Forms 中建立衍生的節點<xref:System.Windows.Forms.TreeView>控制項或中的衍生項目<xref:System.Windows.Forms.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="731b2-103">You can create a derived node in a Windows Forms <xref:System.Windows.Forms.TreeView> control or a derived item in a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="731b2-104">衍生可讓您新增您所需的任何欄位，以及新增自訂方法和建構函式來處理它們。</span><span class="sxs-lookup"><span data-stu-id="731b2-104">Derivation allows you to add any fields you require, as well as custom methods and constructors for handling them.</span></span> <span data-ttu-id="731b2-105">這項功能的其中一個用途是將 Customer 物件附加至每個樹狀節點或清單項目。</span><span class="sxs-lookup"><span data-stu-id="731b2-105">One use of this feature is to attach a Customer object to each tree node or list item.</span></span> <span data-ttu-id="731b2-106">這裡的範例是針對<xref:System.Windows.Forms.TreeView>控制項，但是相同的方法可用於<xref:System.Windows.Forms.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="731b2-106">The examples here are for a <xref:System.Windows.Forms.TreeView> control, but the same approach can be used for a <xref:System.Windows.Forms.ListView> control.</span></span>  
  
### <a name="to-derive-a-tree-node"></a><span data-ttu-id="731b2-107">衍生樹狀節點</span><span class="sxs-lookup"><span data-stu-id="731b2-107">To derive a tree node</span></span>  
  
-   <span data-ttu-id="731b2-108">建立新的節點類別，衍生自<xref:System.Windows.Forms.TreeNode>類別，且具有自訂欄位來記錄檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="731b2-108">Create a new node class, derived from the <xref:System.Windows.Forms.TreeNode> class, which has a custom field to record a file path.</span></span>  
  
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
  
### <a name="to-use-a-derived-tree-node"></a><span data-ttu-id="731b2-109">使用衍生樹狀節點</span><span class="sxs-lookup"><span data-stu-id="731b2-109">To use a derived tree node</span></span>  
  
1.  <span data-ttu-id="731b2-110">您可以使用新的衍生樹狀節點做為函式呼叫的參數。</span><span class="sxs-lookup"><span data-stu-id="731b2-110">You can use the new derived tree node as a parameter to function calls.</span></span>  
  
     <span data-ttu-id="731b2-111">在下列範例中，針對文字檔案位置設定的路徑是 [我的文件] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="731b2-111">In the example below, the path set for the location of the text file is the My Documents folder.</span></span> <span data-ttu-id="731b2-112">這是因為您可以假設大部分執行 Windows 作業系統的電腦都會包含這個目錄。</span><span class="sxs-lookup"><span data-stu-id="731b2-112">This is done because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="731b2-113">也可讓具備最小系統存取層級的使用者安全地執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="731b2-113">This also allows users with minimal system access levels to safely run the application.</span></span>  
  
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
  
2.  <span data-ttu-id="731b2-114">如果您傳遞的樹狀節點和它的類型為<xref:System.Windows.Forms.TreeNode>類別，則您必須轉換為衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="731b2-114">If you are passed the tree node and it is typed as a <xref:System.Windows.Forms.TreeNode> class, then you will need to cast to your derived class.</span></span> <span data-ttu-id="731b2-115">轉型是物件類型之間的明確轉換。</span><span class="sxs-lookup"><span data-stu-id="731b2-115">Casting is an explicit conversion from one type of object to another.</span></span> <span data-ttu-id="731b2-116">如需有關轉換的詳細資訊，請參閱 <<c0> [ 隱含和明確轉換](~/docs/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)(Visual Basic)、 [（) 運算子](~/docs/csharp/language-reference/operators/invocation-operator.md)(Visual C#)，或[轉型運算子: （)](/cpp/cpp/cast-operator-parens) ([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]).</c0></span><span class="sxs-lookup"><span data-stu-id="731b2-116">For more information on casting, see [Implicit and Explicit Conversions](~/docs/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) (Visual Basic), [() Operator](~/docs/csharp/language-reference/operators/invocation-operator.md) (Visual C#), or [Cast Operator: ()](/cpp/cpp/cast-operator-parens) ([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="731b2-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="731b2-117">See also</span></span>
- [<span data-ttu-id="731b2-118">TreeView 控制項</span><span class="sxs-lookup"><span data-stu-id="731b2-118">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)
- [<span data-ttu-id="731b2-119">ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="731b2-119">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
