---
title: 用於移植到 .NET Core 的工具
description: 了解一些您可用來移植到 .NET Core 的工具
author: cartermp
ms.author: mairaw
ms.date: 12/07/2018
ms.openlocfilehash: 88e3edb0442b3326a77323fe4b6396f3eb1ca767
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55904870"
---
# <a name="tools-to-help-with-porting-to-net-core"></a><span data-ttu-id="63616-103">協助移植到 .NET Core 的工具</span><span class="sxs-lookup"><span data-stu-id="63616-103">Tools to help with porting to .NET Core</span></span>

<span data-ttu-id="63616-104">本文所列的工具可協助您移植：</span><span class="sxs-lookup"><span data-stu-id="63616-104">You may find the tools listed in this article helpful when porting:</span></span>

* <span data-ttu-id="63616-105">[.NET 可移植性分析器](../../standard/analyzers/portability-analyzer.md)，此工具鏈可產生報告，說明您程式碼可在 .NET Framework 及 .NET Core 間移植的程度：形式有：[命令列工具](https://github.com/Microsoft/dotnet-apiport/releases)、[Visual Studio 延伸模組](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)</span><span class="sxs-lookup"><span data-stu-id="63616-105">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md), a toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core:  As a [command line tool](https://github.com/Microsoft/dotnet-apiport/releases) As a [Visual Studio Extension](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)</span></span>
* <span data-ttu-id="63616-106">[.NET API 分析器](../../standard/analyzers/api-analyzer.md)，這項 Roslyn 分析器可探索不同平台上 C# API 的潛在相容性風險，並偵測對已淘汰 API 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="63616-106">[.NET API analyzer](../../standard/analyzers/api-analyzer.md) - A Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span>

<span data-ttu-id="63616-107">此外，您也可以嘗試使用 [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) 工具將較小的解決方案或個別專案移植到 .NET Core 專案檔案格式。</span><span class="sxs-lookup"><span data-stu-id="63616-107">Additionally, you can attempt to port smaller solutions or individual projects to the .NET Core project file format with the [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) tool.</span></span>

> [!WARNING] 
> <span data-ttu-id="63616-108">CsprojToVs2017 是第三方工具。</span><span class="sxs-lookup"><span data-stu-id="63616-108">CsprojToVs2017 is a third-party tool.</span></span> <span data-ttu-id="63616-109">不保證它可搭配您的所有專案運作，而且它可能會導致您所依賴的行為發生些微變更。</span><span class="sxs-lookup"><span data-stu-id="63616-109">There is no guarantee that it will work for all of your projects, and it may cause subtle changes in behavior that you depend on.</span></span> <span data-ttu-id="63616-110">CsprojToVs2017 應該當作將可自動化之基本事項自動化的「起點」使用。</span><span class="sxs-lookup"><span data-stu-id="63616-110">CsprojToVs2017 should be used as a _starting point_ that automates the basic things that can be automated.</span></span> <span data-ttu-id="63616-111">它不是可以用來移轉專案檔格式保證解決方案。</span><span class="sxs-lookup"><span data-stu-id="63616-111">It is not a guaranteed solution to migrating project file formats.</span></span>