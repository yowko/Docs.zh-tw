---
title: 從 .NET 框架到 .NET 核心的埠
description: 了解移植程序，並探索可協助將 .NET Framework 移植到 .NET Core 的工具。
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: e483bb6e48dad6c3bf71bfa81e704a137fc02094
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "75937331"
---
# <a name="overview-of-porting-from-net-framework-to-net-core"></a>從 .NET 框架移植到 .NET 核心的概述

您可能有當前在 .NET 框架上運行的代碼，您有興趣移植到 .NET Core。 本文提供：

* 移植過程概述。
* 在將代碼移植到 .NET Core 時，您可能會發現有用的工具清單。

## <a name="overview-of-the-porting-process"></a>移轉程序概觀

我們建議您在將專案移植到 .NET Core 時使用以下過程：

1. 將要移植的所有專案重新置放為目標 .NET 框架 4.7.2 或更高版本。

   此步驟可確保當 .NET Core 無法支援特定 API 時，您可以使用 .NET Framework 特定目標的 API 替代方案。

2. 使用[.NET 可攜性分析器](../../standard/analyzers/portability-analyzer.md)分析程式集，並查看它們是否可移植到 .NET Core。

   API 可攜性分析器工具分析已編譯的程式集並生成報告。 此報告顯示高級可攜性摘要以及您正在使用的每個 API 的明細，這些 API 在 NET Core 上不可用。

3. 將[.NET API 分析器](../../standard/analyzers/api-analyzer.md)安裝到專案中，以識別<xref:System.PlatformNotSupportedException>某些平臺上的 API 和其他一些潛在的相容性問題。

   此工具類似于可攜性分析器，但它不是分析代碼是否可以在 .NET Core 上構建，而是分析您是否以在運行時引發 A<xref:System.PlatformNotSupportedException>的方式使用 API。 儘管如果您要從 .NET 框架 4.7.2 或更高版本移動，這種情況並不常見，但最好檢查一下。 有關在 .NET Core 上引發異常的 API 的詳細資訊，請參閱[始終在 .NET Core 上引發異常的 API。](../compatibility/unsupported-apis.md)

4. 使用 Visual `packages.config` [Studio 中的轉換工具](/nuget/consume-packages/migrate-packages-config-to-package-reference)將所有依賴項轉換為[包參考](/nuget/consume-packages/package-references-in-project-files)格式。

   此步驟涉及從舊`packages.config`格式轉換依賴項。 `packages.config`在 .NET Core 上不起作用，因此如果您有包依賴項，則需要進行此轉換。

5. 為 .NET Core 創建新專案並複製原始檔案，或嘗試使用工具轉換現有專案檔案。

   .NET Core 使用比 .NET 框架簡化（和不同的）[專案檔案格式](../tools/csproj.md)。 您需要將專案檔案轉換為此格式才能繼續。

6. 移植測試代碼。

   由於移植到 .NET Core 是代碼庫的重大更改，因此強烈建議您移植測試專案，以便在移植代碼時運行測試。 MSTest、xUnit 和 NUnit 都在 .NET Core 上工作。

此外，您可以使用[dotnet try 轉換](https://github.com/dotnet/try-convert)工具嘗試將較小的解決方案或單個專案移植到 .NET Core 專案檔案格式。 `dotnet try-convert`不能保證適用于所有專案，並且可能會導致您所依賴的行為發生細微的變化。 使用它作為一個_起點_，自動執行可以自動化的基本內容。 它不是遷移專案的保證解決方案。

## <a name="next-steps"></a>後續步驟

>[!div class="nextstepaction"]
>[分析依賴項](third-party-deps.md)
