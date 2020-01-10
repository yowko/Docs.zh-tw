---
title: 在 Visual Studio 中取用 .NET Standard 程式庫
description: 建立 .NET Core 應用程式，以使用 Visual Studio 2019 呼叫另一個類別庫的成員。
ms.date: 12/20/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: ec9c6f992bcd4a76e2f70018f3facca42b7b660c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714061"
---
# <a name="consume-a-net-standard-library-in-visual-studio"></a>在 Visual Studio 中取用 .NET Standard 程式庫

建立 .NET Standard 類別庫、測試它並建立程式庫的發行版本之後，下一步就是將它提供給呼叫者。 您可以透過下列兩種方式來執行這項作業：

- 如果該類別庫將供單一方案使用 (例如，如果它是單一大型應用程式中的元件)，您可以直接將它以專案的形式包含在您的方案中。
- 如果程式庫會公開提供，您可以將它發佈為 NuGet 套件。

在本教學課程中，您將了解如何：
> [!div class="checklist"]
>
> - 將主控台應用程式新增至參考 .NET Standard 程式庫專案的方案。
> - 建立包含 .NET Standard 程式庫專案的 NuGet 套件。

## <a name="add-a-console-app-to-your-solution"></a>將主控台應用程式新增至您的解決方案

就像您在[Visual Studio 的測試 .NET Standard 程式庫](testing-library-with-visual-studio.md)中，將單元測試包含在與類別庫相同的方案中，您可以將應用程式納入為該解決方案的一部分。 例如，您可以在提示使用者輸入字串並回報其第一個字元是否為大寫的主控台應用程式中，使用您的類別庫：

1. 開啟您在[Visual Studio 中建立 .NET Standard 程式庫一](library-with-visual-studio.md)文中所建立的 `ClassLibraryProjects` 解決方案。

1. 將名為 "展示" 的新 .NET Core 主控台應用程式加入至方案。

   1. 以滑鼠右鍵按一下**方案總管**中的方案，然後選取 [**加入** > **新增專案**]。

   1. 在 [**加入新專案**] 頁面的 [搜尋] 方塊中，輸入**主控台**。 從**C#** [語言] 清單中選擇或**Visual Basic** ，然後從 [平臺] 清單中選擇 [**所有平臺**]。 選擇 [**主控台應用程式（.Net Core）** ] 範本，然後選擇 [**下一步]** 。

   1. 在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入**展示**。 接著，選擇 [建立]。

1. 在方案總管 中，以滑鼠右鍵按一下 **ShowCase** 專案，然後在內容功能表中選取 [設定為啟始專案]。

   ![Visual Studio 專案操作功能表來設定啟始專案](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. 一開始，您的專案並無法存取類別庫。 若要讓它在您的類別庫中呼叫方法，您可以建立類別庫的參考。 在方案總管 中，以滑鼠右鍵按一下 `ShowCase` 專案的 [相依性] 節點，然後選取 [新增參考]。

   ![Visual Studio 中的 [新增參考] 內容功能表](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. 在 [參考管理員] 對話方塊中，選取**StringLibrary**、您的類別庫專案，然後選取 [確定] 按鈕。

   ![已選取 StringLibrary 的參考管理員對話方塊](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. 在*Program.cs*或*Program .Vb*檔案的程式碼視窗中，將所有程式碼取代為下列程式碼：

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   該程式碼會使用 `row` 變數來維護寫入至主控台視窗的資料列數目計數。 當它大於或等於25時，程式碼就會清除主控台視窗，並向使用者顯示訊息。

   此程式會提示使用者輸入字串。 它會指出該字串開頭是否為大寫字元。 如果使用者在未輸入字串的情況下按 Enter 鍵，應用程式就會結束，而且主控台視窗會關閉。

1. 必要時，變更工具列以編譯 `ShowCase` 專案的 [偵錯] 版本。 選取 **ShowCase** 按鈕上的綠色箭號，以編譯並執行程式。

   ![顯示調試按鈕的 Visual Studio 專案工具列](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

您可以遵循[使用 Visual Studio 來處理C#或 Visual Basic .net core Hello World 應用程式](debugging-with-visual-studio.md)中的步驟，並透過[Visual Studio 發行您的 .net core Hello World 應用](publishing-with-visual-studio.md)程式，以使用此程式庫來進行偵錯工具和發行。

## <a name="create-a-nuget-package"></a>建立 NuGet 套件

您可以藉由 NuGet 套件的形式發行類別庫，讓您的類別庫可供廣泛使用。 Visual Studio 不支援建立 NuGet 套件。 若要建立一個，您必須使用 .NET Core CLI 的命令：

1. 開啟主控台視窗。

   例如，在 Windows 工作列的 [搜尋] 方塊中輸入 [**命令提示**字元]。 選取 [**命令提示**字元] 桌面應用程式，或按下**enter** （如果已在搜尋結果中選取）。

1. 瀏覽至您類別庫的專案目錄。 此目錄包含您的原始程式碼和專案檔*StringLibrary*或*StringLibrary. vbproj*。

1. 執行[dotnet pack](../tools/dotnet-pack.md)命令以產生副檔名為*nupkg*的套件：

   ```dotnetcli
   dotnet pack --no-build
   ```

   > [!TIP]
   > 如果包含 *dotnet.exe* 的目錄不在您的 PATH 中，則您可以在主控台視窗中輸入 `where dotnet.exe` 來尋找其位置。

如需有關建立 NuGet 套件的詳細資訊，請參閱[如何使用跨平台工具建立 NuGet 套件](../deploying/creating-nuget-packages.md)。
