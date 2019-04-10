---
title: HOW TO：確保繫結至相同資料來源的多個控制項都能保持同步
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding multiple
- controls [Windows Forms], synchronizing with data source
ms.assetid: c2f0ecc6-11e6-4c2c-a1ca-0759630c451e
ms.openlocfilehash: 8f7e59720420a845fa195b8c0fb078a8699a9bc3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170335"
---
# <a name="how-to-ensure-multiple-controls-bound-to-the-same-data-source-remain-synchronized"></a><span data-ttu-id="c2e03-102">HOW TO：確保繫結至相同資料來源的多個控制項都能保持同步</span><span class="sxs-lookup"><span data-stu-id="c2e03-102">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>
<span data-ttu-id="c2e03-103">使用 Windows Form 中的資料繫結時，有時候多個控制項繫結至相同的資料來源中。</span><span class="sxs-lookup"><span data-stu-id="c2e03-103">Oftentimes when working with data binding in Windows Forms, multiple controls are bound to the same data source.</span></span> <span data-ttu-id="c2e03-104">在某些情況下，可能必須採取額外步驟以確保控制項的繫結的內容維持彼此以及與資料來源同步處理。</span><span class="sxs-lookup"><span data-stu-id="c2e03-104">In some cases, it may be necessary to take extra steps to ensure that the bound properties of the controls remain synchronized with each other and the data source.</span></span> <span data-ttu-id="c2e03-105">這些步驟會需要有兩種情況：</span><span class="sxs-lookup"><span data-stu-id="c2e03-105">These steps are necessary in two situations:</span></span>  
  
-   <span data-ttu-id="c2e03-106">如果資料來源不會實作<xref:System.ComponentModel.IBindingList>，並因此產生<xref:System.ComponentModel.IBindingList.ListChanged>類型的事件<xref:System.ComponentModel.ListChangedType.ItemChanged>。</span><span class="sxs-lookup"><span data-stu-id="c2e03-106">If the data source does not implement <xref:System.ComponentModel.IBindingList>, and therefore generate <xref:System.ComponentModel.IBindingList.ListChanged> events of type <xref:System.ComponentModel.ListChangedType.ItemChanged>.</span></span>  
  
