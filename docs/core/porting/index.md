---
title: 從 .NET Framework 到 .NET Core 的埠
description: 了解移植程序，並探索可協助將 .NET Framework 移植到 .NET Core 的工具。
author: cartermp
ms.date: 10/22/2019
ms.custom: seodec18
ms.openlocfilehash: 89f00e5c6ce7f3cea7a3135c9b2856c54a70da40
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73038523"
---
# <a name="overview-of-the-porting-process-from-net-framework-to-net-core"></a>從 .NET Framework 到 .NET Core 的移植程式總覽

您的程式碼可能目前是在您想要移植到 .NET Core 的 .NET Framework 上執行。 本文提供：

* 移植程式的總覽。
* 當您將程式碼移植到 .NET Core 時，您可能會覺得有用的工具清單。

## <a name="overview-of-the-porting-process"></a>移轉程序概觀

將您的專案移植到 .NET Core 時，建議您使用下列進程：

1. 將所有想要移轉到目標 .NET Framework 4.7.2 或更新版本的專案重定為目標。

   此步驟可確保當 .NET Core 無法支援特定 API 時，您可以使用 .NET Framework 特定目標的 API 替代方案。

2. 使用[.net 可攜性分析器](../../standard/analyzers/portability-analyzer.md)來分析您的元件，並查看它們是否可移植到 .net Core。

   API 可攜性分析器工具會分析已編譯的元件，並產生報表。 此報告會顯示高階的可攜性摘要，以及您所使用的每個 API 在 NET Core 上無法取得的明細。

3. 將[.NET API 分析器](../../standard/analyzers/api-analyzer.md)安裝到您的專案，以識別在某些平臺上擲回 <xref:System.PlatformNotSupportedException> 的 api，以及一些其他潛在的相容性問題。

   這項工具與可攜性分析器類似，但不會分析是否可以在 .NET Core 上建立，而是會分析您是否以在執行時間擲回 <xref:System.PlatformNotSupportedException> 的方式來使用 API。 雖然這在您從 .NET Framework 4.7.2 或更高版本中移動時並不常見，但仍可進行檢查。

4. 使用[Visual Studio 中的轉換工具](/nuget/consume-packages/migrate-packages-config-to-package-reference)，將所有 `packages.config` 相依性轉換為[PackageReference](/nuget/consume-packages/package-references-in-project-files)格式。

   此步驟牽涉到從舊版 `packages.config` 格式轉換相依性。 `packages.config` 無法在 .NET Core 上執行，因此如果您有封裝相依性，就需要進行這項轉換。

5. 為 .NET Core 建立新的專案，並複製原始程式檔，或嘗試使用工具轉換現有的專案檔。

   .NET Core 使用簡化的（和不同的）[專案檔案格式](../tools/csproj.md)，而不是 .NET Framework。 您必須將專案檔轉換成此格式才能繼續。

6. 移植您的測試程式碼。

   因為移轉到 .NET Core 對程式碼基底是巨變，所以強烈建議您移轉測試，以便在移轉您的程式碼時執行測試。 MSTest、xUnit 和 NUnit 全都適用于 .NET Core。

此外，您可以在單一作業中，使用 [[dotnet try-convert](https://github.com/dotnet/try-convert)] 工具，嘗試將較小的方案或個別專案移植到 .NET Core 專案檔案格式。 `dotnet try-convert` 不保證適用於您的所有專案，而且可能會導致您所依賴之行為發生細微變更。 它應該做為自動化可以自動化之基本事項的「起點」。 它不是可移轉專案的保證解決方案。

>[!div class="step-by-step"]
>[下一步](net-framework-tech-unavailable.md)
