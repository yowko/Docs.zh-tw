---
ms.openlocfilehash: 975edd1bda507b46da353db788d9730560f9b573
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "65632124"
---
> [!NOTE]
> 從 .NET Core 2.0 SDK 開始，您不必[`dotnet restore`](~/docs/core/tools/dotnet-restore.md)運行，因為它由需要還原的所有命令（如`dotnet new`）`dotnet build`和`dotnet run`進行隱式運行。
> 它在執行明確還原有意義的某些情況下仍然是有效的命令，例如 [Azure DevOps Services 中的持續整合組建](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core)，或在需要明確控制還原進行時間的建置系統中。
