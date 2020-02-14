---
title: 如何：將追蹤陳述式加入至應用程式程式碼
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tracing [.NET Framework], conditional writes based on switches
- trace statements
- WriteLineIf method
- tracing [.NET Framework], adding trace statements
- Assert method, tracing code
- trace switches, conditional writes based on switches
- WriteIf method
ms.assetid: f3a93fa7-1717-467d-aaff-393e5c9828b4
ms.openlocfilehash: 21df0e8129505e50e6b7f29c4f4f5aea94f380e3
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217473"
---
# <a name="how-to-add-trace-statements-to-application-code"></a><span data-ttu-id="52e80-102">如何：將追蹤陳述式加入至應用程式程式碼</span><span class="sxs-lookup"><span data-stu-id="52e80-102">How to: Add Trace Statements to Application Code</span></span>
<span data-ttu-id="52e80-103">追蹤最常使用的方法就是將輸出寫入接聽程式的方法：**Write**、**WriteIf**、**WriteLine**、**WriteLineIf**、**Assert** 和 **Fail**。</span><span class="sxs-lookup"><span data-stu-id="52e80-103">The methods used most often for tracing are the methods for writing output to listeners: **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**, and **Fail**.</span></span> <span data-ttu-id="52e80-104">這些方法可以分成兩種類別：**Write**、**WriteLine** 與 **Fail** 都會無條件地發出輸出，而 **WriteIf**、**WriteLineIf** 與 **Assert** 則會測試布林條件，並根據條件的值寫入或不寫入。</span><span class="sxs-lookup"><span data-stu-id="52e80-104">These methods can be divided into two categories: **Write**, **WriteLine**, and **Fail** all emit output unconditionally, whereas **WriteIf**, **WriteLineIf**, and **Assert** test a Boolean condition, and write or do not write based on the value of the condition.</span></span> <span data-ttu-id="52e80-105">如果條件為 **，** WriteIf**與**WriteLineIf`true` 會發出輸出，而如果條件為 **，則** Assert`false` 會發出輸出。</span><span class="sxs-lookup"><span data-stu-id="52e80-105">**WriteIf** and **WriteLineIf** emit output if the condition is `true`, and **Assert** emits output if the condition is `false`.</span></span>  
  
 <span data-ttu-id="52e80-106">設計追蹤和偵錯策略時，應該思考該輸出的內容為何。</span><span class="sxs-lookup"><span data-stu-id="52e80-106">When designing your tracing and debugging strategy, you should think about how you want the output to look.</span></span> <span data-ttu-id="52e80-107">若在多個 **Write** 陳述式中填入不相關的資訊，將會建立一個不易閱讀的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="52e80-107">Multiple **Write** statements filled with unrelated information will create a log that is difficult to read.</span></span> <span data-ttu-id="52e80-108">相反地，若使用 **WriteLine** 將相關的陳述式置於不同行，可能難以區別哪些資訊有所關聯。</span><span class="sxs-lookup"><span data-stu-id="52e80-108">On the other hand, using **WriteLine** to put related statements on separate lines may make it difficult to distinguish what information belongs together.</span></span> <span data-ttu-id="52e80-109">一般而言，當您想要將多個來源的資訊結合成單一的告知性訊息時，請使用多個 **Write** 陳述式，而當您想要建立單一且完整的訊息時，則請使用 **WriteLine** 陳述式。</span><span class="sxs-lookup"><span data-stu-id="52e80-109">In general, use multiple **Write** statements when you want to combine information from multiple sources to create a single informative message, and use the **WriteLine** statement when you want to create a single, complete message.</span></span>  
  
### <a name="to-write-a-complete-line"></a><span data-ttu-id="52e80-110">若要撰寫完整行</span><span class="sxs-lookup"><span data-stu-id="52e80-110">To write a complete line</span></span>  
  
