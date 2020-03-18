---
title: 在 Visual Studio 中取用 .NET Standard 程式庫
description: 使用 Visual Studio 2019 構建一個 .NET Core 應用程式，調用另一個類庫的成員。
ms.date: 12/20/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4eb75f23359334ea483cba1498f1804c4b24c80c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920462"
---
# <a name="consume-a-net-standard-library-in-visual-studio"></a>在 Visual Studio 中取用 .NET Standard 程式庫

創建 .NET 標準類庫、測試並生成庫發佈版本後，下一步是使其可供調用方使用。 您可以使用兩種方式執行此動作：

- 如果該類別庫將供單一方案使用 (例如，如果它是單一大型應用程式中的元件)，您可以直接將它以專案的形式包含在您的方案中。
- 如果庫將公開提供，則可以將其分發為 NuGet 包。

在本教學課程中，您會了解如何：
> [!div class="checklist"]
>
> - 將主控台應用添加到引用 .NET 標準庫專案的解決方案。
> - 創建包含 .NET 標準庫專案的 NuGet 包。

## <a name="add-a-console-app-to-your-solution"></a>將主控台應用添加到解決方案

正如在[Visual Studio 中的測試 .NET 標準庫](testing-library-with-visual-studio.md)中將單元測試包含在與類庫相同的解決方案中一樣，您可以將應用程式包含在該解決方案中。 例如，您可以在提示使用者輸入字串並回報其第一個字元是否為大寫的主控台應用程式中，使用您的類別庫：

1. 打開在`ClassLibraryProjects`Visual Studio 文章中[生成 .NET 標準庫中](library-with-visual-studio.md)創建的解決方案。

1. 向解決方案添加新的 .NET 核心主控台應用程式，名為"ShowCase"。

   1. 按右鍵**解決方案資源管理器**中的解決方案，然後選擇"**添加新** > **專案**"。

   1. 在"**添加新專案**"頁上，在搜索框中輸入**主控台**。 從"語言"清單中選擇**C#** 或**視覺化基本，** 然後從"平臺"清單中選擇 **"所有平臺**"。 選擇**主控台應用 （.NET 核心）** 範本，然後選擇 **"下一步**"。

   1. 在"**配置新專案**"頁上，在 **"專案名稱**"框中輸入 **"顯示案例**"。 然後，選擇 **"創建**"。

1. 在方案總管**** 中，以滑鼠右鍵按一下 **ShowCase** 專案，然後在內容功能表中選取 [設定為啟始專案]****。

   ![視覺化工作室專案內容功能表，用於設置啟動專案](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. 一開始，您的專案並無法存取類別庫。 若要讓它在您的類別庫中呼叫方法，您可以建立類別庫的參考。 在方案總管**** 中，以滑鼠右鍵按一下 `ShowCase` 專案的 [相依性]**** 節點，然後選取 [新增參考]****。

   ![在視覺化工作室中添加參考內容功能表](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. 在 [參考管理員]**** 對話方塊中，選取**StringLibrary**、您的類別庫專案，然後選取 [確定]**** 按鈕。

   ![選定字串庫的參考管理器對話方塊](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. 在*Program.cs*或*程式.vb*檔的代碼視窗中，將所有代碼替換為以下代碼：

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   該程式碼會使用 `row` 變數來維護寫入至主控台視窗的資料列數目計數。 每當它大於或等於 25 時，代碼都會清除主控台視窗並顯示給使用者的消息。

   此程式會提示使用者輸入字串。 它會指出該字串開頭是否為大寫字元。 如果使用者在不輸入字串的情況下按下 Enter 鍵，應用程式將結束，主控台視窗將關閉。

1. 必要時，變更工具列以編譯 `ShowCase` 專案的 [偵錯]**** 版本。 選取 **ShowCase** 按鈕上的綠色箭號，以編譯並執行程式。

   ![視覺化工作室專案工具列顯示調試按鈕](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

您可以使用 Visual Studio 調試和發佈使用此庫的應用程式，按照調試[C# 或 Visual Basic .NET 核心 Hello World 應用程式](debugging-with-visual-studio.md)的步驟，並使用 Visual Studio[發佈您的 .NET Core Hello World 應用程式](publishing-with-visual-studio.md)。

## <a name="create-a-nuget-package"></a>建立 NuGet 套件

您可以藉由 NuGet 套件的形式發行類別庫，讓您的類別庫可供廣泛使用。 視覺化工作室不支援創建 NuGet 包。 要創建一個，您需要使用 .NET 核心 CLI 命令：

1. 開啟主控台視窗。

   例如，在 Windows 工作列上的搜索框中輸入**命令提示符**。 選擇**命令提示**桌面應用，或按**Enter，** 如果它已在搜尋結果中選擇。

1. 瀏覽至您類別庫的專案目錄。 該目錄包含您的原始程式碼和專案檔案 *，StringLibrary.csproj*或*StringLibrary.vbproj*。

1. 運行[dotnet pack](../tools/dotnet-pack.md)命令以生成具有 *.nupkg*副檔名的包：

   ```dotnetcli
   dotnet pack --no-build
   ```

   > [!TIP]
   > 如果包含 *dotnet.exe* 的目錄不在您的 PATH 中，則您可以在主控台視窗中輸入 `where dotnet.exe` 來尋找其位置。

有關創建 NuGet 包的詳細資訊，請參閱[如何使用 .NET 核心 CLI 創建 NuGet 包](../deploying/creating-nuget-packages.md)。
