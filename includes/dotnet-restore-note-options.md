---
ms.openlocfilehash: 47811d3fab2e4fa531d383dfe818e3cac5613eb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72179970"
---
> [!NOTE]
> <span data-ttu-id="20b68-101">從 .NET Core 2.0 開始，您不必運行[`dotnet restore`](~/docs/core/tools/dotnet-restore.md)，因為它由需要還原的所有命令（如`dotnet build`和`dotnet run`） 隱式運行。</span><span class="sxs-lookup"><span data-stu-id="20b68-101">Starting with .NET Core 2.0, you don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet build` and `dotnet run`.</span></span> <span data-ttu-id="20b68-102">它在執行明確還原有意義的某些情況下仍然是有效的命令，例如 [Azure DevOps Services 中的持續整合組建](/azure/devops/build-release/apps/aspnet/build-aspnet-core)，或在需要明確控制還原進行時間的建置系統中。</span><span class="sxs-lookup"><span data-stu-id="20b68-102">It's still a valid command in certain scenarios where doing an explicit restore makes sense, such as [continuous integration builds in Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control the time at which the restore occurs.</span></span>
>
> <span data-ttu-id="20b68-103">此命令也支援以完整形式傳入的 `dotnet restore` 選項 (例如 `--source`)。</span><span class="sxs-lookup"><span data-stu-id="20b68-103">This command also supports the `dotnet restore` options when passed in the long form (for example, `--source`).</span></span> <span data-ttu-id="20b68-104">不支援簡短形式選項，例如 `-s`。</span><span class="sxs-lookup"><span data-stu-id="20b68-104">Short form options, such as `-s`, are not supported.</span></span>
