---
title: "如何：確保繫結至相同資料來源的多個控制項都能保持同步"
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
- controls [Windows Forms], binding multiple
- controls [Windows Forms], synchronizing with data source
ms.assetid: c2f0ecc6-11e6-4c2c-a1ca-0759630c451e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 227ad36e87c3deceb7fefe3cd19013fc8e76c686
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-ensure-multiple-controls-bound-to-the-same-data-source-remain-synchronized"></a><span data-ttu-id="09c62-102">如何：確保繫結至相同資料來源的多個控制項都能保持同步</span><span class="sxs-lookup"><span data-stu-id="09c62-102">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>
<span data-ttu-id="09c62-103">有時候當使用 Windows Form 中的資料繫結時，多個控制項所繫結至相同的資料來源。</span><span class="sxs-lookup"><span data-stu-id="09c62-103">Oftentimes when working with data binding in Windows Forms, multiple controls are bound to the same data source.</span></span> <span data-ttu-id="09c62-104">在某些情況下，可能必須採取額外步驟以確保控制項的繫結的內容中與其他每個及資料來源同步處理。</span><span class="sxs-lookup"><span data-stu-id="09c62-104">In some cases, it may be necessary to take extra steps to ensure that the bound properties of the controls remain synchronized with each other and the data source.</span></span> <span data-ttu-id="09c62-105">這些步驟是兩個情況中，必須：</span><span class="sxs-lookup"><span data-stu-id="09c62-105">These steps are necessary in two situations:</span></span>  
  
-   <span data-ttu-id="09c62-106">如果資料來源沒有實作<xref:System.ComponentModel.IBindingList>，並因此產生<xref:System.ComponentModel.IBindingList.ListChanged>類型的事件<xref:System.ComponentModel.ListChangedType.ItemChanged>。</span><span class="sxs-lookup"><span data-stu-id="09c62-106">If the data source does not implement <xref:System.ComponentModel.IBindingList>, and therefore generate <xref:System.ComponentModel.IBindingList.ListChanged> events of type <xref:System.ComponentModel.ListChangedType.ItemChanged>.</span></span>  
  
