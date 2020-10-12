---
title: NETSDK1073：無法辨識 FrameworkReference
description: 如何解決找不到 FrameworkReference 的問題。
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1073
ms.openlocfilehash: 59b5f63dcfe0115feabc2d87d24a09c6a650cc62
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2020
ms.locfileid: "91957137"
---
# <a name="netsdk1073-the-frameworkreference-was-not-recognized"></a><span data-ttu-id="250a0-103">NETSDK1073：無法辨識 FrameworkReference</span><span class="sxs-lookup"><span data-stu-id="250a0-103">NETSDK1073: The FrameworkReference was not recognized</span></span>

<span data-ttu-id="250a0-104">本文**適用于：** ✔️ .NET 2.1.100 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="250a0-104">**This article applies to:** ✔️ .NET 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="250a0-105">此錯誤通常表示 SDK 找不到特定的 FrameworkReference 版本。</span><span class="sxs-lookup"><span data-stu-id="250a0-105">This error typically means there is a version of a particular FrameworkReference that the SDK cannot find.</span></span> <span data-ttu-id="250a0-106">請嘗試刪除您的 *obj* 和 *bin* 資料夾並執行， `dotnet restore` 以重新下載最新的目標套件。</span><span class="sxs-lookup"><span data-stu-id="250a0-106">Try deleting your *obj* and *bin* folders and running `dotnet restore` to redownload the latest targeting packs.</span></span>

<span data-ttu-id="250a0-107">或者，您的安裝可能有問題，因此請確定您是使用最新版本的 .NET 並 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="250a0-107">Alternatively, there could be an issue with your install, so ensure you're on the latest versions of .NET and Visual Studio</span></span>
