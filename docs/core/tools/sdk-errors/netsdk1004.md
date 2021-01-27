---
title: NETSDK1004：找不到資產檔案
description: 瞭解在找不到檔案上的 project.assets.js時，所發生的 .NET SDK 錯誤 NETSDK1004。
ms.topic: error-reference
ms.date: 01/26/2021
f1_keywords:
- NETSDK1004
ms.openlocfilehash: ed42ad0e8ebef7362cc029125fe51d3f300acbae
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/27/2021
ms.locfileid: "98900355"
---
# <a name="netsdk1004-assets-file-not-found"></a><span data-ttu-id="96a56-103">NETSDK1004：找不到資產檔案</span><span class="sxs-lookup"><span data-stu-id="96a56-103">NETSDK1004: Assets file not found</span></span>

<span data-ttu-id="96a56-104">本文 **適用于：** ✔️ .net CORE 2.1.100 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="96a56-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="96a56-105">在組建期間找不到資產檔案 *project.assets.js* 時，就會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="96a56-105">This error occurs when the assets file *project.assets.json* is not found during build.</span></span> <span data-ttu-id="96a56-106">完整的錯誤訊息類似于：</span><span class="sxs-lookup"><span data-stu-id="96a56-106">The full error message is similar to:</span></span>

<span data-ttu-id="96a56-107">**NETSDK1004：找不到資產檔案「C:\IncorrectPath\project.assets.js開啟」。執行 NuGet 套件還原，以產生此檔案。**</span><span class="sxs-lookup"><span data-stu-id="96a56-107">**NETSDK1004: Assets file 'C:\IncorrectPath\project.assets.json' not found. Run a NuGet package restore to generate this file.**</span></span>

<span data-ttu-id="96a56-108">您可能會遇到警告 NETSDK1004 的其中一個原因是，您是 `dotnet build` 從包含字元的目錄路徑中執行命令 `%` 。</span><span class="sxs-lookup"><span data-stu-id="96a56-108">One reason you might encounter warning NETSDK1004 is if you run the `dotnet build` command from a directory path that contains a `%` character.</span></span>
