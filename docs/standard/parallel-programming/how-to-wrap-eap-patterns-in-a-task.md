---
title: 作法：將 EAP 模式包裝在工作中
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to wrap EAP patterns
ms.assetid: f11ed467-af2f-4504-8a2e-299a6c36d44e
ms.openlocfilehash: 339544ce9f0ee44097d1a60e0d2c2035d81f674d
ms.sourcegitcommit: 6d09ae36acba0b0e2ba47999f8f1a725795462a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2020
ms.locfileid: "92925359"
---
# <a name="how-to-wrap-eap-patterns-in-a-task"></a><span data-ttu-id="ddb6d-102">作法：將 EAP 模式包裝在工作中</span><span class="sxs-lookup"><span data-stu-id="ddb6d-102">How to: Wrap EAP Patterns in a Task</span></span>
<span data-ttu-id="ddb6d-103">下列範例將示範如何使用 <xref:System.Threading.Tasks.TaskCompletionSource%601>，將事件式非同步模式 (EAP) 的任意序列公開為單一工作。</span><span class="sxs-lookup"><span data-stu-id="ddb6d-103">The following example shows how to expose an arbitrary sequence of Event-Based Asynchronous Pattern (EAP) operations as one task by using a <xref:System.Threading.Tasks.TaskCompletionSource%601>.</span></span> <span data-ttu-id="ddb6d-104">此範例也示範如何使用 <xref:System.Threading.CancellationToken> 在 <xref:System.Net.WebClient> 物件上叫用內建的取消方法。</span><span class="sxs-lookup"><span data-stu-id="ddb6d-104">The example also shows how to use a <xref:System.Threading.CancellationToken> to invoke the built-in cancellation methods on the <xref:System.Net.WebClient> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddb6d-105">範例</span><span class="sxs-lookup"><span data-stu-id="ddb6d-105">Example</span></span>  
 [!code-csharp[FromAsync#08](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#08)]
 [!code-vb[FromAsync#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="ddb6d-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ddb6d-106">See also</span></span>

- [<span data-ttu-id="ddb6d-107">TPL 和傳統 .NET 非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="ddb6d-107">TPL and Traditional .NET Asynchronous Programming</span></span>](tpl-and-traditional-async-programming.md)
