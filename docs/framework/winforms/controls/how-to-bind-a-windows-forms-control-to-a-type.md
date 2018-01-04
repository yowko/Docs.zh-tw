---
title: "如何：將 Windows Forms 控制項繫結至型別"
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
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 94faeebb-d2bc-45d6-86d7-96a42661b43d
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d346e1f853d735e8aae0dd5647c14ac6eb8c237b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type"></a><span data-ttu-id="0fe80-102">如何：將 Windows Forms 控制項繫結至型別</span><span class="sxs-lookup"><span data-stu-id="0fe80-102">How to: Bind a Windows Forms Control to a Type</span></span>
<span data-ttu-id="0fe80-103">當您在建立與資料互動的控制項時，有時會發現有必要將控制項繫結至類型，而非物件。</span><span class="sxs-lookup"><span data-stu-id="0fe80-103">When you are building controls that interact with data, you will sometimes find it necessary to bind a control to a type, rather than an object.</span></span> <span data-ttu-id="0fe80-104">特別是在設計階段會發生這種情況，此時資料可能無法使用，但是資料繫結控制項仍然需要顯示類型公用介面中的資訊。</span><span class="sxs-lookup"><span data-stu-id="0fe80-104">This situation arises especially at design time, when data may not be available, but your data-bound controls still need to display information from a type's public interface.</span></span> <span data-ttu-id="0fe80-105">例如，您可能會繫結 <xref:System.Windows.Forms.DataGridView> 控制項至 Web 服務所公開的物件，並想讓 <xref:System.Windows.Forms.DataGridView> 控制項將設計階段的資料行標記為自訂類型的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="0fe80-105">For example, you may bind a <xref:System.Windows.Forms.DataGridView> control to an object exposed by a Web service and want the <xref:System.Windows.Forms.DataGridView> control to label its columns at design time with the member names of a custom type.</span></span>  
  
 <span data-ttu-id="0fe80-106">您可以輕鬆地繫結控制項至具有 <xref:System.Windows.Forms.BindingSource> 元件的類型。</span><span class="sxs-lookup"><span data-stu-id="0fe80-106">You can easily bind a control to a type with the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fe80-107">範例</span><span class="sxs-lookup"><span data-stu-id="0fe80-107">Example</span></span>  
 <span data-ttu-id="0fe80-108">下列程式碼範例示範如何使用 <xref:System.Windows.Forms.BindingSource> 元件將 <xref:System.Windows.Forms.DataGridView> 控制項繫結至自訂類型。</span><span class="sxs-lookup"><span data-stu-id="0fe80-108">The following code example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a custom type by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="0fe80-109">當您執行範例時，您會注意到在控制項填入資料之前，<xref:System.Windows.Forms.DataGridView> 標記會反映 `Customer` 物件屬性的資料行。</span><span class="sxs-lookup"><span data-stu-id="0fe80-109">When you run the example, you'll notice the <xref:System.Windows.Forms.DataGridView> has labeled columns that reflect the properties of a `Customer` object, before the control is populated with data.</span></span> <span data-ttu-id="0fe80-110">此範例包含 [Add Customer] 按鈕，以將資料加入至 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="0fe80-110">The example has an Add Customer button to add data to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="0fe80-111">當您按一下按鈕，新 `Customer` 物件會加入至 <xref:System.Windows.Forms.BindingSource>。</span><span class="sxs-lookup"><span data-stu-id="0fe80-111">When you click the button, a new `Customer` object is added to the <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="0fe80-112">在實際案例中，可能會透過呼叫 Web 服務或其他資料來源取得資料。</span><span class="sxs-lookup"><span data-stu-id="0fe80-112">In a real-world scenario, the data might be obtained by a call to a Web service or other data source.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnector.BindingToType#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindingToType#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0fe80-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="0fe80-113">Compiling the Code</span></span>  
 <span data-ttu-id="0fe80-114">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="0fe80-114">This example requires:</span></span>  
  
-   <span data-ttu-id="0fe80-115">System 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="0fe80-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="0fe80-116">如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置命令列](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="0fe80-116">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="0fe80-117">您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。</span><span class="sxs-lookup"><span data-stu-id="0fe80-117">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="0fe80-118">另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="0fe80-118">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fe80-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="0fe80-119">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="0fe80-120">BindingSource 元件</span><span class="sxs-lookup"><span data-stu-id="0fe80-120">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)
