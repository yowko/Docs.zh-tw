---
title: 作法：使用 BindingSource 元件跨表單共用繫結資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], BindingSource component
- data binding [Windows Forms], sharing data across forms
- BindingSource component [Windows Forms], examples
- BindingSource [Windows Forms], using with multiple forms
ms.assetid: a1a49630-db9c-4485-b888-1f62a373a4f7
ms.openlocfilehash: aa497194fd4ac65f48773a45175333a1d862b453
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956079"
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a><span data-ttu-id="db81c-102">作法：使用 BindingSource 元件跨表單共用繫結資料</span><span class="sxs-lookup"><span data-stu-id="db81c-102">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>
<span data-ttu-id="db81c-103">您可以使用 <xref:System.Windows.Forms.BindingSource> 元件輕鬆地跨表單共用資料。</span><span class="sxs-lookup"><span data-stu-id="db81c-103">You can easily share data across forms using the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="db81c-104">例如，您可能想要顯示一個唯讀表單，該表單會摘要資料來源資料，並顯示另一個可編輯的表單，其中包含在資料來源中目前所選取項目的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="db81c-104">For example, you may want to display one read-only form that summarizes the data-source data and another editable form that contains detailed information about the currently selected item in the data source.</span></span> <span data-ttu-id="db81c-105">這個範例將示範此案例。</span><span class="sxs-lookup"><span data-stu-id="db81c-105">This example demonstrates this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db81c-106">範例</span><span class="sxs-lookup"><span data-stu-id="db81c-106">Example</span></span>  
 <span data-ttu-id="db81c-107">下列程式碼範例示範如何跨表單共用 <xref:System.Windows.Forms.BindingSource> 及其繫結的資料。</span><span class="sxs-lookup"><span data-stu-id="db81c-107">The following code example demonstrates how to share a <xref:System.Windows.Forms.BindingSource> and its bound data across forms.</span></span> <span data-ttu-id="db81c-108">在此範例中，會傳遞共用的 <xref:System.Windows.Forms.BindingSource> 至子表單的建構函式。</span><span class="sxs-lookup"><span data-stu-id="db81c-108">In this example, the shared <xref:System.Windows.Forms.BindingSource> is passed to the constructor of the child form.</span></span> <span data-ttu-id="db81c-109">子表單可讓使用者在主表單中編輯目前所選取項目的資料。</span><span class="sxs-lookup"><span data-stu-id="db81c-109">The child form allows the user to edit the data for the currently selected item in the main form.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="db81c-110">在此範例中，會處理 <xref:System.Windows.Forms.BindingSource> 元件的 <xref:System.Windows.Forms.BindingSource.BindingComplete> 事件，以確保這兩個表單維持同步處理。</span><span class="sxs-lookup"><span data-stu-id="db81c-110">The <xref:System.Windows.Forms.BindingSource.BindingComplete> event for the <xref:System.Windows.Forms.BindingSource> component is handled in the example to ensure that the two forms remain synchronized.</span></span> <span data-ttu-id="db81c-111">如需如何完成此作業的詳細資訊, [請參閱如何:請確定系結至相同資料來源的多個](../multiple-controls-bound-to-data-source-synchronized.md)控制項保持同步。</span><span class="sxs-lookup"><span data-stu-id="db81c-111">For more information about why this is done, see [How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized](../multiple-controls-bound-to-data-source-synchronized.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="db81c-112">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="db81c-112">Compiling the Code</span></span>  
 <span data-ttu-id="db81c-113">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="db81c-113">This example requires:</span></span>  
  
- <span data-ttu-id="db81c-114">System、System.Windows.Forms、System.Drawing、System.Data 和 System.Xml 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="db81c-114">References to the System, System.Windows.Forms, System.Drawing, System.Data, and System.Xml assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db81c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db81c-115">See also</span></span>

- [<span data-ttu-id="db81c-116">BindingSource 元件</span><span class="sxs-lookup"><span data-stu-id="db81c-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="db81c-117">Windows Forms 資料繫結</span><span class="sxs-lookup"><span data-stu-id="db81c-117">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="db81c-118">如何：處理資料系結時所發生的錯誤和例外狀況</span><span class="sxs-lookup"><span data-stu-id="db81c-118">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
