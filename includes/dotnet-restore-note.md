---
ms.openlocfilehash: f22ee4accf9ff00814fa540adce4b9ecc6686da4
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537728"
---
<span data-ttu-id="484f8-101">您不必執行， [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) 因為它是由所有需要進行還原的命令（例如 `dotnet new` 、 `dotnet build` 、 `dotnet run` 、、 `dotnet test` `dotnet publish` 和 `dotnet pack` ）隱含地執行。</span><span class="sxs-lookup"><span data-stu-id="484f8-101">You don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet new`, `dotnet build`, `dotnet run`, `dotnet test`, `dotnet publish`, and `dotnet pack`.</span></span> <span data-ttu-id="484f8-102">若要停用隱含還原，請使用 `--no-restore` 選項。</span><span class="sxs-lookup"><span data-stu-id="484f8-102">To disable implicit restore, use the `--no-restore` option.</span></span>

<span data-ttu-id="484f8-103">在 `dotnet restore` 明確還原的特定情況下，此命令仍很有用，例如 [Azure DevOps Services 中的持續整合組建](/azure/devops/build-release/apps/aspnet/build-aspnet-core) ，或在需要明確控制還原進行時的組建系統。</span><span class="sxs-lookup"><span data-stu-id="484f8-103">The `dotnet restore` command is still useful in certain scenarios where explicitly restoring makes sense, such as [continuous integration builds in Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control when the restore occurs.</span></span>

<span data-ttu-id="484f8-104">如需有關如何管理 NuGet 摘要的詳細資訊，請參閱[ `dotnet restore` 檔](../docs/core/tools/dotnet-restore.md)。</span><span class="sxs-lookup"><span data-stu-id="484f8-104">For information about how to manage NuGet feeds, see the [`dotnet restore` documentation](../docs/core/tools/dotnet-restore.md).</span></span>