1. <span data-ttu-id="52e80-111">呼叫 <xref:System.Diagnostics.Trace.WriteLine%2A> 或 <xref:System.Diagnostics.Trace.WriteLineIf%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="52e80-111">Call the <xref:System.Diagnostics.Trace.WriteLine%2A> or <xref:System.Diagnostics.Trace.WriteLineIf%2A> method.</span></span>  
  
     <span data-ttu-id="52e80-112">將歸位字元附加到此方法傳回的訊息結尾，讓由 **Write**、**WriteIf**、**WriteLine** 或 **WriteLineIf** 傳回的下一個訊息，從下行開始：</span><span class="sxs-lookup"><span data-stu-id="52e80-112">A carriage return is appended to the end of the message this method returns, so that the next message returned by **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the following line:</span></span>  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteLine("Error in AppendData procedure.")  
    Trace.WriteLineIf(errorFlag, "Error in AppendData procedure.")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteLine ("Error in AppendData procedure.");  
    System.Diagnostics.Trace.WriteLineIf(errorFlag,   
       "Error in AppendData procedure.");  
    ```  
  
### <a name="to-write-a-partial-line"></a><span data-ttu-id="52e80-113">若要寫入部分行</span><span class="sxs-lookup"><span data-stu-id="52e80-113">To write a partial line</span></span>  
  
1. <span data-ttu-id="52e80-114">呼叫 <xref:System.Diagnostics.Trace.Write%2A> 或 <xref:System.Diagnostics.Trace.WriteIf%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="52e80-114">Call the <xref:System.Diagnostics.Trace.Write%2A> or <xref:System.Diagnostics.Trace.WriteIf%2A> method.</span></span>  
  
     <span data-ttu-id="52e80-115">由 **Write**、**WriteIf**、**WriteLine** 或 **WriteLineIf** 放出的下一個訊息，將會以 **Write** 或 **WriteIf** 陳述式所放出訊息的相同行開始：</span><span class="sxs-lookup"><span data-stu-id="52e80-115">The next message put out by a **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the same line as the message put out by the **Write** or **WriteIf** statement:</span></span>  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteIf(errorFlag, "Error in AppendData procedure.")  
    Debug.WriteIf(errorFlag, "Transaction abandoned.")  
    Trace.Write("Invalid value for data request")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteIf(errorFlag,   
       "Error in AppendData procedure.");  
    System.Diagnostics.Debug.WriteIf(errorFlag, "Transaction abandoned.");  
    Trace.Write("Invalid value for data request");  
    ```  
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a><span data-ttu-id="52e80-116">若要確認特定條件存在 (不論在執行方法之前或之後)</span><span class="sxs-lookup"><span data-stu-id="52e80-116">To verify that certain conditions exist either before or after you execute a method</span></span>  
  
1. <span data-ttu-id="52e80-117">呼叫 <xref:System.Diagnostics.Trace.Assert%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="52e80-117">Call the <xref:System.Diagnostics.Trace.Assert%2A> method.</span></span>  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="52e80-118">追蹤和偵錯時都可以使用 **Assert**。</span><span class="sxs-lookup"><span data-stu-id="52e80-118">You can use **Assert** with both tracing and debugging.</span></span> <span data-ttu-id="52e80-119">此範例會將呼叫堆疊輸出到任何 **Listeners** 集合中的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="52e80-119">This example outputs the call stack to any listener in the **Listeners** collection.</span></span> <span data-ttu-id="52e80-120">如需詳細資訊，請參閱 [Managed 程式碼中的判斷提示](/visualstudio/debugger/assertions-in-managed-code)以及 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="52e80-120">For more information, see [Assertions in Managed Code](/visualstudio/debugger/assertions-in-managed-code) and <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52e80-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52e80-121">See also</span></span>

- <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>
- [<span data-ttu-id="52e80-122">追蹤和檢測應用程式</span><span class="sxs-lookup"><span data-stu-id="52e80-122">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="52e80-123">如何：建立、初始化和設定追蹤參數</span><span class="sxs-lookup"><span data-stu-id="52e80-123">How to: Create, Initialize and Configure Trace Switches</span></span>](how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="52e80-124">追蹤參數</span><span class="sxs-lookup"><span data-stu-id="52e80-124">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="52e80-125">追蹤接聽程式</span><span class="sxs-lookup"><span data-stu-id="52e80-125">Trace Listeners</span></span>](trace-listeners.md)