-   <span data-ttu-id="09c62-107">如果資料來源實作<xref:System.ComponentModel.IEditableObject>。</span><span class="sxs-lookup"><span data-stu-id="09c62-107">If the data source implements <xref:System.ComponentModel.IEditableObject>.</span></span>  
  
 <span data-ttu-id="09c62-108">在前一個案例中，您可以使用<xref:System.Windows.Forms.BindingSource>繫結至控制項的資料來源。</span><span class="sxs-lookup"><span data-stu-id="09c62-108">In the former case, you can use a <xref:System.Windows.Forms.BindingSource> to bind the data source to the controls.</span></span> <span data-ttu-id="09c62-109">在後者的情況下，您可以使用<xref:System.Windows.Forms.BindingSource>及處理<xref:System.Windows.Forms.BindingSource.BindingComplete>事件和呼叫<xref:System.Windows.Forms.BindingManagerBase.EndCurrentEdit%2A>上相關聯<xref:System.Windows.Forms.BindingManagerBase>。</span><span class="sxs-lookup"><span data-stu-id="09c62-109">In the latter case, you use a <xref:System.Windows.Forms.BindingSource> and handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event and call <xref:System.Windows.Forms.BindingManagerBase.EndCurrentEdit%2A> on the associated <xref:System.Windows.Forms.BindingManagerBase>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09c62-110">範例</span><span class="sxs-lookup"><span data-stu-id="09c62-110">Example</span></span>  
 <span data-ttu-id="09c62-111">下列程式碼範例示範如何繫結的三個控制項，兩個文字方塊控制項和<xref:System.Windows.Forms.DataGridView>控制項 — 中的相同資料行<xref:System.Data.DataSet>使用<xref:System.Windows.Forms.BindingSource>元件。</span><span class="sxs-lookup"><span data-stu-id="09c62-111">The following code example demonstrates how to bind three controls—two text-box controls and a <xref:System.Windows.Forms.DataGridView> control—to the same column in a <xref:System.Data.DataSet> using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="09c62-112">這個範例示範如何處理<xref:System.Windows.Forms.BindingSource.BindingComplete>事件，並確定單一文字方塊的文字值變更時，其他文字方塊和<xref:System.Windows.Forms.DataGridView>控制項以正確的值更新。</span><span class="sxs-lookup"><span data-stu-id="09c62-112">This example demonstrates how to handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event and ensure that when the text value of one text box is changed, the additional text box and the <xref:System.Windows.Forms.DataGridView> control are updated with the correct value.</span></span>  
  
 <span data-ttu-id="09c62-113">此範例會使用<xref:System.Windows.Forms.BindingSource>繫結資料來源和控制項。</span><span class="sxs-lookup"><span data-stu-id="09c62-113">The example uses a <xref:System.Windows.Forms.BindingSource> to bind the data source and the controls.</span></span> <span data-ttu-id="09c62-114">或者，您可以直接繫結控制項至資料來源並擷取<xref:System.Windows.Forms.BindingManagerBase>從表單的繫結<xref:System.Windows.Forms.Control.BindingContext%2A>然後處理<xref:System.Windows.Forms.BindingManagerBase.BindingComplete>事件<xref:System.Windows.Forms.BindingManagerBase>。</span><span class="sxs-lookup"><span data-stu-id="09c62-114">Alternatively, you can bind the controls directly to the data source and retrieve the <xref:System.Windows.Forms.BindingManagerBase> for the binding from the form's <xref:System.Windows.Forms.Control.BindingContext%2A> and then handle the <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> event for the <xref:System.Windows.Forms.BindingManagerBase>.</span></span> <span data-ttu-id="09c62-115">如何執行此動作的範例，請參閱 [說明] 頁面，關於<xref:System.Windows.Forms.BindingManagerBase.BindingComplete>事件<xref:System.Windows.Forms.BindingManagerBase>。</span><span class="sxs-lookup"><span data-stu-id="09c62-115">For an example of how to do this, see the Help page about the <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> event of <xref:System.Windows.Forms.BindingManagerBase>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="09c62-116">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="09c62-116">Compiling the Code</span></span>  
  
-   <span data-ttu-id="09c62-117">這個程式碼範例要求</span><span class="sxs-lookup"><span data-stu-id="09c62-117">This code example requires</span></span>  
  
-   <span data-ttu-id="09c62-118"><xref:System>、<xref:System.Windows.Forms> 和 <xref:System.Drawing> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="09c62-118">References to the <xref:System>, <xref:System.Windows.Forms>, and <xref:System.Drawing> assemblies.</span></span>  
  
-   <span data-ttu-id="09c62-119">表單具有<xref:System.Windows.Forms.Form.Load>處理事件和呼叫`InitializeControlsAndDataSource`從表單的範例方法<xref:System.Windows.Forms.Form.Load>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="09c62-119">A form with the <xref:System.Windows.Forms.Form.Load> event handled and a call to the `InitializeControlsAndDataSource` method in the example from the form's <xref:System.Windows.Forms.Form.Load> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09c62-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="09c62-120">See Also</span></span>  
 [<span data-ttu-id="09c62-121">操作說明：使用 BindingSource 元件跨表單共用繫結資料</span><span class="sxs-lookup"><span data-stu-id="09c62-121">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>](../../../docs/framework/winforms/controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 [<span data-ttu-id="09c62-122">Windows Forms 資料繫結中的變更告知</span><span class="sxs-lookup"><span data-stu-id="09c62-122">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [<span data-ttu-id="09c62-123">與資料繫結相關的介面</span><span class="sxs-lookup"><span data-stu-id="09c62-123">Interfaces Related to Data Binding</span></span>](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)  
 [<span data-ttu-id="09c62-124">Windows Forms 資料繫結</span><span class="sxs-lookup"><span data-stu-id="09c62-124">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)
