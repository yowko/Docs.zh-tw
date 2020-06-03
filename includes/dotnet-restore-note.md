---
ms.openlocfilehash: e140b375f4f289df895052aa093f03f381d62488
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102734"
---
<span data-ttu-id="44c44-101">您不需要執行 [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) ，因為它是由需要進行還原的所有命令隱含執行，例如 `dotnet new` 、 `dotnet build` 、 `dotnet run` 、 `dotnet test` 、 `dotnet publish` 和 `dotnet pack` 。</span><span class="sxs-lookup"><span data-stu-id="44c44-101">You don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet new`, `dotnet build`, `dotnet run`, `dotnet test`, `dotnet publish`, and `dotnet pack`.</span></span> <span data-ttu-id="44c44-102">若要停用隱含還原，請使用 `--no-restore` 選項。</span><span class="sxs-lookup"><span data-stu-id="44c44-102">To disable implicit restore, use the `--no-restore` option.</span></span>

<span data-ttu-id="44c44-103">在 `dotnet restore` 明確還原的特定情況下，此命令仍然很有用，例如[Azure DevOps Services 中的持續整合組建](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core)，或在需要明確控制還原發生時機的組建系統中。</span><span class="sxs-lookup"><span data-stu-id="44c44-103">The `dotnet restore` command is still useful in certain scenarios where explicitly restoring makes sense, such as [continuous integration builds in Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control when the restore occurs.</span></span>

<span data-ttu-id="44c44-104">如需如何管理 NuGet 摘要的相關資訊，請參閱[ `dotnet restore` 檔](../docs/core/tools/dotnet-restore.md)集。</span><span class="sxs-lookup"><span data-stu-id="44c44-104">For information about how to manage NuGet feeds, see the [`dotnet restore` documentation](../docs/core/tools/dotnet-restore.md).</span></span>
