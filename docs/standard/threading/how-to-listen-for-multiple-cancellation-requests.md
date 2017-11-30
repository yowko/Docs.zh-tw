---
title: "如何：接聽多個取消要求"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation tokens, joining
- LinkedTokenSource, how to
ms.assetid: 6f4f3804-2ed7-41b4-a97a-6e32b93f6e05
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 36cf338a15ad3f7d234f902c50a2dbb1b2e95847
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a><span data-ttu-id="b8655-102">如何：接聽多個取消要求</span><span class="sxs-lookup"><span data-stu-id="b8655-102">How to: Listen for Multiple Cancellation Requests</span></span>
<span data-ttu-id="b8655-103">這個範例示範如何取消語彙基元兩個同時接聽，讓您可以取消作業，如果 token，或是要求它。</span><span class="sxs-lookup"><span data-stu-id="b8655-103">This example shows how to listen to two cancellation tokens simultaneously so that you can cancel an operation if either token requests it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8655-104">啟用 [Just My Code] 時，Visual Studio 在某些情況下會在擲回例外狀況的字行上中斷，並顯示錯誤訊息，指出「使用者程式碼未處理例外狀況」。</span><span class="sxs-lookup"><span data-stu-id="b8655-104">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="b8655-105">這個錯誤是良性的。</span><span class="sxs-lookup"><span data-stu-id="b8655-105">This error is benign.</span></span> <span data-ttu-id="b8655-106">您可以按 F5 鍵繼續，並查看下面範例中示範的例外狀況處理行為。</span><span class="sxs-lookup"><span data-stu-id="b8655-106">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="b8655-107">若要防止 Visual Studio 的第一個錯誤的中斷，只要取消核取下的 [Just My Code] 核取方塊**工具、 選項、 偵錯、 一般**。</span><span class="sxs-lookup"><span data-stu-id="b8655-107">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8655-108">範例</span><span class="sxs-lookup"><span data-stu-id="b8655-108">Example</span></span>  
 <span data-ttu-id="b8655-109">在下列範例中，<xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A>方法用來將兩個權杖聯結到一個權杖。</span><span class="sxs-lookup"><span data-stu-id="b8655-109">In the following example, the <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> method is used to join two tokens into one token.</span></span> <span data-ttu-id="b8655-110">這可讓要傳遞給這些方法會採用一個取消語彙基元當做引數的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b8655-110">This enables the token to be passed to methods that take just one cancellation token as an argument.</span></span> <span data-ttu-id="b8655-111">此範例示範常見的案例中的方法必須觀察這兩個語彙基元從傳入外部類別，而產生的類別內的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b8655-111">The example demonstrates a common scenario in which a method must observe both a token passed in from outside the class, and a token generated inside the class.</span></span>  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 <span data-ttu-id="b8655-112">連結的語彙基元會擲回<xref:System.OperationCanceledException>，傳遞的例外狀況的語彙基元是連結的語彙基元，不是其中一個前置項語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b8655-112">When the linked token throws an <xref:System.OperationCanceledException>, the token that is passed to the exception is the linked token, not either of the predecessor tokens.</span></span> <span data-ttu-id="b8655-113">若要判斷哪一個語彙基元已取消，直接簽前置 token 的狀態。</span><span class="sxs-lookup"><span data-stu-id="b8655-113">To determine which of the tokens was canceled, check the status of the predecessor tokens directly.</span></span>  
  
 <span data-ttu-id="b8655-114">在此範例中，<xref:System.AggregateException>應該永遠不會擲回，但是它會攔截到這裡因為真實世界案例中以外的任何其他例外狀況<xref:System.OperationCanceledException>擲回的工作委派會包裝在<xref:System.OperationCanceledException>。</span><span class="sxs-lookup"><span data-stu-id="b8655-114">In this example, <xref:System.AggregateException> should never be thrown, but it is caught here because in real-world scenarios any other exceptions besides <xref:System.OperationCanceledException> that are thrown from the task delegate are wrapped in a <xref:System.OperationCanceledException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8655-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8655-115">See Also</span></span>  
 [<span data-ttu-id="b8655-116">Managed 執行緒中的取消作業</span><span class="sxs-lookup"><span data-stu-id="b8655-116">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
