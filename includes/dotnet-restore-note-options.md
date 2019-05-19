---
ms.openlocfilehash: 497ac09e5c9a10470d3ae1932d7e3dc114d121dd
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632000"
---
> [!NOTE]
> 從 .NET Core 2.0 開始，您不需要執行 [`dotnet restore`](~/docs/core/tools/dotnet-restore.md)，因為它是以隱含方式由需要進行還原的所有命令執行，例如 `dotnet build` 和 `dotnet run`。 它在執行明確還原有意義的某些情況下仍然是有效的命令，例如 [Azure DevOps Services 中的持續整合組建](/azure/devops/build-release/apps/aspnet/build-aspnet-core)，或在需要明確控制還原進行時間的建置系統中。
>
> 此命令也支援以完整形式傳入的 `dotnet restore` 選項 (例如 `--source`)。 不支援簡短形式選項，例如 `-s`。
