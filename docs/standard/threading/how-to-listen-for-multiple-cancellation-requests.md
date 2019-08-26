---
title: 作法：接聽多個取消要求
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation tokens, joining
- LinkedTokenSource, how to
ms.assetid: 6f4f3804-2ed7-41b4-a97a-6e32b93f6e05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2684f0fd43f84573933fc0a7107ce4f9035bc092
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913311"
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a><span data-ttu-id="4d26d-102">作法：接聽多個取消要求</span><span class="sxs-lookup"><span data-stu-id="4d26d-102">How to: Listen for Multiple Cancellation Requests</span></span>
<span data-ttu-id="4d26d-103">此範例顯示如何同時接聽兩個取消權杖，讓您可以在其中一個權杖要求作業時將作業取消。</span><span class="sxs-lookup"><span data-stu-id="4d26d-103">This example shows how to listen to two cancellation tokens simultaneously so that you can cancel an operation if either token requests it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4d26d-104">啟用 [Just My Code] 時，Visual Studio 在某些情況下會在擲回例外狀況的字行上中斷，並顯示錯誤訊息，指出「使用者程式碼未處理例外狀況」。</span><span class="sxs-lookup"><span data-stu-id="4d26d-104">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="4d26d-105">這個錯誤是良性的。</span><span class="sxs-lookup"><span data-stu-id="4d26d-105">This error is benign.</span></span> <span data-ttu-id="4d26d-106">您可以按 F5 鍵繼續，並查看下面範例中示範的例外狀況處理行為。</span><span class="sxs-lookup"><span data-stu-id="4d26d-106">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="4d26d-107">若要防止 Visual Studio 在遇到第一個錯誤時就中斷，只要取消核取 [工具]、[選項]、[偵錯]、[一般]  下的 [Just My Code] 核取方塊即可。</span><span class="sxs-lookup"><span data-stu-id="4d26d-107">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d26d-108">範例</span><span class="sxs-lookup"><span data-stu-id="4d26d-108">Example</span></span>  
 <span data-ttu-id="4d26d-109">在下列範例中，<xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> 方法是用來將兩個權杖聯結為一個權杖。</span><span class="sxs-lookup"><span data-stu-id="4d26d-109">In the following example, the <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> method is used to join two tokens into one token.</span></span> <span data-ttu-id="4d26d-110">這可將權杖傳遞給僅採取一個取消權杖作為引數的方法。</span><span class="sxs-lookup"><span data-stu-id="4d26d-110">This enables the token to be passed to methods that take just one cancellation token as an argument.</span></span> <span data-ttu-id="4d26d-111">此範例示範一個常見的案例，其中方法必須同時觀察從類別外部傳入的權杖，以及類別內部產生的權杖。</span><span class="sxs-lookup"><span data-stu-id="4d26d-111">The example demonstrates a common scenario in which a method must observe both a token passed in from outside the class, and a token generated inside the class.</span></span>  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 <span data-ttu-id="4d26d-112">當連結的權杖擲回 <xref:System.OperationCanceledException> 時，傳遞給例外狀況的權杖是連結的權杖，而非其中一個前置項權杖。</span><span class="sxs-lookup"><span data-stu-id="4d26d-112">When the linked token throws an <xref:System.OperationCanceledException>, the token that is passed to the exception is the linked token, not either of the predecessor tokens.</span></span> <span data-ttu-id="4d26d-113">若要判斷哪一個權杖已取消，請直接檢查前置項權杖的狀態。</span><span class="sxs-lookup"><span data-stu-id="4d26d-113">To determine which of the tokens was canceled, check the status of the predecessor tokens directly.</span></span>  
  
 <span data-ttu-id="4d26d-114">在此範例中，應該永遠不會擲回 <xref:System.AggregateException>，但是卻在這裡攔截到它，是因為在真實案例中，<xref:System.OperationCanceledException> 以外從工作委派擲回的任何其他例外狀況，都會包裝在 <xref:System.AggregateException> 中。</span><span class="sxs-lookup"><span data-stu-id="4d26d-114">In this example, <xref:System.AggregateException> should never be thrown, but it is caught here because in real-world scenarios any other exceptions besides <xref:System.OperationCanceledException> that are thrown from the task delegate are wrapped in a <xref:System.AggregateException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d26d-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d26d-115">See also</span></span>

- [<span data-ttu-id="4d26d-116">Managed 執行緒中的取消作業</span><span class="sxs-lookup"><span data-stu-id="4d26d-116">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
