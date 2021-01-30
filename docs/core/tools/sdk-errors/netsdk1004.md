---
title: NETSDK1004：找不到資產檔案
description: 瞭解在找不到檔案上的 project.assets.js時，所發生的 .NET SDK 錯誤 NETSDK1004。
ms.topic: error-reference
ms.date: 01/29/2021
f1_keywords:
- NETSDK1004
ms.openlocfilehash: 8416063fe318106cbcb4dbccacef3ecaaff5bba2
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216431"
---
# <a name="netsdk1004-assets-file-not-found"></a>NETSDK1004：找不到資產檔案

本文 **適用于：** ✔️ .net CORE 2.1.100 SDK 和更新版本

NuGet 會在 *obj* 資料夾中，將名為 *project.assets.js* 的檔案寫入，而 .net SDK 會使用它來取得封裝的相關資訊，以傳遞至編譯器。 在組建期間找不到資產檔案 *project.assets.js* 時，就會發生此錯誤。 完整的錯誤訊息與下列範例類似：

**NETSDK1004：找不到資產檔案「C:\path\to\project.assets.js開啟」。執行 NuGet 套件還原，以產生此檔案。**

以下是一些可能的錯誤原因：

* 您正在 `dotnet build` 從包含字元的目錄路徑中執行命令 `%` 。 若要解決此錯誤，請 `%` 從資料夾名稱中移除，然後重新執行 `dotnet build` 。
* 專案系統不會自動偵測並還原專案檔的變更。 若要解決此錯誤，請開啟命令提示字元，然後 `dotnet restore` 在專案上執行。
* 專案是由舊版 Nuget.exe 分開還原。 若要解決此錯誤，請開啟命令提示字元，然後 `dotnet restore` 在專案上執行。
* 先前的錯誤（例如 NETSDK1045 (您所使用的 SDK 版本不支援專案的目標 framework) ，因此無法建立專案資產檔案。 若要解決 NETSDK1004 錯誤，請解決先前的錯誤，然後 `dotnet restore` 在專案上執行。
* App Center CI 正在建立一個專案，而該專案具有不在 NuGet 中的外部元件。 若要解決此錯誤，請使用元件的 NuGet 套件。
