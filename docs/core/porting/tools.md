---
title: 用於移植到 .NET Core 的工具
description: 了解一些您可用來移植到 .NET Core 的工具
author: cartermp
ms.date: 05/03/2020
ms.openlocfilehash: d0cf0abf206950beb34556ca3ba7243d8cad241e
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795582"
---
# <a name="tools-to-help-with-porting-to-net-core"></a>協助移植到 .NET Core 的工具

本文所列的工具可協助您移植：

- [.Net 可攜性分析器](../../standard/analyzers/portability-analyzer.md)-一種工具鏈，可以產生一份報告，說明您的程式碼在 .NET FRAMEWORK 和 .net Core 之間的可攜程度：
  - 做為[命令列工具](https://github.com/Microsoft/dotnet-apiport/releases)
  - 做為[Visual Studio 擴充](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)功能
- [.NET API 分析器](../../standard/analyzers/api-analyzer.md)，這項 Roslyn 分析器可探索不同平台上 C# API 的潛在相容性風險，並偵測對已淘汰 API 的呼叫。
- [try-convert](https://www.nuget.org/packages/try-convert/) -一種可將專案或整個解決方案轉換成 .net SDK 的 .net Core 通用工具，包括將桌面應用程式移至 .net Core。 如果您已建立更複雜的組建（例如自訂工作、目標或匯入），而且它會拒絕許多與 .NET Core 不相容的專案類型，則不建議使用此選項。
