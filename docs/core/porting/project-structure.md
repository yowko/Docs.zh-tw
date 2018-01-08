---
title: "組織專案以支援 .NET Framework 及 .NET Core"
description: "協助想要同時針對 .NET Framework 及 .NET Core 編譯解決方案的專案擁有者。"
keywords: ".NET, .NET Core, .NET Framework, 專案配置, 多個架構"
author: conniey
ms.author: mairaw
ms.date: 04/06/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 3af62252-1dfa-4336-8d2f-5cfdb57d7724
ms.workload: dotnetcore
ms.openlocfilehash: 08fe18233c13410f0fb970020bce090d3345ca84
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="organizing-your-project-to-support-net-framework-and-net-core"></a>組織專案以支援 .NET Framework 及 .NET Core

本文可協助想要同時針對 .NET Framework 及 .NET Core 編譯解決方案的專案擁有者。 它提供數個選項，組織專案以協助開發人員達成此目標。 下列清單提供當您決定如何使用 .NET Core 設定專案配置時，要考量的一些典型案例。 此清單不一定涵蓋您想要的所有項目，根據專案需求決定優先順序。

* [**將現有的專案和 .NET Core 專案合併成單一專案**][option-csproj]

  *適用於︰*
  * 藉由編譯單一專案而非編譯多個專案，每個都會以不同的 .NET Framework 版本或平台為目標，以簡化建置流程。
  * 因為您必須管理單一專案檔，所以簡化多目標專案的來源檔案管理。 新增/移除來源檔案時，替代方案需要您手動同步處理這些專案與其他專案。
  * 輕鬆產生 NuGet 封裝以供耗用。
  * 讓您使用編譯器指示詞，在程式庫中針對特定的 .NET Framework 版本撰寫程式碼。

  *不支援的情節：*
  * 需要開發人員使用 Visual Studio 2017 開啟現有的專案。 若要支援舊版的 Visual Studio，[將專案檔放在不同的資料夾](#support-vs)是較好的選擇。

* <a name="support-vs"></a>[**將現有的專案和新的 .NET Core 專案分開**][option-csproj-folder]

  *適用於︰*
  * 繼續支援現有專案的開發，但不必升級可能沒有 Visual Studio 2017 的開發人員/參與者。
  * 減少現有專案中製造新Bug 的可能性，因為這些專案不需要任何程式碼變換。

## <a name="example"></a>範例

請考慮以下的儲存機制︰

![現有專案][example-initial-project]

[**原始程式碼**][example-initial-project-code]

下列描述幾種方式以新增這個存放庫的 .NET Core 支援，視現有專案的條件約束和複雜性而定。

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a>使用多目標 .NET Core 專案取代現有的專案

重新組織存放庫，以便移除任何現有的 *\*.csproj* 檔案，並建立以多個架構為目標的單一 *\*.csproj* 檔案。 這是很不錯的選擇，因為單一專案能夠編譯不同的架構。 它也可以處理個別目標架構的不同編譯選項及相依性。

![建立以多個架構為目標的 csproj][example-csproj]

[**原始程式碼**][example-csproj-code]

要注意的變更如下︰
* 將 *packages.config* 和 *\*.csproj* 取代為新的 [.NET Core *\*.csproj*][example-csproj-netcore]。 NuGet 套件是使用 `<PackageReference> ItemGroup` 所指定。

## <a name="keep-existing-projects-and-create-a-net-core-project"></a>保留現有的專案並建立 .NET Core 專案

如果現有的專案以較舊的架構為目標，您可能想要保持這些專案不變，使用 .NET Core 專案以未來的架構為目標。

![在不同資料夾中有現有專案的 .NET Core 專案][example-csproj-different-folder]

[**原始程式碼**][example-csproj-different-code]

要注意的變更如下︰
* .NET Core 和現有的專案保存在不同的資料夾中。
    * 將專案放在不同的資料夾中，可避免強迫使用 Visual Studio 2017。 您可以建立不同的解決方案只開啟舊的專案。

## <a name="see-also"></a>請參閱

如需移轉至 .NET Core 的詳細指引，請參閱 [.NET Core 移植文件][porting-doc]。

[porting-doc]: index.md
[example-initial-project]: media/project-structure/project.png "現有專案"
[example-initial-project-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library/

[example-csproj]: media/project-structure/project.csproj.png "建立以多個架構為目標的 csproj"
[example-csproj-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-csproj/
[example-csproj-netcore]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-csproj/src/Car/Car.csproj

[example-csproj-different-folder]: media/project-structure/project.csproj.different.png "在不同資料夾中有現有 PCL 的 .NET Core 專案"
[example-csproj-different-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-csproj-keep-existing/

[option-csproj]: #replace-existing-projects-with-a-multi-targeted-net-core-project
[option-csproj-folder]: #keep-existing-projects-and-create-a-net-core-project
