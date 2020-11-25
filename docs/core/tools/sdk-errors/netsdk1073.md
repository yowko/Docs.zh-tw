---
title: NETSDK1073：無法辨識 FrameworkReference
description: 如何解決找不到 FrameworkReference 的問題。
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1073
ms.openlocfilehash: 2b2dbf2a0d3e13dca4fe634529b7951f2333ce28
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713024"
---
# <a name="netsdk1073-the-frameworkreference-was-not-recognized"></a><span data-ttu-id="f1d39-103">NETSDK1073：無法辨識 FrameworkReference</span><span class="sxs-lookup"><span data-stu-id="f1d39-103">NETSDK1073: The FrameworkReference was not recognized</span></span>

<span data-ttu-id="f1d39-104">本文 **適用于：** ✔️ .net CORE 2.1.100 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="f1d39-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="f1d39-105">此錯誤通常表示 SDK 找不到特定的 FrameworkReference 版本。</span><span class="sxs-lookup"><span data-stu-id="f1d39-105">This error typically means there is a version of a particular FrameworkReference that the SDK cannot find.</span></span> <span data-ttu-id="f1d39-106">請嘗試刪除您的 *obj* 和 *bin* 資料夾並執行， `dotnet restore` 以重新下載最新的目標套件。</span><span class="sxs-lookup"><span data-stu-id="f1d39-106">Try deleting your *obj* and *bin* folders and running `dotnet restore` to redownload the latest targeting packs.</span></span>

<span data-ttu-id="f1d39-107">或者，您的安裝可能有問題，因此請確定您是使用最新版本的 .NET 並 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f1d39-107">Alternatively, there could be an issue with your install, so ensure you're on the latest versions of .NET and Visual Studio</span></span>
