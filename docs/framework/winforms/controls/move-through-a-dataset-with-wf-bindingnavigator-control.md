---
title: HOW TO：使用 Windows Forms BindingNavigator 控制項在資料集中移動
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- datasets [Windows Forms], moving through
- BindingNavigator control [Windows Forms], moving through datasets
- examples [Windows Forms], BindingNavigator control
ms.assetid: 146d97be-3d97-400e-accb-860bbf47729d
ms.openlocfilehash: 3f9759eab464d0f66712358705e2481532412162
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649218"
---
# <a name="how-to-move-through-a-dataset-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="bb2b8-102">HOW TO：使用 Windows Forms BindingNavigator 控制項在資料集中移動</span><span class="sxs-lookup"><span data-stu-id="bb2b8-102">How to: Move Through a DataSet with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="bb2b8-103">當您建立資料驅動應用程式時，通常需要向使用者顯示資料集合。</span><span class="sxs-lookup"><span data-stu-id="bb2b8-103">As you build data-driven applications, you will often need to display collections of data to users.</span></span> <span data-ttu-id="bb2b8-104"><xref:System.Windows.Forms.BindingNavigator> 控制項搭配 <xref:System.Windows.Forms.BindingSource> 元件提供方便且可擴充的方案，可在集合中移動並循序顯示項目。</span><span class="sxs-lookup"><span data-stu-id="bb2b8-104">The <xref:System.Windows.Forms.BindingNavigator> control, in conjunction with the <xref:System.Windows.Forms.BindingSource> component, provides a convenient and extensible solution for moving through a collection and displaying items sequentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb2b8-105">範例</span><span class="sxs-lookup"><span data-stu-id="bb2b8-105">Example</span></span>  
 <span data-ttu-id="bb2b8-106">下列程式碼範例示範如何使用 <xref:System.Windows.Forms.BindingNavigator> 控制項在資料中移動。</span><span class="sxs-lookup"><span data-stu-id="bb2b8-106">The following code example demonstrates how to use a <xref:System.Windows.Forms.BindingNavigator> control to move through data.</span></span> <span data-ttu-id="bb2b8-107">這個集合會包含在使用 <xref:System.Windows.Forms.BindingSource> 元件繫結至 <xref:System.Windows.Forms.TextBox> 控制項的 <xref:System.Data.DataView> 中。</span><span class="sxs-lookup"><span data-stu-id="bb2b8-107">The set is contained in a <xref:System.Data.DataView>, which is bound to a <xref:System.Windows.Forms.TextBox> control with a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb2b8-108">在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。</span><span class="sxs-lookup"><span data-stu-id="bb2b8-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="bb2b8-109">使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。</span><span class="sxs-lookup"><span data-stu-id="bb2b8-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="bb2b8-110">如需詳細資訊，請參閱[保護連線資訊](../../data/adonet/protecting-connection-information.md)。</span><span class="sxs-lookup"><span data-stu-id="bb2b8-110">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataNavigator#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataNavigator#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bb2b8-111">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="bb2b8-111">Compiling the Code</span></span>  
 <span data-ttu-id="bb2b8-112">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="bb2b8-112">This example requires:</span></span>  
  
- <span data-ttu-id="bb2b8-113">System、System.Data、System.Drawing、System.Windows.Forms 和 System.Xml 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="bb2b8-113">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="bb2b8-114">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="bb2b8-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="bb2b8-115">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="bb2b8-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb2b8-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb2b8-116">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="bb2b8-117">BindingNavigator 控制項</span><span class="sxs-lookup"><span data-stu-id="bb2b8-117">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="bb2b8-118">BindingSource 元件</span><span class="sxs-lookup"><span data-stu-id="bb2b8-118">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="bb2b8-119">如何：將 Windows Forms 控制項繫結至型別</span><span class="sxs-lookup"><span data-stu-id="bb2b8-119">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
