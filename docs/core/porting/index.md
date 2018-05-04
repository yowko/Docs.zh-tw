---
title: 從 .NET Framework 移轉到 .NET Core
description: 了解移植程序，並探索可協助將 .NET Framework 移植到 .NET Core 的工具。
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.openlocfilehash: bf4f50ca915f21cdda6b99ae6bdf9e837eca3ae7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="porting-to-net-core-from-net-framework"></a>從 .NET Framework 移轉到 .NET Core

如果已在 .NET Framework 上執行程式碼，您可能也想要在 .NET Core 1.0 執行程式碼。  本文章涵蓋移轉程序的概觀，以及移轉到 .NET Core 時可能覺得有用的工具清單。

## <a name="overview-of-the-porting-process"></a>移轉程序概觀

建議的移轉程序會遵循下列一系列步驟。  此程序的每個部分未來會在其他文章中進一步討論。

1. 識別及說明協力廠商相依性。

   這涉及了解程式協力廠商相依性是什麼、依賴它們的方式、查看它們是否也在 .NET Core 上執行的方式，以及不在 .NET Core 上執行時可以採取的步驟。
   
2. 將所有想要移轉到目標 .NET Framework 4.6.2 的專案重定為目標。

   這可確保當 .NET Core 無法支援特定 API 時，您可以使用 .NET Framework 特定目標的 API 替代方案。
   
3. 使用 [API 可攜性分析工具](https://github.com/Microsoft/dotnet-apiport/) 分析組件，並且根據結果開發移轉計劃。

   API 可攜性分析工具會分析已編譯的組件並產生報告，顯示高階的可攜性摘要，以及您使用但 .NET Core 不提供的每個 API 分析。  您可以使用此報告與程式碼基底分析，開發移轉程式碼的計劃。
   
4. 移轉測試程式碼。

   因為移轉到 .NET Core 對程式碼基底是巨變，所以強烈建議您移轉測試，以便在移轉程式碼時執行測試。  MSTest、xUnit 和 NUnit 都支援目前的 .NET Core 1.0。
   
6. 執行移轉計劃！

## <a name="tools-to-help"></a>協助工具

以下是您會發現有幫助的簡短工具清單︰

* NuGet - [NuGet 用戶端](https://dist.nuget.org/index.html)或 [NuGet 套件總管](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer)，適用於 .NET 實作的 Microsoft 封裝管理員。
* API 可攜性分析器：[命令列工具](https://github.com/Microsoft/dotnet-apiport/releases)或 [Visual Studio 擴充功能](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)，一種工具鏈，可以產生一份報表，說明程式碼在 .NET Framework 與 .NET Core 之間的可攜程度，以及逐一分析組件問題。  如需詳細資訊，請參閱 [Tooling to help you on the process](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/)。
* 反向封裝搜尋：[有用的 Web 服務](https://packagesearch.azurewebsites.net)，可讓您搜尋類型，以及尋找包含該類型的封裝。

## <a name="next-steps"></a>後續步驟

[分析協力廠商相依性。](third-party-deps.md)
   
