---
title: 組織適用於.NET Framework 和.NET Core 的專案
description: 協助想要同時針對 .NET Framework 及 .NET Core 編譯解決方案的專案擁有者。
author: conniey
ms.date: 12/07/2018
ms.openlocfilehash: d71cc3102846c08f4e35831921b8cc4ca82f9e1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75777338"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a>組織專案以同時支援 .NET Framework 及 .NET Core

您可以創建一個解決方案，用於並行為 .NET 框架和 .NET Core 進行編譯。 本文介紹幾個專案組織選項，以説明您實現這一目標。 在決定如何使用 .NET Core 設置專案佈局時，需要考慮以下一些典型方案。 此清單不一定涵蓋您想要的所有項目，根據專案需求決定優先順序。

- [**將現有的專案和 .NET Core 專案合併成單一專案**](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  *適用於︰*
  - 通過編譯單個專案而不是多個專案來簡化生成過程，每個專案都針對不同的 .NET Framework 版本或平臺。
  - 簡化多目標專案的原始檔案管理，因為必須管理單個專案檔案。 添加或刪除原始檔案時，替代方法要求您手動將這些檔與其他專案同步。
  - 輕鬆生成用於消費的 NuGet 包。
  - 讓您使用編譯器指示詞，在程式庫中針對特定的 .NET Framework 版本撰寫程式碼。

  *不支援的方案：*
  - 要求開發人員使用 Visual Studio 2017 或更高版本打開現有專案。 若要支援舊版的 Visual Studio，[將專案檔放在不同的資料夾](#support-vs)是較好的選擇。

- <a name="support-vs"></a>[**將現有的專案和新的 .NET Core 專案分開**](#keep-existing-projects-and-create-a-net-core-project)

  *適用於︰*
  - 支援開發現有專案，供可能沒有 Visual Studio 2017 或更高版本的開發人員和貢獻者開發。
  - 減少在現有專案中創建新 Bug 的可能性，因為這些專案中不需要代碼改動。

## <a name="example"></a>範例

請考慮以下的儲存機制︰

![現有專案](./media/project-structure/existing-project-structure.png)

[**原始程式碼**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/)

下列描述幾種方式以新增這個存放庫的 .NET Core 支援，視現有專案的條件約束和複雜性而定。

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a>使用多目標 .NET Core 專案取代現有的專案

重新組織存儲庫，以便刪除任何現有的*\*.csproj*檔，並創建針對多個框架的單個*\*.csproj*檔。 這是一個不錯的選擇，因為單個專案能夠為不同的框架進行編譯。 它也可以處理個別目標架構的不同編譯選項及相依性。

![建立以多個架構為目標的 csproj](./media/project-structure/multi-targeted-project.png)

[**原始程式碼**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/)

要注意的變更如下︰

- 以新的 [.NET Core *\*.csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj) 取代 *packages.config* 和 *\*.csproj*。 NuGet 套件是使用 `<PackageReference> ItemGroup` 所指定。

## <a name="keep-existing-projects-and-create-a-net-core-project"></a>保留現有的專案並建立 .NET Core 專案

如果現有的專案以較舊的架構為目標，您可能想要保持這些專案不變，使用 .NET Core 專案以未來的架構為目標。

![.NET Core 專案與現有專案位在不同的資料夾](./media/project-structure/separate-projects-same-source.png)

[**原始程式碼**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/)

.NET Core 和現有的專案保存在不同的資料夾中。 將專案保留在單獨的資料夾中可以避免強制您擁有 Visual Studio 2017 或更高版本。 您可以建立不同的解決方案只開啟舊的專案。

## <a name="see-also"></a>另請參閱

- [.NET 核心移植文檔](index.md)
