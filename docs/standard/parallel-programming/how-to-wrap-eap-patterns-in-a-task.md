---
title: 如何：將 EAP 模式包裝在工作中
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to wrap EAP patterns
ms.assetid: f11ed467-af2f-4504-8a2e-299a6c36d44e
ms.openlocfilehash: ac7436892c644340286bb4670bf75c9cd63a8ce5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73106827"
---
# <a name="how-to-wrap-eap-patterns-in-a-task"></a><span data-ttu-id="e5f67-102">如何：將 EAP 模式包裝在工作中</span><span class="sxs-lookup"><span data-stu-id="e5f67-102">How to: Wrap EAP Patterns in a Task</span></span>
<span data-ttu-id="e5f67-103">下列範例將示範如何使用 <xref:System.Threading.Tasks.TaskCompletionSource%601>，將事件式非同步模式 (EAP) 的任意序列公開為單一工作。</span><span class="sxs-lookup"><span data-stu-id="e5f67-103">The following example shows how to expose an arbitrary sequence of Event-Based Asynchronous Pattern (EAP) operations as one task by using a <xref:System.Threading.Tasks.TaskCompletionSource%601>.</span></span> <span data-ttu-id="e5f67-104">此範例也示範如何使用 <xref:System.Threading.CancellationToken> 在 <xref:System.Net.WebClient> 物件上叫用內建的取消方法。</span><span class="sxs-lookup"><span data-stu-id="e5f67-104">The example also shows how to use a <xref:System.Threading.CancellationToken> to invoke the built-in cancellation methods on the <xref:System.Net.WebClient> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5f67-105">範例</span><span class="sxs-lookup"><span data-stu-id="e5f67-105">Example</span></span>  
 [!code-csharp[FromAsync#08](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#08)]
 [!code-vb[FromAsync#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="e5f67-106">請參閱</span><span class="sxs-lookup"><span data-stu-id="e5f67-106">See also</span></span>

- [<span data-ttu-id="e5f67-107">TPL 和傳統 .NET Framework 非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="e5f67-107">TPL and Traditional .NET Framework Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)
