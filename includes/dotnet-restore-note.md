---
ms.openlocfilehash: e140b375f4f289df895052aa093f03f381d62488
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102734"
---
[`dotnet restore`](~/docs/core/tools/dotnet-restore.md)不必運行`dotnet new`,因為它由需要還原的所有命令(如`dotnet build``dotnet run``dotnet test``dotnet publish`、、、、、`dotnet pack`和 ) 隱式運行。 要禁用隱式還原,請使用`--no-restore`選項。

該`dotnet restore`命令在某些顯式還原有意義的方案中仍然有用,例如[Azure DevOps 服務中的連續整合生成](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core)或需要顯式控制還原時建構系統的生成。

有關如何管理 NuGet 源的資訊,請參考[`dotnet restore`文件](../docs/core/tools/dotnet-restore.md)。
