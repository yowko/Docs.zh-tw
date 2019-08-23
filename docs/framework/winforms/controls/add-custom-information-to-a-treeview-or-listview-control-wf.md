---
title: 作法：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)
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
ms.openlocfilehash: f588a00c430eb1ae1f0cdcde6b7dd22f0c8671c5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956991"
---
# <a name="how-to-add-custom-information-to-a-treeview-or-listview-control-windows-forms"></a><span data-ttu-id="89fb1-102">作法：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="89fb1-102">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>
<span data-ttu-id="89fb1-103">您可以在<xref:System.Windows.Forms.TreeView> <xref:System.Windows.Forms.ListView>控制項中的 Windows Forms 控制項或衍生專案中建立衍生節點。</span><span class="sxs-lookup"><span data-stu-id="89fb1-103">You can create a derived node in a Windows Forms <xref:System.Windows.Forms.TreeView> control or a derived item in a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="89fb1-104">衍生可讓您新增您所需的任何欄位，以及新增自訂方法和建構函式來處理它們。</span><span class="sxs-lookup"><span data-stu-id="89fb1-104">Derivation allows you to add any fields you require, as well as custom methods and constructors for handling them.</span></span> <span data-ttu-id="89fb1-105">這項功能的其中一個用途是將 Customer 物件附加至每個樹狀節點或清單項目。</span><span class="sxs-lookup"><span data-stu-id="89fb1-105">One use of this feature is to attach a Customer object to each tree node or list item.</span></span> <span data-ttu-id="89fb1-106">這裡的範例適用于<xref:System.Windows.Forms.TreeView>控制項, 但相同的方法也可<xref:System.Windows.Forms.ListView>用於控制項。</span><span class="sxs-lookup"><span data-stu-id="89fb1-106">The examples here are for a <xref:System.Windows.Forms.TreeView> control, but the same approach can be used for a <xref:System.Windows.Forms.ListView> control.</span></span>  
  
### <a name="to-derive-a-tree-node"></a><span data-ttu-id="89fb1-107">衍生樹狀節點</span><span class="sxs-lookup"><span data-stu-id="89fb1-107">To derive a tree node</span></span>  
  
- <span data-ttu-id="89fb1-108">建立新的節點類別 (衍生<xref:System.Windows.Forms.TreeNode>自類別), 其中包含用來記錄檔案路徑的自訂欄位。</span><span class="sxs-lookup"><span data-stu-id="89fb1-108">Create a new node class, derived from the <xref:System.Windows.Forms.TreeNode> class, which has a custom field to record a file path.</span></span>  
  
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
  
### <a name="to-use-a-derived-tree-node"></a><span data-ttu-id="89fb1-109">使用衍生樹狀節點</span><span class="sxs-lookup"><span data-stu-id="89fb1-109">To use a derived tree node</span></span>  
  
1. <span data-ttu-id="89fb1-110">您可以使用新的衍生樹狀節點做為函式呼叫的參數。</span><span class="sxs-lookup"><span data-stu-id="89fb1-110">You can use the new derived tree node as a parameter to function calls.</span></span>  
  
     <span data-ttu-id="89fb1-111">在下列範例中，針對文字檔案位置設定的路徑是 [我的文件] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="89fb1-111">In the example below, the path set for the location of the text file is the My Documents folder.</span></span> <span data-ttu-id="89fb1-112">這是因為您可以假設大部分執行 Windows 作業系統的電腦都會包含這個目錄。</span><span class="sxs-lookup"><span data-stu-id="89fb1-112">This is done because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="89fb1-113">也可讓具備最小系統存取層級的使用者安全地執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="89fb1-113">This also allows users with minimal system access levels to safely run the application.</span></span>  
  
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
    treeView1.Nodes.Add(new myTreeNode(System.Environment.GetFolderPath
       (System.Environment.SpecialFolder.Personal)
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
  
2. <span data-ttu-id="89fb1-114">如果您傳遞樹狀節點, 而且它是以<xref:System.Windows.Forms.TreeNode>類別的形式輸入, 則您必須將轉換成衍生類別。</span><span class="sxs-lookup"><span data-stu-id="89fb1-114">If you are passed the tree node and it is typed as a <xref:System.Windows.Forms.TreeNode> class, then you will need to cast to your derived class.</span></span> <span data-ttu-id="89fb1-115">轉型是物件類型之間的明確轉換。</span><span class="sxs-lookup"><span data-stu-id="89fb1-115">Casting is an explicit conversion from one type of object to another.</span></span> <span data-ttu-id="89fb1-116">如需轉換的詳細資訊, 請參閱[隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)(Visual Basic)、轉[型和類型轉換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)(Visual C#) 或[Cast 運算子: ()](/cpp/cpp/cast-operator-parens) (visual C++)。</span><span class="sxs-lookup"><span data-stu-id="89fb1-116">For more information on casting, see [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) (Visual Basic), [Casting and type conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md) (Visual C#), or [Cast Operator: ()](/cpp/cpp/cast-operator-parens) (Visual C++).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="89fb1-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89fb1-117">See also</span></span>

- [<span data-ttu-id="89fb1-118">TreeView 控制項</span><span class="sxs-lookup"><span data-stu-id="89fb1-118">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="89fb1-119">ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="89fb1-119">ListView Control</span></span>](listview-control-windows-forms.md)
