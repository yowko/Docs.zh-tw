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
# <a name="tools-to-help-with-porting-to-net-core"></a>協助移植到 .NET Core 的工具

本文所列的工具可協助您移植：

* [.NET 可移植性分析器](../../standard/analyzers/portability-analyzer.md)，此工具鏈可產生報告，說明您程式碼可在 .NET Framework 及 .NET Core 間移植的程度：形式有：[命令列工具](https://github.com/Microsoft/dotnet-apiport/releases)、[Visual Studio 延伸模組](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)
* [.NET API 分析器](../../standard/analyzers/api-analyzer.md)，這項 Roslyn 分析器可探索不同平台上 C# API 的潛在相容性風險，並偵測對已淘汰 API 的呼叫。

此外，您也可以嘗試使用 [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) 工具將較小的解決方案或個別專案移植到 .NET Core 專案檔案格式。

> [!WARNING] 
> CsprojToVs2017 是第三方工具。 不保證它可搭配您的所有專案運作，而且它可能會導致您所依賴的行為發生些微變更。 CsprojToVs2017 應該當作將可自動化之基本事項自動化的「起點」使用。 它不是可以用來移轉專案檔格式保證解決方案。