-   <span data-ttu-id="c2e03-107">如果資料來源實作<xref:System.ComponentModel.IEditableObject>。</span><span class="sxs-lookup"><span data-stu-id="c2e03-107">If the data source implements <xref:System.ComponentModel.IEditableObject>.</span></span>  
  
 <span data-ttu-id="c2e03-108">在前一個案例中，您可以使用<xref:System.Windows.Forms.BindingSource>繫結至控制項的資料來源。</span><span class="sxs-lookup"><span data-stu-id="c2e03-108">In the former case, you can use a <xref:System.Windows.Forms.BindingSource> to bind the data source to the controls.</span></span> <span data-ttu-id="c2e03-109">在後者的情況下，您可以使用<xref:System.Windows.Forms.BindingSource>，並處理<xref:System.Windows.Forms.BindingSource.BindingComplete>事件，並呼叫<xref:System.Windows.Forms.BindingManagerBase.EndCurrentEdit%2A>相關<xref:System.Windows.Forms.BindingManagerBase>。</span><span class="sxs-lookup"><span data-stu-id="c2e03-109">In the latter case, you use a <xref:System.Windows.Forms.BindingSource> and handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event and call <xref:System.Windows.Forms.BindingManagerBase.EndCurrentEdit%2A> on the associated <xref:System.Windows.Forms.BindingManagerBase>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2e03-110">範例</span><span class="sxs-lookup"><span data-stu-id="c2e03-110">Example</span></span>  
 <span data-ttu-id="c2e03-111">下列程式碼範例示範如何將三個控制項繫結 — 兩個文字方塊控制項和<xref:System.Windows.Forms.DataGridView>控制 — 中的相同資料行<xref:System.Data.DataSet>使用<xref:System.Windows.Forms.BindingSource>元件。</span><span class="sxs-lookup"><span data-stu-id="c2e03-111">The following code example demonstrates how to bind three controls—two text-box controls and a <xref:System.Windows.Forms.DataGridView> control—to the same column in a <xref:System.Data.DataSet> using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="c2e03-112">此範例示範如何處理<xref:System.Windows.Forms.BindingSource.BindingComplete>事件，並確保其中一個文字方塊的文字值變更時，其他的文字方塊和<xref:System.Windows.Forms.DataGridView>控制項以正確的值更新。</span><span class="sxs-lookup"><span data-stu-id="c2e03-112">This example demonstrates how to handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event and ensure that when the text value of one text box is changed, the additional text box and the <xref:System.Windows.Forms.DataGridView> control are updated with the correct value.</span></span>  
  
 <span data-ttu-id="c2e03-113">此範例會使用<xref:System.Windows.Forms.BindingSource>繫結資料來源和控制項。</span><span class="sxs-lookup"><span data-stu-id="c2e03-113">The example uses a <xref:System.Windows.Forms.BindingSource> to bind the data source and the controls.</span></span> <span data-ttu-id="c2e03-114">或者，您可以直接繫結控制項至資料來源，並擷取<xref:System.Windows.Forms.BindingManagerBase>從表單的繫結<xref:System.Windows.Forms.Control.BindingContext%2A>，然後處理<xref:System.Windows.Forms.BindingManagerBase.BindingComplete>事件<xref:System.Windows.Forms.BindingManagerBase>。</span><span class="sxs-lookup"><span data-stu-id="c2e03-114">Alternatively, you can bind the controls directly to the data source and retrieve the <xref:System.Windows.Forms.BindingManagerBase> for the binding from the form's <xref:System.Windows.Forms.Control.BindingContext%2A> and then handle the <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> event for the <xref:System.Windows.Forms.BindingManagerBase>.</span></span> <span data-ttu-id="c2e03-115">如何執行這項操作的範例，請參閱 [說明] 頁面，關於<xref:System.Windows.Forms.BindingManagerBase.BindingComplete>事件的<xref:System.Windows.Forms.BindingManagerBase>。</span><span class="sxs-lookup"><span data-stu-id="c2e03-115">For an example of how to do this, see the Help page about the <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> event of <xref:System.Windows.Forms.BindingManagerBase>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleControls#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleControls#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c2e03-116">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="c2e03-116">Compiling the Code</span></span>  
  
-   <span data-ttu-id="c2e03-117">此程式碼範例需要</span><span class="sxs-lookup"><span data-stu-id="c2e03-117">This code example requires</span></span>  
  
-   <span data-ttu-id="c2e03-118"><xref:System>、<xref:System.Windows.Forms> 和 <xref:System.Drawing> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="c2e03-118">References to the <xref:System>, <xref:System.Windows.Forms>, and <xref:System.Drawing> assemblies.</span></span>  
  
-   <span data-ttu-id="c2e03-119">使用表單<xref:System.Windows.Forms.Form.Load>處理的事件和呼叫`InitializeControlsAndDataSource`方法，在範例中，從表單的<xref:System.Windows.Forms.Form.Load>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="c2e03-119">A form with the <xref:System.Windows.Forms.Form.Load> event handled and a call to the `InitializeControlsAndDataSource` method in the example from the form's <xref:System.Windows.Forms.Form.Load> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2e03-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2e03-120">See also</span></span>

- [<span data-ttu-id="c2e03-121">HOW TO：使用 BindingSource 元件跨表單共用繫結資料</span><span class="sxs-lookup"><span data-stu-id="c2e03-121">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>](./controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)
- [<span data-ttu-id="c2e03-122">Windows Form 資料繫結中的變更告知</span><span class="sxs-lookup"><span data-stu-id="c2e03-122">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)
- [<span data-ttu-id="c2e03-123">與資料繫結相關的介面</span><span class="sxs-lookup"><span data-stu-id="c2e03-123">Interfaces Related to Data Binding</span></span>](interfaces-related-to-data-binding.md)
- [<span data-ttu-id="c2e03-124">Windows Form 資料繫結</span><span class="sxs-lookup"><span data-stu-id="c2e03-124">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
