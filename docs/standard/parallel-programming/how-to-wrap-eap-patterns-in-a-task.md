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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4287879bd95f7bc1e1dc99f74fa0d7cc0fe737f
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45593721"
---
# <a name="how-to-wrap-eap-patterns-in-a-task"></a><span data-ttu-id="c01b2-102">如何：將 EAP 模式包裝在工作中</span><span class="sxs-lookup"><span data-stu-id="c01b2-102">How to: Wrap EAP Patterns in a Task</span></span>
<span data-ttu-id="c01b2-103">下列範例將示範如何使用 <xref:System.Threading.Tasks.TaskCompletionSource%601>，將事件式非同步模式 (EAP) 的任意序列公開為單一工作。</span><span class="sxs-lookup"><span data-stu-id="c01b2-103">The following example shows how to expose an arbitrary sequence of Event-Based Asynchronous Pattern (EAP) operations as one task by using a <xref:System.Threading.Tasks.TaskCompletionSource%601>.</span></span> <span data-ttu-id="c01b2-104">此範例也示範如何使用 <xref:System.Threading.CancellationToken> 在 <xref:System.Net.WebClient> 物件上叫用內建的取消方法。</span><span class="sxs-lookup"><span data-stu-id="c01b2-104">The example also shows how to use a <xref:System.Threading.CancellationToken> to invoke the built-in cancellation methods on the <xref:System.Net.WebClient> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c01b2-105">範例</span><span class="sxs-lookup"><span data-stu-id="c01b2-105">Example</span></span>  
 [!code-csharp[FromAsync#08](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#08)]
 [!code-vb[FromAsync#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="c01b2-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c01b2-106">See also</span></span>

- [<span data-ttu-id="c01b2-107">TPL 和傳統 .NET Framework 非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="c01b2-107">TPL and Traditional .NET Framework Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)
