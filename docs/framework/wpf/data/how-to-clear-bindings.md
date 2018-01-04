---
title: "操作說明：清除繫結"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bindings [WPF], clearing
- clearing bindings [WPF]
- data binding [WPF], clearing bindings
ms.assetid: 73962a93-32a9-4bcd-9240-bcfbb239093a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: af45d504eb4e7d45808f787925a90c8e0ed19476
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-clear-bindings"></a><span data-ttu-id="67060-102">操作說明：清除繫結</span><span class="sxs-lookup"><span data-stu-id="67060-102">How to: Clear Bindings</span></span>
<span data-ttu-id="67060-103">這個範例顯示如何清除物件的繫結。</span><span class="sxs-lookup"><span data-stu-id="67060-103">This example shows how to clear bindings from an object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67060-104">範例</span><span class="sxs-lookup"><span data-stu-id="67060-104">Example</span></span>  
 <span data-ttu-id="67060-105">若要清除從物件上的個別屬性的繫結，請呼叫<xref:System.Windows.Data.BindingOperations.ClearBinding%2A>如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="67060-105">To clear a binding from an individual property on an object, call <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> as shown in the following example.</span></span> <span data-ttu-id="67060-106">下列範例會移除從繫結<xref:System.Windows.Controls.TextBlock.TextProperty>的*mytext*、<xref:System.Windows.Controls.TextBlock>物件。</span><span class="sxs-lookup"><span data-stu-id="67060-106">The following example removes the binding from the <xref:System.Windows.Controls.TextBlock.TextProperty> of *mytext*, a <xref:System.Windows.Controls.TextBlock> object.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 <span data-ttu-id="67060-107">清除繫結會移除繫結，讓相依性屬性的值還原為沒有繫結時應該有的值。</span><span class="sxs-lookup"><span data-stu-id="67060-107">Clearing the binding removes the binding so that the value of the dependency property is changed to whatever it would have been without the binding.</span></span> <span data-ttu-id="67060-108">這個值可以是預設值、繼承值或是資料範本繫結的值。</span><span class="sxs-lookup"><span data-stu-id="67060-108">This value could be a default value, an inherited value, or a value from a data template binding.</span></span>  
  
 <span data-ttu-id="67060-109">若要清除的物件上的所有可能屬性繫結，請使用<xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>。</span><span class="sxs-lookup"><span data-stu-id="67060-109">To clear bindings from all possible properties on an object, use <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67060-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="67060-110">See Also</span></span>  
 <xref:System.Windows.Data.BindingOperations>  
 [<span data-ttu-id="67060-111">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="67060-111">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="67060-112">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="67060-112">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
