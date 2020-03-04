---
title: 用於移植到 .NET Core 的工具
description: 了解一些您可用來移植到 .NET Core 的工具
author: cartermp
ms.date: 12/07/2018
ms.openlocfilehash: 98b3a29f2287414b2cd323f1cbf2225905592b26
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157514"
---
# <a name="tools-to-help-with-porting-to-net-core"></a>協助移植到 .NET Core 的工具

本文所列的工具可協助您移植：

- [.Net 可攜性分析器](../../standard/analyzers/portability-analyzer.md)-一種工具鏈，可以產生一份報告，說明您的程式碼在 .NET FRAMEWORK 和 .net Core 之間的可攜程度：
  - 做為[命令列工具](https://github.com/Microsoft/dotnet-apiport/releases)
  - 做為[Visual Studio 擴充](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)功能
- [.NET API 分析器](../../standard/analyzers/api-analyzer.md)，這項 Roslyn 分析器可探索不同平台上 C# API 的潛在相容性風險，並偵測對已淘汰 API 的呼叫。

此外，您也可以嘗試使用 [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) 工具將較小的解決方案或個別專案移植到 .NET Core 專案檔案格式。

> [!WARNING]
> CsprojToVs2017 是第三方工具。 不保證它可搭配您的所有專案運作，而且它可能會導致您所依賴的行為發生些微變更。 CsprojToVs2017 應該當作將可自動化之基本事項自動化的「起點」使用。 它不是可以用來移轉專案檔格式保證解決方案。
