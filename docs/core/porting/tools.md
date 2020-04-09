---
title: 用於移植到 .NET Core 的工具
description: 了解一些您可用來移植到 .NET Core 的工具
author: cartermp
ms.date: 12/07/2018
ms.openlocfilehash: 64bad7600d8e17ada83d4bd8bc56762fd1789f43
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989125"
---
# <a name="tools-to-help-with-porting-to-net-core"></a><span data-ttu-id="329f4-103">協助移植到 .NET Core 的工具</span><span class="sxs-lookup"><span data-stu-id="329f4-103">Tools to help with porting to .NET Core</span></span>

<span data-ttu-id="329f4-104">本文所列的工具可協助您移植：</span><span class="sxs-lookup"><span data-stu-id="329f4-104">You may find the tools listed in this article helpful when porting:</span></span>

- <span data-ttu-id="329f4-105">[.NET 可移植性分析器](../../standard/analyzers/portability-analyzer.md)- 一個工具鏈,可以生成代碼在 .NET 框架和 .NET Core 之間的可移植性的報告:</span><span class="sxs-lookup"><span data-stu-id="329f4-105">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) - A toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core:</span></span>
  - <span data-ttu-id="329f4-106">為[命令列工具](https://github.com/Microsoft/dotnet-apiport/releases)</span><span class="sxs-lookup"><span data-stu-id="329f4-106">As a [command-line tool](https://github.com/Microsoft/dotnet-apiport/releases)</span></span>
  - <span data-ttu-id="329f4-107">作為[視覺工作室擴展](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)</span><span class="sxs-lookup"><span data-stu-id="329f4-107">As a [Visual Studio extension](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)</span></span>
- <span data-ttu-id="329f4-108">[.NET API 分析器](../../standard/analyzers/api-analyzer.md)，這項 Roslyn 分析器可探索不同平台上 C# API 的潛在相容性風險，並偵測對已淘汰 API 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="329f4-108">[.NET API analyzer](../../standard/analyzers/api-analyzer.md) - A Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span>

<span data-ttu-id="329f4-109">此外，您也可以嘗試使用 [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) 工具將較小的解決方案或個別專案移植到 .NET Core 專案檔案格式。</span><span class="sxs-lookup"><span data-stu-id="329f4-109">Additionally, you can attempt to port smaller solutions or individual projects to the .NET Core project file format with the [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) tool.</span></span>

> [!WARNING]
> <span data-ttu-id="329f4-110">CsprojToVs2017 是第三方工具。</span><span class="sxs-lookup"><span data-stu-id="329f4-110">CsprojToVs2017 is a third-party tool.</span></span> <span data-ttu-id="329f4-111">不保證它可搭配您的所有專案運作，而且它可能會導致您所依賴的行為發生些微變更。</span><span class="sxs-lookup"><span data-stu-id="329f4-111">There is no guarantee that it will work for all of your projects, and it may cause subtle changes in behavior that you depend on.</span></span> <span data-ttu-id="329f4-112">CsprojToVs2017 應該當作將可自動化之基本事項自動化的「起點」__ 使用。</span><span class="sxs-lookup"><span data-stu-id="329f4-112">CsprojToVs2017 should be used as a _starting point_ that automates the basic things that can be automated.</span></span> <span data-ttu-id="329f4-113">它不是可以用來移轉專案檔格式保證解決方案。</span><span class="sxs-lookup"><span data-stu-id="329f4-113">It is not a guaranteed solution to migrating project file formats.</span></span>
