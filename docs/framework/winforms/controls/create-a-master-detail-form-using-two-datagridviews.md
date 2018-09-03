---
title: 如何： 建立主版詳細資料表單使用兩個 Windows Form DataGridView 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], creating
ms.assetid: 99f6e876-3f7f-4139-9063-e36587c95b02
ms.openlocfilehash: 328970c5cc14669770793070942dd32f0144c159
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43487100"
---
# <a name="how-to-create-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a><span data-ttu-id="f8c6b-102">如何：使用兩個 Windows Form DataGridView 控制項建立主從式表單</span><span class="sxs-lookup"><span data-stu-id="f8c6b-102">How to: Create a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="f8c6b-103">下列程式碼範例會使用兩個 <xref:System.Windows.Forms.DataGridView> 控制項繫結至兩個 <xref:System.Windows.Forms.BindingSource> 元件來建立主從式表單。</span><span class="sxs-lookup"><span data-stu-id="f8c6b-103">The following code example creates a master/detail form using two <xref:System.Windows.Forms.DataGridView> controls bound to two <xref:System.Windows.Forms.BindingSource> components.</span></span> <span data-ttu-id="f8c6b-104">資料來源是 <xref:System.Data.DataSet>，包含來自 Northwind SQL Server 範例資料庫的 `Customers` 和 `Orders` 資料表，以及透過 `CustomerID` 資料行和這兩者產生關聯的 <xref:System.Data.DataRelation>。</span><span class="sxs-lookup"><span data-stu-id="f8c6b-104">The data source is a <xref:System.Data.DataSet> that contains the `Customers` and `Orders` tables from the Northwind SQL Server sample database along with a <xref:System.Data.DataRelation> that relates the two through the `CustomerID` column.</span></span>  
  
 <span data-ttu-id="f8c6b-105">一個 <xref:System.Windows.Forms.BindingSource> 會繫結至資料集中的父代 `Customers` 資料表。</span><span class="sxs-lookup"><span data-stu-id="f8c6b-105">One <xref:System.Windows.Forms.BindingSource> is bound to the parent `Customers` table in the data set.</span></span> <span data-ttu-id="f8c6b-106">此資料會顯示在 <xref:System.Windows.Forms.DataGridView> 主控制項。</span><span class="sxs-lookup"><span data-stu-id="f8c6b-106">This data is displayed in the master <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="f8c6b-107">其他 <xref:System.Windows.Forms.BindingSource> 會繫結至第一個資料連接器。</span><span class="sxs-lookup"><span data-stu-id="f8c6b-107">The other <xref:System.Windows.Forms.BindingSource> is bound to the first data connector.</span></span> <span data-ttu-id="f8c6b-108">第二個 <xref:System.Windows.Forms.BindingSource> 的 <xref:System.Windows.Forms.BindingSource.DataMember%2A> 屬性會設為 <xref:System.Data.DataRelation> 的名稱。</span><span class="sxs-lookup"><span data-stu-id="f8c6b-108">The <xref:System.Windows.Forms.BindingSource.DataMember%2A> property of the second <xref:System.Windows.Forms.BindingSource> is set to the <xref:System.Data.DataRelation> name.</span></span> <span data-ttu-id="f8c6b-109">這會導致相關的 <xref:System.Windows.Forms.DataGridView> 詳細資料控制項顯示 `Orders` 子資料表的資料列，對應到 <xref:System.Windows.Forms.DataGridView> 主控制項中的目前資料列。</span><span class="sxs-lookup"><span data-stu-id="f8c6b-109">This causes the associated detail <xref:System.Windows.Forms.DataGridView> control to display the rows of the child `Orders` table that correspond to the current row in the master <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <span data-ttu-id="f8c6b-110">如需這個程式碼範例的完整說明，請參閱 <<c0> [ 逐步解說： 建立主版/詳細表單使用兩個 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md)。</span><span class="sxs-lookup"><span data-stu-id="f8c6b-110">For a complete explanation of this code example, see [Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8c6b-111">範例</span><span class="sxs-lookup"><span data-stu-id="f8c6b-111">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f8c6b-112">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="f8c6b-112">Compiling the Code</span></span>  
 <span data-ttu-id="f8c6b-113">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="f8c6b-113">This example requires:</span></span>  
  
 <span data-ttu-id="f8c6b-114">System、System.Data、System.Windows.Forms 和 System.XML 組件的參考。 </span><span class="sxs-lookup"><span data-stu-id="f8c6b-114">References to the System, System.Data, System.Windows.Forms, and System.XML assemblies.</span></span>  
  
-   <span data-ttu-id="f8c6b-115">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="f8c6b-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="f8c6b-116">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="f8c6b-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="f8c6b-117">另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Forms 程式碼範例](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="f8c6b-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f8c6b-118">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="f8c6b-118">.NET Framework Security</span></span>  
 <span data-ttu-id="f8c6b-119">在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。</span><span class="sxs-lookup"><span data-stu-id="f8c6b-119">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="f8c6b-120">使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。</span><span class="sxs-lookup"><span data-stu-id="f8c6b-120">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="f8c6b-121">如需詳細資訊，請參閱[保護連線資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)。</span><span class="sxs-lookup"><span data-stu-id="f8c6b-121">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8c6b-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8c6b-122">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="f8c6b-123">逐步解說：使用兩個 Windows Forms DataGridView 控制項建立主從式表單</span><span class="sxs-lookup"><span data-stu-id="f8c6b-123">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md)  
 [<span data-ttu-id="f8c6b-124">在 Windows Forms DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="f8c6b-124">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="f8c6b-125">保護連線資訊</span><span class="sxs-lookup"><span data-stu-id="f8c6b-125">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)
