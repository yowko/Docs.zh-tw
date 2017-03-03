---
title: "組織專案以支援 .NET Framework 及 .NET Core"
description: "組織專案以支援 .NET Framework 及 .NET Core"
keywords: ".NET、.NET Core"
author: conniey
ms.author: mairaw
ms.date: 07/18/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 3af62252-1dfa-4336-8d2f-5cfdb57d7724
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: ed2fdad2a784f4e4ce1f8a660b5bb151935fd2d4
ms.lasthandoff: 01/18/2017

---

# <a name="organizing-your-project-to-support-net-framework-and-net-core"></a>組織專案以支援 .NET Framework 及 .NET Core

本文是為了協助想要同時針對 .NET Framework 及 .NET Core 編譯解決方案的專案擁有者。  它提供數個選項，組織專案以協助開發人員達成此目標。  以下是當您決定如何使用 .NET Core 設定專案配置時，要考量的一些典型案例。  它們不一定涵蓋您想要的所有項目，專案需求決定優先順序。

* [**將現有的專案和 .NET Core 專案合併成單一專案**][option-xproj]
  
  *適用於︰*
  * 藉由編譯單一專案而非編譯多個專案，每個都會以不同的 .NET Framework 版本或平台為目標，以簡化建置流程。
  * 因為您必須管理單一專案檔案，所以簡化多目標專案的來源檔案管理。  新增/移除來源檔案時，替代方案需要您手動同步處理這些專案與其他專案。
  * 輕鬆產生 NuGet 封裝以供耗用。
  * 讓您使用編譯器指示詞，在程式庫中針對特定的 .NET Framework 版本撰寫程式碼。
  
  *不支援的情節：*
  * 不允許開發人員不使用 Visual Studio 2015 開啟現有的專案。 若要支援舊版的 Visual Studio，[將專案檔放在不同的資料夾](#support-vs)是較好的選擇。
  * 不允許您在相同的方案檔中，跨不同專案類型共用 .NET Core 程式庫。 若要支援此功能，[建立可攜式類別庫](#support-pcl)是較好的選擇。
  * 不允許 MSBuild 目標和工作支援的專案組建或負載修改。 若要支援此功能，[建立可攜式類別庫](#support-pcl)是較好的選擇。

* <a name="support-vs"></a>[**將現有的專案和新的 .NET Core 專案分開**][option-xproj-folder]
  
  *適用於︰*
  * 繼續支援現有專案的開發，但不必升級可能沒有 Visual Studio 2015 的開發人員/參與者。
  * 減少現有專案中製造新 bug 的可能性，因為這些專案不需要任何程式碼變換。

* <a name="support-pcl"></a>[**保留現有的專案並建立以 .NET Core 為目標的可攜式類別庫 (PCL)**][option-pcl]

  *適用於︰*
  * 參考桌面的 .NET Core 程式庫及/或相同方案中以完整 .NET Framework 為目標的 Web 專案。
  * 支援修改專案組建或載入程序。 這些修改可以包含 `*.csproj` 檔案中的 MSBuild 工作和目標。

  *不支援的情節：*
  * 不允許您針對特定的 .NET Framework 版本撰寫程式碼，因為不支援[預先定義的前置處理器符號][how-to-multitarget]。

## <a name="example"></a>範例

請考慮以下的儲存機制︰

![現有專案][example-initial-project]

[**原始程式碼**][example-initial-project-code]

有幾種不同的方式可以加入此儲存機制的 .NET Core 支援，視現有專案的條件約束和複雜性而定，後文會說明。

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project-xproj"></a>使用多目標 .NET Core 專案 (xproj) 取代現有的專案

儲存機制可以重新組織，以便移除任何現有的 `*.csproj` 檔案，並建立以多個架構為目標的單一 `*.xproj` 檔案。  這是很不錯的選擇，因為單一專案能夠編譯不同的架構。  它也有能力處理不同的編譯選項、相依性等等。 依目標架構。

![建立以多個架構為目標的 xproj][example-xproj]

[**原始程式碼**][example-xproj-code]

要注意的變更如下︰
* 新增 `global.json`
* 將 `packages.config` 和 `*.csproj` 替換成 `project.json` 和 `*.xproj`
* [Car's project.json][example-xproj-projectjson] 及其[測試專案][example-xproj-projectjson-test]中，支援建置現有 .NET Framework 以及其他架構的變更

## <a name="create-a-portable-class-library-pcl-to-target-net-core"></a>建立以 .NET Core 為目標的可攜式類別庫 (PCL)

如果現有的專案在其 `*.csproj` 檔案中包含複雜的建置作業或內容，建立 PCL 會很容易。

![][example-pcl]

[**原始程式碼**][example-pcl-code]

要注意的變更如下︰
*  將 `project.json` 重新命名為 `{project-name}.project.json`
    * 嘗試還原相同目錄中的程式庫封裝時，這可避免 Visual Studio 中的潛在衝突。 如需詳細資訊，請參閱 [NuGet 常見問題集](https://docs.nuget.org/consume/nuget-faq#working-with-packages)的「_我在同一個資料夾中有多個專案，我該如何為每個專案使用不同的 packages.config 或 project.json 檔案的？_」
    *  **替代**︰在另一個資料夾中建立 PCL，並參考原始的原始程式碼避免這個問題。  將 PCL 放在另一個資料夾中的額外好處，是沒有 Visual Studio 2015 的使用者仍可使用較舊的專案，不必載入新的方案。
*  若要在建立 PCL 之後以 .NET Standard 為目標，請在 Visual Studio 中開啟 [Project's Properties]\(專案的內容)。 在 [目標] 區段中，按一下 [以 .NET 平台標準為目標] 連結。  重複相同的步驟可以反轉這項變更。

## <a name="keep-existing-projects-and-create-a-net-core-project"></a>保留現有的專案並建立 .NET Core 專案

如果現有的專案以較舊的架構為目標，您可能想要保持這些專案不變，使用 .NET Core 專案以未來的架構為目標。

![在不同資料夾中有現有 PCL 的 .NET Core 專案][example-xproj-different-folder]

[**原始程式碼**][example-xproj-different-code]

要注意的變更如下︰
* .NET Core 和現有的專案保存在不同的資料夾中。
    * 這會避免前文中因為同一資料夾中有多個 project.json/package.config 檔案所造成的封裝還原問題。
    * 將專案放在不同的資料夾中，可避免強迫使用 Visual Studio 2015 (因 project.json 之故)。  您可以建立不同的解決方案只開啟舊的專案。

## <a name="see-also"></a>另請參閱

如需移至 project.json 和 xproj 的詳細指引，請參閱 [.NET Core 移轉文件][porting-doc]。

[porting-doc]: index.md
[example-initial-project]: media/project-structure/project.png "現有專案"
[example-initial-project-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library/

[example-xproj]: media/project-structure/project.xproj.png "建立以多個架構為目標的 xproj"
[example-xproj-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-xproj/
[example-xproj-projectjson]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-xproj/src/Car/project.json
[example-xproj-projectjson-test]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-xproj/tests/Car.Tests/project.json

[example-xproj-different-folder]: media/project-structure/project.xproj.different.png "在不同資料夾中有現有 PCL 的 .NET Core 專案"
[example-xproj-different-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-xproj-keep-csproj/

[example-pcl]: media/project-structure/project.pcl.png "以 .NET Core 為目標的 PCL"
[example-pcl-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-pcl

[option-xproj]: #replace-existing-projects-with-a-multi-targeted-net-core-project-xproj
[option-pcl]: #create-a-portable-class-library-pcl-to-target-net-core
[option-xproj-folder]: #keep-existing-projects-and-create-a-net-core-project

[how-to-multitarget]: ../tutorials/libraries.md#how-to-multitarget

