---
title: 用於移植到 .NET Core 的工具
description: 了解一些您可用來移植到 .NET Core 的工具
author: cartermp
ms.date: 05/03/2020
ms.openlocfilehash: b8678ec72fe5d910d5f8cff4768106e7496f9276
ms.sourcegitcommit: 1274a1a4a4c7e2eaf56b38da76ef7cec789726ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2020
ms.locfileid: "91406124"
---
# <a name="tools-to-help-with-porting-to-net-core"></a>協助移植到 .NET Core 的工具

本文所列的工具可協助您移植：

- [.Net 可攜性分析器](../../standard/analyzers/portability-analyzer.md) -此工具鏈可產生您的程式碼在 .NET FRAMEWORK 和 .net Core 之間的可攜性報告：
  - 作為 [命令列工具](https://github.com/Microsoft/dotnet-apiport/releases)
  - 做為[Visual Studio 擴充](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)功能
- [平臺相容性分析器](../../standard/analyzers/platform-compat-analyzer.md) -Roslyn 分析器，會在應用程式使用平臺特定 api 時，從可能無法使用 API 的呼叫位置通知開發人員。
- [.NET API 分析器](../../standard/analyzers/api-analyzer.md) -Roslyn 分析器，可協助偵測跨平臺應用程式和程式庫中的平臺相容性問題。
- [try-convert](https://www.nuget.org/packages/try-convert/) -可將專案或整個解決方案轉換成 .net SDK 的 .net Core 通用工具，包括將桌面應用程式移至 .net Core。 如果您已建立更複雜的組建 (例如自訂工作、目標或匯入) ，則不建議您這麼做，而且會拒絕許多與 .NET Core 不相容的專案類型。
