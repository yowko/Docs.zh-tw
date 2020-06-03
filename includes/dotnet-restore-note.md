---
ms.openlocfilehash: e140b375f4f289df895052aa093f03f381d62488
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102734"
---
您不需要執行 [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) ，因為它是由需要進行還原的所有命令隱含執行，例如 `dotnet new` 、 `dotnet build` 、 `dotnet run` 、 `dotnet test` 、 `dotnet publish` 和 `dotnet pack` 。 若要停用隱含還原，請使用 `--no-restore` 選項。

在 `dotnet restore` 明確還原的特定情況下，此命令仍然很有用，例如[Azure DevOps Services 中的持續整合組建](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core)，或在需要明確控制還原發生時機的組建系統中。

如需如何管理 NuGet 摘要的相關資訊，請參閱[ `dotnet restore` 檔](../docs/core/tools/dotnet-restore.md)集。
