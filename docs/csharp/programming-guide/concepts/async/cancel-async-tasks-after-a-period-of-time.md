---
title: '在一段時間後取消非同步工作 (c # ) 」'
description: 瞭解如何排程取消任何未在一段時間內完成的相關聯工作。
ms.date: 08/19/2020
ms.topic: tutorial
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: ad9064f8f45a737982ffc35ab4ea2395ddae9016
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811414"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a><span data-ttu-id="2a4e9-103">在一段時間後取消非同步工作 (C#)</span><span class="sxs-lookup"><span data-stu-id="2a4e9-103">Cancel async tasks after a period of time (C#)</span></span>

<span data-ttu-id="2a4e9-104"><xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType>如果您不想要等候作業完成，您可以使用方法在一段時間後取消非同步作業。</span><span class="sxs-lookup"><span data-stu-id="2a4e9-104">You can cancel an asynchronous operation after a period of time by using the <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="2a4e9-105">這個方法會排程取消任何未在運算式所指定時間內完成的相關聯工作 `CancelAfter` 。</span><span class="sxs-lookup"><span data-stu-id="2a4e9-105">This method schedules the cancellation of any associated tasks that aren't complete within the period of time that's designated by the `CancelAfter` expression.</span></span>

<span data-ttu-id="2a4e9-106">這個範例會將 [工作清單 (c ) # ](cancel-an-async-task-or-a-list-of-tasks.md) 中所開發的程式碼加入至 [取消]，以下載網站清單並顯示每個網站的內容長度。</span><span class="sxs-lookup"><span data-stu-id="2a4e9-106">This example adds to the code that's developed in [Cancel a list of tasks (C#)](cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>

<span data-ttu-id="2a4e9-107">本教學課程涵蓋下列項目：</span><span class="sxs-lookup"><span data-stu-id="2a4e9-107">This tutorial covers:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="2a4e9-108">更新現有的 .NET 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="2a4e9-108">Updating an existing .NET console application</span></span>
> - <span data-ttu-id="2a4e9-109">排程取消</span><span class="sxs-lookup"><span data-stu-id="2a4e9-109">Scheduling a cancellation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2a4e9-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="2a4e9-110">Prerequisites</span></span>

<span data-ttu-id="2a4e9-111">本教學課程需要下列各項：</span><span class="sxs-lookup"><span data-stu-id="2a4e9-111">This tutorial requires the following:</span></span>

- <span data-ttu-id="2a4e9-112">您預期會在 [ [取消工作清單] (c # ) ](cancel-an-async-task-or-a-list-of-tasks.md) 教學課程中建立應用程式</span><span class="sxs-lookup"><span data-stu-id="2a4e9-112">You're expected to have created an application in the [Cancel a list of tasks (C#)](cancel-an-async-task-or-a-list-of-tasks.md) tutorial</span></span>
- [<span data-ttu-id="2a4e9-113">.NET 5.0 或更新版本的 SDK</span><span class="sxs-lookup"><span data-stu-id="2a4e9-113">.NET 5.0 or later SDK</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
- <span data-ttu-id="2a4e9-114">整合式開發環境 (IDE) </span><span class="sxs-lookup"><span data-stu-id="2a4e9-114">Integrated development environment (IDE)</span></span>
  - [<span data-ttu-id="2a4e9-115">建議 Visual Studio、Visual Studio Code 或 Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="2a4e9-115">We recommend Visual Studio, Visual Studio Code, or Visual Studio for Mac</span></span>](https://visualstudio.microsoft.com)

## <a name="update-application-entry-point"></a><span data-ttu-id="2a4e9-116">更新應用程式進入點</span><span class="sxs-lookup"><span data-stu-id="2a4e9-116">Update application entry point</span></span>

<span data-ttu-id="2a4e9-117">`Main`以下列內容取代現有的方法：</span><span class="sxs-lookup"><span data-stu-id="2a4e9-117">Replace the existing `Main` method with the following:</span></span>

```csharp
static async Task Main()
{
    Console.WriteLine("Application started.");

    try
    {
        s_cts.CancelAfter(3500);

        await SumPageSizesAsync();
    }
    catch (TaskCanceledException)
    {
        Console.WriteLine("\nTasks cancelled: timed out.\n");
    }

    Console.WriteLine("Application ending.");
}
```

<span data-ttu-id="2a4e9-118">更新的 `Main` 方法會將幾個教學訊息寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="2a4e9-118">The updated `Main` method writes a few instructional messages to the console.</span></span> <span data-ttu-id="2a4e9-119">在 [try catch](../../../language-reference/keywords/try-catch.md)內，呼叫以 <xref:System.Threading.CancellationTokenSource.CancelAfter(System.Int32)?displayProperty=nameWithType> 排程取消。</span><span class="sxs-lookup"><span data-stu-id="2a4e9-119">Within the [try catch](../../../language-reference/keywords/try-catch.md), a call to <xref:System.Threading.CancellationTokenSource.CancelAfter(System.Int32)?displayProperty=nameWithType> to schedule a cancellation.</span></span> <span data-ttu-id="2a4e9-120">這將會在一段時間後發出通知。</span><span class="sxs-lookup"><span data-stu-id="2a4e9-120">This will signal cancellation after a period of time.</span></span>

<span data-ttu-id="2a4e9-121">接下來， `SumPageSizesAsync` 會等待方法。</span><span class="sxs-lookup"><span data-stu-id="2a4e9-121">Next, the `SumPageSizesAsync` method is awaited.</span></span> <span data-ttu-id="2a4e9-122">如果處理所有 Url 的速度比排程取消更快，則應用程式會結束。</span><span class="sxs-lookup"><span data-stu-id="2a4e9-122">If processing all of the URLs occurs faster than the scheduled cancellation, the application ends.</span></span> <span data-ttu-id="2a4e9-123">但是，如果在處理所有 Url 之前觸發排程取消， <xref:System.Threading.Tasks.TaskCanceledException> 就會擲回。</span><span class="sxs-lookup"><span data-stu-id="2a4e9-123">However, if the scheduled cancellation is triggered before all of the URLs are processed, a <xref:System.Threading.Tasks.TaskCanceledException> is thrown.</span></span>

### <a name="example-application-output"></a><span data-ttu-id="2a4e9-124">範例應用程式輸出</span><span class="sxs-lookup"><span data-stu-id="2a4e9-124">Example application output</span></span>

```console
Application started.

https://docs.microsoft.com                                       37,357
https://docs.microsoft.com/aspnet/core                           85,589
https://docs.microsoft.com/azure                                398,939
https://docs.microsoft.com/azure/devops                          73,663

Tasks cancelled: timed out.

Application ending.
```

## <a name="complete-example"></a><span data-ttu-id="2a4e9-125">完整範例</span><span class="sxs-lookup"><span data-stu-id="2a4e9-125">Complete example</span></span>

<span data-ttu-id="2a4e9-126">下列程式碼是範例 *Program.cs* 檔的完整文字。</span><span class="sxs-lookup"><span data-stu-id="2a4e9-126">The following code is the complete text of the *Program.cs* file for the example.</span></span>

:::code language="csharp" source="snippets/cancel-tasks/cancel-task-after-period-of-time/Program.cs":::

## <a name="see-also"></a><span data-ttu-id="2a4e9-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a4e9-127">See also</span></span>

- <xref:System.Threading.CancellationToken>
- <xref:System.Threading.CancellationTokenSource>
- [<span data-ttu-id="2a4e9-128">使用 async 和 await 進行非同步程式設計 (c # ) </span><span class="sxs-lookup"><span data-stu-id="2a4e9-128">Asynchronous programming with async and await (C#)</span></span>](index.md)
- [<span data-ttu-id="2a4e9-129">取消 (c # ) 的工作清單 </span><span class="sxs-lookup"><span data-stu-id="2a4e9-129">Cancel a list of tasks (C#)</span></span>](cancel-an-async-task-or-a-list-of-tasks.md)
