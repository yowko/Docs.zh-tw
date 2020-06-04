---
title: 作法：寫入記錄檔訊息
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, writing log messages
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
ms.openlocfilehash: 28c5fe77e2711dfcac96e621a90fb9506eb74775
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410045"
---
# <a name="how-to-write-log-messages-visual-basic"></a><span data-ttu-id="9ea2e-102">如何：寫入記錄訊息 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ea2e-102">How to: Write Log Messages (Visual Basic)</span></span>

<span data-ttu-id="9ea2e-103">您可以使用 `My.Application.Log` 和 `My.Log` 物件記錄應用程式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9ea2e-103">You can use the `My.Application.Log` and `My.Log` objects to log information about your application.</span></span> <span data-ttu-id="9ea2e-104">此範例示範如何使用 `My.Application.Log.WriteEntry` 方法寫入追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="9ea2e-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information.</span></span>

<span data-ttu-id="9ea2e-105">如需記錄例外狀況資訊，請使用 `My.Application.Log.WriteException` 方法；請參閱[如何：記錄例外狀況](how-to-log-exceptions.md)。</span><span class="sxs-lookup"><span data-stu-id="9ea2e-105">For logging exception information, use the `My.Application.Log.WriteException` method; see [How to: Log Exceptions](how-to-log-exceptions.md).</span></span>

## <a name="example"></a><span data-ttu-id="9ea2e-106">範例</span><span class="sxs-lookup"><span data-stu-id="9ea2e-106">Example</span></span>

<span data-ttu-id="9ea2e-107">此範例使用 `My.Application.Log.WriteEntry` 方法以寫出追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="9ea2e-107">This example uses the `My.Application.Log.WriteEntry` method to write out the trace information.</span></span>

[!code-vb[VbVbalrMyApplicationLog#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#11)]

## <a name="net-framework-security"></a><span data-ttu-id="9ea2e-108">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="9ea2e-108">.NET Framework Security</span></span>

<span data-ttu-id="9ea2e-109">請確定您寫入記錄檔的資料不包含機密資訊，例如使用者密碼。</span><span class="sxs-lookup"><span data-stu-id="9ea2e-109">Make sure the data you write to the log does not include sensitive information such as user passwords.</span></span> <span data-ttu-id="9ea2e-110">如需詳細資訊，請參閱[使用應用程式記錄檔](working-with-application-logs.md)。</span><span class="sxs-lookup"><span data-stu-id="9ea2e-110">For more information, see [Working with Application Logs](working-with-application-logs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9ea2e-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ea2e-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="9ea2e-112">使用應用程式記錄檔</span><span class="sxs-lookup"><span data-stu-id="9ea2e-112">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="9ea2e-113">作法：記錄例外狀況</span><span class="sxs-lookup"><span data-stu-id="9ea2e-113">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)
- [<span data-ttu-id="9ea2e-114">逐步解說：判斷 My.Application.Log 寫入資訊的位置</span><span class="sxs-lookup"><span data-stu-id="9ea2e-114">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="9ea2e-115">逐步解說：變更 My.Application.Log 寫入資訊的位置</span><span class="sxs-lookup"><span data-stu-id="9ea2e-115">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="9ea2e-116">逐步解說：篩選 My.Application.Log 輸出</span><span class="sxs-lookup"><span data-stu-id="9ea2e-116">Walkthrough: Filtering My.Application.Log Output</span></span>](walkthrough-filtering-my-application-log-output.md)
