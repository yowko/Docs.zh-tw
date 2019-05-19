---
ms.openlocfilehash: 975edd1bda507b46da353db788d9730560f9b573
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632124"
---
> [!NOTE]
> 從 .NET Core 2.0 SDK 開始，您不需要執行 [`dotnet restore`](~/docs/core/tools/dotnet-restore.md)，因為所有需要進行還原的命令 (例如 `dotnet new`、`dotnet build` 和 `dotnet run`) 都會以隱含方式執行它。
> 它在執行明確還原有意義的某些情況下仍然是有效的命令，例如 [Azure DevOps Services 中的持續整合組建](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core)，或在需要明確控制還原進行時間的建置系統中。
