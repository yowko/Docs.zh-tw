---
title: 如何：使用 BindingSource 元件跨表單共用繫結資料
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], BindingSource component
- data binding [Windows Forms], sharing data across forms
- BindingSource component [Windows Forms], examples
- BindingSource [Windows Forms], using with multiple forms
ms.assetid: a1a49630-db9c-4485-b888-1f62a373a4f7
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c1f9eec7d520742021747219df5f8f63058fc4f9
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a><span data-ttu-id="b8e56-102">如何：使用 BindingSource 元件跨表單共用繫結資料</span><span class="sxs-lookup"><span data-stu-id="b8e56-102">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>
<span data-ttu-id="b8e56-103">您可以使用 <xref:System.Windows.Forms.BindingSource> 元件輕鬆地跨表單共用資料。</span><span class="sxs-lookup"><span data-stu-id="b8e56-103">You can easily share data across forms using the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="b8e56-104">例如，您可能想要顯示一個唯讀表單，該表單會摘要資料來源資料，並顯示另一個可編輯的表單，其中包含在資料來源中目前所選取項目的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="b8e56-104">For example, you may want to display one read-only form that summarizes the data-source data and another editable form that contains detailed information about the currently selected item in the data source.</span></span> <span data-ttu-id="b8e56-105">這個範例將示範此案例。</span><span class="sxs-lookup"><span data-stu-id="b8e56-105">This example demonstrates this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8e56-106">範例</span><span class="sxs-lookup"><span data-stu-id="b8e56-106">Example</span></span>  
 <span data-ttu-id="b8e56-107">下列程式碼範例示範如何跨表單共用 <xref:System.Windows.Forms.BindingSource> 及其繫結的資料。</span><span class="sxs-lookup"><span data-stu-id="b8e56-107">The following code example demonstrates how to share a <xref:System.Windows.Forms.BindingSource> and its bound data across forms.</span></span> <span data-ttu-id="b8e56-108">在此範例中，會傳遞共用的 <xref:System.Windows.Forms.BindingSource> 至子表單的建構函式。</span><span class="sxs-lookup"><span data-stu-id="b8e56-108">In this example, the shared <xref:System.Windows.Forms.BindingSource> is passed to the constructor of the child form.</span></span> <span data-ttu-id="b8e56-109">子表單可讓使用者在主表單中編輯目前所選取項目的資料。</span><span class="sxs-lookup"><span data-stu-id="b8e56-109">The child form allows the user to edit the data for the currently selected item in the main form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8e56-110">在此範例中，會處理 <xref:System.Windows.Forms.BindingSource> 元件的 <xref:System.Windows.Forms.BindingSource.BindingComplete> 事件，以確保這兩個表單維持同步處理。</span><span class="sxs-lookup"><span data-stu-id="b8e56-110">The <xref:System.Windows.Forms.BindingSource.BindingComplete> event for the <xref:System.Windows.Forms.BindingSource> component is handled in the example to ensure that the two forms remain synchronized.</span></span> <span data-ttu-id="b8e56-111">如須為何進行此動作的詳細資訊，請參閱[如何：確保繫結至相同資料來源的多個控制項都能保持同步](../../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md)。</span><span class="sxs-lookup"><span data-stu-id="b8e56-111">For more information about why this is done, see [How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized](../../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b8e56-112">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="b8e56-112">Compiling the Code</span></span>  
 <span data-ttu-id="b8e56-113">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="b8e56-113">This example requires:</span></span>  
  
-   <span data-ttu-id="b8e56-114">System、System.Windows.Forms、System.Drawing、System.Data 和 System.Xml 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="b8e56-114">References to the System, System.Windows.Forms, System.Drawing, System.Data, and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="b8e56-115">Visual Basic 或 Visual C# 中建置這個範例，從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="b8e56-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="b8e56-116">您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。</span><span class="sxs-lookup"><span data-stu-id="b8e56-116">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="b8e56-117">另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="b8e56-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8e56-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8e56-118">See Also</span></span>  
 [<span data-ttu-id="b8e56-119">BindingSource 元件</span><span class="sxs-lookup"><span data-stu-id="b8e56-119">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="b8e56-120">Windows Forms 資料繫結</span><span class="sxs-lookup"><span data-stu-id="b8e56-120">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="b8e56-121">操作說明：處理資料繫結時所發生的錯誤和例外狀況</span><span class="sxs-lookup"><span data-stu-id="b8e56-121">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
