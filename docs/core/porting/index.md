---
title: 將程式碼從 .NET Framework 移植到 .NET Core
description: 了解移植程序，並探索可協助將 .NET Framework 移植到 .NET Core 的工具。
author: cartermp
ms.date: 07/03/2019
ms.custom: seodec18
ms.openlocfilehash: c408beb97290c41d2ab6944b9d1f68bbc5e946fb
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609240"
---
# <a name="port-your-code-from-net-framework-to-net-core"></a>將您的程式碼從 .NET Framework 移植到 .NET Core

如果您有在 .NET Framework 上執行的程式碼，您可能也想要在 .NET Core 上執行程式碼。 此處提供移轉程序的概觀，以及將您的程式碼移轉到 .NET Core 時可能覺得有用的工具清單。

## <a name="overview-of-the-porting-process"></a>移轉程序概觀

這是將您的程式碼移植到 .NET Core 的建議程序。 此程序的每個步驟未來會在其他文章中進一步討論。

1. 識別及說明協力廠商相依性。

   此步驟涉及了解程式協力廠商相依性是什麼、依賴它們的方式、查看它們是否也在 .NET Core 上執行的方式，以及不在 .NET Core 上執行時可以採取的步驟。 它涵蓋將您的相依性移轉到 .NET Core 中使用之 [PackageReference](/nuget/consume-packages/package-references-in-project-files) 格式的方式。

2. 將所有想要移轉到目標 .NET Framework 4.7.2 或更新版本的專案重定為目標。

   此步驟可確保當 .NET Core 無法支援特定 API 時，您可以使用 .NET Framework 特定目標的 API 替代方案。

3. 使用 [.NET 可攜性分析工具](../../standard/analyzers/portability-analyzer.md)來分析組件，並且根據結果開發移轉計劃。

   API 可攜性分析器工具可分析您的設定組件，並產生報告以顯示高階可攜性摘要與您使用但 .NET Core 不提供之每個 API 的明細。 您可以使用此報告與程式碼基底分析，開發移轉程式碼的計劃。

4. 移轉測試程式碼。

   因為移轉到 .NET Core 對程式碼基底是巨變，所以強烈建議您移轉測試，以便在移轉您的程式碼時執行測試。 MSTest、xUnit 與 NUnit 都支援 .NET Core。

5. 執行移轉計劃！

下列清單顯示您在移轉程序期間可能會發現有用的工具：

* .NET 可移植性分析器：[命令列工具](https://github.com/Microsoft/dotnet-apiport/releases)或 [Visual Studio 延伸模組](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)，一種可以產生報表的工具，說明程式碼在 .NET Framework 和目標 .NET Core 平台之間的可移植程度。 此報表包含目標 .NET Core 平台上所缺少的類型和 API 各組件細項。 如需詳細資訊，請參閱 [.NET 可攜性分析器](../../standard/analyzers/portability-analyzer.md)。 建議您在開始移植之前，先執行 .NET 可移植性分析器工具，原因是它會協助您找出所缺少 API 中的任何差異。
* .NET API 分析器：一種 Roslyn 分析器，可探索在某些平台上擲出 <xref:System.PlatformNotSupportedException> 的 .NET Standard API、偵測對已淘汰 API 的呼叫，以及探索不同平台上 C# API 的其他潛在相容性風險。 如需詳細資訊，請參閱 [.NET API 分析器](../../standard/analyzers/api-analyzer.md)。 在您已建立 .NET Core 專案後，此分析器有助於找出不同平台上的執行階段行為差異。
* 反向封裝搜尋：[有用的 Web 服務](https://packagesearch.azurewebsites.net)，可讓您搜尋類型，以及尋找包含該類型的封裝。

此外，您也可以嘗試使用 [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) 工具將較小的解決方案或個別專案移植到 .NET Core 專案檔案格式。

> [!WARNING]
> CsprojToVs2017 是第三方工具。 不保證它可搭配您的所有專案運作，而且它可能會導致您所依賴的行為發生些微變更。 CsprojToVs2017 應該當作將可自動化之基本事項自動化的「起點」  使用。 它不是可以用來移轉專案檔格式保證解決方案。

>[!div class="step-by-step"]
>[下一步](net-framework-tech-unavailable.md)
