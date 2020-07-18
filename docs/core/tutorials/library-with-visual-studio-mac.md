---
title: 使用 Visual Studio for Mac 建立 .NET Standard 類別庫
description: 瞭解如何使用 Visual Studio for Mac 建立 .NET Standard 類別庫。
ms.date: 06/08/2020
ms.openlocfilehash: 8e1e4ca3bc1b12d889b847d80318f3d6cd1bbe46
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416010"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio-for-mac"></a>教學課程：使用 Visual Studio for Mac 建立 .NET Standard 程式庫

在本教學課程中，您會建立包含單一字串處理方法的類別庫。 您可以將它實作為[擴充方法](../../csharp/programming-guide/classes-and-structs/extension-methods.md)，讓您可以如同類別的成員一樣呼叫它 <xref:System.String> 。

「類別庫」** 會定義應用程式所呼叫的類型和方法。 以 .NET Standard 2.1 為目標的類別庫可供以任何支援2.1 版 .NET Standard 的 .NET 實作為目標的應用程式使用。 當您完成類別庫時，您可以將它散發為協力廠商元件，或作為一或多個應用程式的配套元件。

> [!NOTE]
> 我們非常重視您的意見反應。 您有兩種方式可以提供意見反應給 Visual Studio for Mac 開發小組：
>
> - 在 Visual Studio for Mac 中，從功能表**選取**  >  [說明] [回報**問題**]，或從 [歡迎使用] 畫面中選取 [**回報問題**]，這會開啟用來提出錯誤報表的視窗。 您可在[開發人員社群](https://developercommunity.visualstudio.com/spaces/41/index.html)入口網站追蹤您的意見反應。
> - 若要提出建議，請從功能表**選取 [** 說明]  >  [**提供建議**] 或從 [歡迎使用] 畫面中**提供建議**，這會帶您前往[Visual Studio for Mac 的開發人員社區網頁](https://developercommunity.visualstudio.com/content/idea/post.html?space=41)。

## <a name="prerequisites"></a>先決條件

* [安裝 Visual Studio for Mac 8.6 版或更新](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)版本。 選取 [安裝 .NET Core] 選項。 安裝 Xamarin 對於 .NET Core 開發而言是選擇性的。 如需詳細資訊，請參閱下列資源：

  * [教學課程：安裝 Visual Studio for Mac](/visualstudio/mac/installation)。
  * [支援的 macOS 版本](../install/dependencies.md?pivots=os-macos)。
  * [Visual Studio for Mac 支援的 .Net Core 版本](/visualstudio/mac/net-core-support)。

## <a name="create-a-solution-with-a-class-library-project"></a>使用類別庫專案建立解決方案

Visual Studio 方案會當做一個或多個專案的容器。 在方案中建立方案和類別庫專案。 您稍後會將其他相關的專案新增至相同的方案。

1. 啟動 Visual Studio for Mac。

1. 在 [開始] 視窗中，選取 [**新增專案**]。

1. 在 [**新增專案**] 對話方塊的 [**多平臺**] 節點下，選取 [連結**庫**]，然後選取 [ **.NET Standard 程式庫**] 範本，然後選取 **[下一步]**。

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="[新增專案] 對話方塊":::

1. 在 [**設定新的 .NET Standard 程式庫**] 對話方塊中，選擇 [.NET Standard 2.1]，然後選取 **[下一步]**。

   :::image type="content" source="media/library-with-visual-studio-mac/choose-net-std-21.png" alt-text="選擇 .NET Standard 2。1":::

1. 將專案命名為 "StringLibrary" 和方案 "ClassLibraryProjects"。 在選取**的方案目錄中，保留 [建立專案目錄**]。 選取 [建立]。

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project-options.png" alt-text="Visual Studio for Mac [新增專案] 對話方塊選項":::

1. 從主功能表中，選取 [ **View**  >  **pad**  >  **Solution**]，然後選取 [dock] 圖示以讓 pad 保持開啟。

   :::image type="content" source="media/library-with-visual-studio-mac/solution-dock-icon.png" alt-text="Solution pad 的停駐圖示":::

1. 在 [ **Solution** pad] 中，展開 `StringLibrary` 節點以顯示範本所提供的類別檔案*Class1.cs*。 在檔案上按一下<kbd>ctrl 鍵</kbd>，從內容功能表中選取 [**重新命名**]，然後將檔案重新命名為*StringLibrary.cs*。 開啟檔案，並以下列程式碼取代內容：

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

1. 按<kbd>則是⌘</kbd><kbd>S</kbd> （<kbd>命令</kbd> + <kbd>s</kbd>）以儲存檔案。

1. 選取 IDE 視窗下邊界中的 [錯誤]****，以開啟 [錯誤]**** 面板。 選取 [建置輸出]**** 按鈕。

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-error-button.png" alt-text="Visual Studio Mac IDE 的下邊界，顯示 [錯誤] 按鈕":::

1. **Build**  >  從功能表中選取 [組建**組建全部**]。

   解決方案隨即建置。 建置輸出面板會顯示建置成功。

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-build-panel.png" alt-text="[錯誤] 面板的 Visual Studio Mac [建置輸出] 窗格，其中包含「建置成功」訊息":::

## <a name="add-a-console-app-to-the-solution"></a>將主控台應用程式新增至解決方案

新增使用類別庫的主控台應用程式。 應用程式會提示使用者輸入字串，並報告字串是否以大寫字元開頭。

1. 在 [ **solution** pad] 中，按<kbd>ctrl</kbd>-按一下 `ClassLibraryProjects` 解決方案。 從**Web 和主控台**應用程式範本選取範本，以加入新的**主控台應用程式**專案  >  **App** ，然後選取 **[下一步]**。

1. 選取 [ **.Net Core 3.1** ] 做為**目標架構**，然後選取 **[下一步]**。

1. 為專案**展示**命名。 選取 [建立]**** 以在解決方案中建立專案。

   :::image type="content" source="media/library-with-visual-studio-mac/add-showcase-project.png" alt-text="新增展示專案":::

1. 開啟*Program.cs*檔案。 將程式碼取代為下列程式碼：

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   此程式會提示使用者輸入字串。 它會指出該字串開頭是否為大寫字元。 如果使用者在未輸入字串的情況下按<kbd>enter</kbd>鍵，應用程式就會結束，而且主控台視窗會關閉。

   該程式碼會使用 `row` 變數來維護寫入至主控台視窗的資料列數目計數。 當它大於或等於25時，程式碼就會清除主控台視窗，並向使用者顯示訊息。

## <a name="add-a-project-reference"></a>新增專案參考

一開始，新的主控台應用程式專案無法存取類別庫。 若要讓它能夠呼叫類別庫中的方法，請建立類別庫專案的專案參考。

1. 在 [**解決方案**] 面板中，以<kbd>ctrl 鍵</kbd>按一下新**展示**專案的 [相依性 **]** 節點。 在內容功能表中，選取 [**加入參考**]。

1. 在 [**參考**] 對話方塊中，選取 [ **StringLibrary** ]，然後選取 **[確定]**。

## <a name="run-the-app"></a>執行應用程式

1. <kbd>ctrl</kbd>-按一下展示專案，然後從內容功能表中選取 [**執行專案**]。

1. 輸入字串並按<kbd>enter</kbd>鍵以嘗試程式，然後按<kbd>enter</kbd>結束。

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-console-window.png" alt-text="Visual Studio for Mac 主控台視窗，顯示您的應用程式正在執行":::

## <a name="additional-resources"></a>其他資源

* [使用 .NET Core CLI 開發程式庫](libraries.md)
* [.NET Standard 版本和支援的平臺](../../standard/net-standard.md)。
* [Visual Studio 2019 for Mac 版本資訊](/visualstudio/releasenotes/vs2019-mac-relnotes)

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已建立解決方案和程式庫專案，並加入了使用該程式庫的主控台應用程式專案。 在下一個教學課程中，您會將單元測試專案加入至方案。

> [!div class="nextstepaction"]
> [使用 Visual Studio for Mac 測試具有 .NET Core 的 .NET Standard 程式庫](testing-library-with-visual-studio-mac.md)
