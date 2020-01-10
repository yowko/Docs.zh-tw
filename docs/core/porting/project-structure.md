---
title: 組織適用於.NET Framework 和.NET Core 的專案
description: 協助想要同時針對 .NET Framework 及 .NET Core 編譯解決方案的專案擁有者。
author: conniey
ms.date: 12/07/2018
ms.openlocfilehash: d71cc3102846c08f4e35831921b8cc4ca82f9e1b
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777338"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a>組織專案以同時支援 .NET Framework 及 .NET Core

您可以建立同時編譯 .NET Framework 和 .NET Core 的解決方案。 本文涵蓋數個可協助您達成此目標的專案組織選項。 以下是當您決定如何使用 .NET Core 設定專案配置時，要考慮的一些典型案例。 此清單不一定涵蓋您想要的所有項目，根據專案需求決定優先順序。

- [**將現有的專案和 .NET Core 專案合併成單一專案**](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  *適用於︰*
  - 藉由編譯單一專案，而不是每個以不同 .NET Framework 版本或平臺為目標的多個專案，來簡化您的組建程式。
  - 簡化多目標專案的來源檔案管理，因為您必須管理單一專案檔案。 新增或移除原始程式檔時，替代方案會要求您手動同步處理這些檔案與其他專案。
  - 輕鬆產生用於耗用量的 NuGet 套件。
  - 讓您使用編譯器指示詞，在程式庫中針對特定的 .NET Framework 版本撰寫程式碼。

  *不支援的情節：*
  - 需要開發人員使用 Visual Studio 2017 或更新版本來開啟現有的專案。 若要支援舊版的 Visual Studio，[將專案檔放在不同的資料夾](#support-vs)是較好的選擇。

- <a name="support-vs"></a>[**將現有的專案和新的 .NET Core 專案分開**](#keep-existing-projects-and-create-a-net-core-project)

  *適用於︰*
  - 針對可能沒有 Visual Studio 2017 或更新版本的開發人員和參與者，支援在現有專案上進行開發。
  - 降低在現有專案中建立新 bug 的可能性，因為這些專案不需要任何程式碼變換。

## <a name="example"></a>範例

請考慮以下的儲存機制︰

![現有專案](./media/project-structure/existing-project-structure.png)

[**Source Code**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/) (原始程式碼)

下列描述幾種方式以新增這個存放庫的 .NET Core 支援，視現有專案的條件約束和複雜性而定。

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a>使用多目標 .NET Core 專案取代現有的專案

重新組織存放庫，以便移除任何現有的 *\*.csproj* 檔案，並建立以多個架構為目標的單一 *\*.csproj* 檔案。 這是很好的選擇，因為單一專案可以針對不同的架構進行編譯。 它也可以處理個別目標架構的不同編譯選項及相依性。

![建立以多個架構為目標的 .csproj](./media/project-structure/multi-targeted-project.png)

[**Source Code**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/) (原始程式碼)

要注意的變更如下︰

- 以新的 [.NET Core *\*.csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj) 取代 *packages.config* 和 *\*.csproj*。 NuGet 套件是使用 `<PackageReference> ItemGroup` 所指定。

## <a name="keep-existing-projects-and-create-a-net-core-project"></a>保留現有的專案並建立 .NET Core 專案

如果現有的專案以較舊的架構為目標，您可能想要保持這些專案不變，使用 .NET Core 專案以未來的架構為目標。

![.NET Core 專案與現有專案位在不同的資料夾](./media/project-structure/separate-projects-same-source.png)

[**Source Code**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/) (原始程式碼)

.NET Core 和現有的專案保存在不同的資料夾中。 將專案保留在不同的資料夾中，可避免強制您擁有 Visual Studio 2017 或更新版本。 您可以建立不同的解決方案只開啟舊的專案。

## <a name="see-also"></a>請參閱

- [.NET Core 移植檔](index.md)
