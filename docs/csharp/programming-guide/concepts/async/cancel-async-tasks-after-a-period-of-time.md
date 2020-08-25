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
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a>在一段時間後取消非同步工作 (C#)

<xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType>如果您不想要等候作業完成，您可以使用方法在一段時間後取消非同步作業。 這個方法會排程取消任何未在運算式所指定時間內完成的相關聯工作 `CancelAfter` 。

這個範例會將 [工作清單 (c ) # ](cancel-an-async-task-or-a-list-of-tasks.md) 中所開發的程式碼加入至 [取消]，以下載網站清單並顯示每個網站的內容長度。

本教學課程涵蓋下列項目：

> [!div class="checklist"]
>
> - 更新現有的 .NET 主控台應用程式
> - 排程取消

## <a name="prerequisites"></a>必要條件

本教學課程需要下列各項：

- 您預期會在 [ [取消工作清單] (c # ) ](cancel-an-async-task-or-a-list-of-tasks.md) 教學課程中建立應用程式
- [.NET 5.0 或更新版本的 SDK](https://dotnet.microsoft.com/download/dotnet/5.0)
- 整合式開發環境 (IDE) 
  - [建議 Visual Studio、Visual Studio Code 或 Visual Studio for Mac](https://visualstudio.microsoft.com)

## <a name="update-application-entry-point"></a>更新應用程式進入點

`Main`以下列內容取代現有的方法：

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

更新的 `Main` 方法會將幾個教學訊息寫入主控台。 在 [try catch](../../../language-reference/keywords/try-catch.md)內，呼叫以 <xref:System.Threading.CancellationTokenSource.CancelAfter(System.Int32)?displayProperty=nameWithType> 排程取消。 這將會在一段時間後發出通知。

接下來， `SumPageSizesAsync` 會等待方法。 如果處理所有 Url 的速度比排程取消更快，則應用程式會結束。 但是，如果在處理所有 Url 之前觸發排程取消， <xref:System.Threading.Tasks.TaskCanceledException> 就會擲回。

### <a name="example-application-output"></a>範例應用程式輸出

```console
Application started.

https://docs.microsoft.com                                       37,357
https://docs.microsoft.com/aspnet/core                           85,589
https://docs.microsoft.com/azure                                398,939
https://docs.microsoft.com/azure/devops                          73,663

Tasks cancelled: timed out.

Application ending.
```

## <a name="complete-example"></a>完整範例

下列程式碼是範例 *Program.cs* 檔的完整文字。

:::code language="csharp" source="snippets/cancel-tasks/cancel-task-after-period-of-time/Program.cs":::

## <a name="see-also"></a>另請參閱

- <xref:System.Threading.CancellationToken>
- <xref:System.Threading.CancellationTokenSource>
- [使用 async 和 await 進行非同步程式設計 (c # ) ](index.md)
- [取消 (c # ) 的工作清單 ](cancel-an-async-task-or-a-list-of-tasks.md)
