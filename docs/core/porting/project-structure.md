---
title: 組織適用於.NET Framework 和.NET Core 的專案
description: 協助想要同時針對 .NET Framework 及 .NET Core 編譯解決方案的專案擁有者。
author: conniey
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 57bb766f1d91c502a508b6362dc642310009c8c4
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55904016"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a>組織專案以同時支援 .NET Framework 及 .NET Core

了解如何建立一個並行編譯 .NET Framework 和 .NET Core 的解決方案。 請參閱數個選項，以組織專案來協助開發人員達成此目標。 以下是當您決定如何使用 .NET Core 設定專案配置時，要考量的一些典型案例。 此清單不一定涵蓋您想要的所有項目，根據專案需求決定優先順序。

* [**將現有的專案和 .NET Core 專案合併成單一專案**](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  *適用於︰*
  * 藉由編譯單一專案而非編譯多個專案，每個都會以不同的 .NET Framework 版本或平台為目標，以簡化建置流程。
  * 因為您必須管理單一專案檔，所以簡化多目標專案的來源檔案管理。 新增/移除來源檔案時，替代方案需要您手動同步處理這些專案與其他專案。
  * 輕鬆產生 NuGet 封裝以供耗用。
  * 讓您使用編譯器指示詞，在程式庫中針對特定的 .NET Framework 版本撰寫程式碼。

  *不支援的情節：*
  * 需要開發人員使用 Visual Studio 2017 開啟現有的專案。 若要支援舊版的 Visual Studio，[將專案檔放在不同的資料夾](#support-vs)是較好的選擇。

* <a name="support-vs"></a>[**將現有的專案和新的 .NET Core 專案分開**](#keep-existing-projects-and-create-a-net-core-project)

  *適用於︰*
  * 繼續支援現有專案的開發，但不必升級可能沒有 Visual Studio 2017 的開發人員/參與者。
  * 減少現有專案中製造新Bug 的可能性，因為這些專案不需要任何程式碼變換。

## <a name="example"></a>範例

請考慮以下的儲存機制︰

![現有專案](media/project-structure/project.png)

[**Source Code**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/) (原始程式碼)

下列描述幾種方式以新增這個存放庫的 .NET Core 支援，視現有專案的條件約束和複雜性而定。

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a>使用多目標 .NET Core 專案取代現有的專案

重新組織存放庫，以便移除任何現有的 *\*.csproj* 檔案，並建立以多個架構為目標的單一 *\*.csproj* 檔案。 這是很不錯的選擇，因為單一專案能夠編譯不同的架構。 它也可以處理個別目標架構的不同編譯選項及相依性。

![建立以多個架構為目標的 csproj](media/project-structure/project.csproj.png)

[**Source Code**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/) (原始程式碼)

要注意的變更如下︰

* 以新的 [.NET Core *\*.csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj) 取代 *packages.config* 和 *\*.csproj*。 NuGet 套件是使用 `<PackageReference> ItemGroup` 所指定。

## <a name="keep-existing-projects-and-create-a-net-core-project"></a>保留現有的專案並建立 .NET Core 專案

如果現有的專案以較舊的架構為目標，您可能想要保持這些專案不變，使用 .NET Core 專案以未來的架構為目標。

![.NET Core 專案與現有專案位在不同的資料夾](media/project-structure/project.csproj.different.png)

[**Source Code**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/) (原始程式碼)

要注意的變更如下︰

* .NET Core 和現有的專案保存在不同的資料夾中。
  * 將專案放在不同的資料夾中，可避免強迫使用 Visual Studio 2017。 您可以建立不同的解決方案只開啟舊的專案。

## <a name="see-also"></a>另請參閱

如需移轉至 .NET Core 的詳細指導，請參閱 [.NET Core 移植文件](index.md)。
