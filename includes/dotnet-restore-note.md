---
ms.openlocfilehash: e140b375f4f289df895052aa093f03f381d62488
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102734"
---
<span data-ttu-id="bc7f1-101">[`dotnet restore`](~/docs/core/tools/dotnet-restore.md)不必運行`dotnet new`,因為它由需要還原的所有命令(如`dotnet build``dotnet run``dotnet test``dotnet publish`、、、、、`dotnet pack`和 ) 隱式運行。</span><span class="sxs-lookup"><span data-stu-id="bc7f1-101">You don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet new`, `dotnet build`, `dotnet run`, `dotnet test`, `dotnet publish`, and `dotnet pack`.</span></span> <span data-ttu-id="bc7f1-102">要禁用隱式還原,請使用`--no-restore`選項。</span><span class="sxs-lookup"><span data-stu-id="bc7f1-102">To disable implicit restore, use the `--no-restore` option.</span></span>

<span data-ttu-id="bc7f1-103">該`dotnet restore`命令在某些顯式還原有意義的方案中仍然有用,例如[Azure DevOps 服務中的連續整合生成](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core)或需要顯式控制還原時建構系統的生成。</span><span class="sxs-lookup"><span data-stu-id="bc7f1-103">The `dotnet restore` command is still useful in certain scenarios where explicitly restoring makes sense, such as [continuous integration builds in Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control when the restore occurs.</span></span>

<span data-ttu-id="bc7f1-104">有關如何管理 NuGet 源的資訊,請參考[`dotnet restore`文件](../docs/core/tools/dotnet-restore.md)。</span><span class="sxs-lookup"><span data-stu-id="bc7f1-104">For information about how to manage NuGet feeds, see the [`dotnet restore` documentation](../docs/core/tools/dotnet-restore.md).</span></span>
