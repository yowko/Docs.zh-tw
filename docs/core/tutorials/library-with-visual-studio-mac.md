---
title: 使用 Visual Studio for Mac 建立 .NET 類別庫
description: 瞭解如何使用 Visual Studio for Mac 建立 .NET 類別庫。
ms.date: 11/30/2020
ms.openlocfilehash: 1b6b26de06d18d505fa6dde3ff9779a3dab3f1e6
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599291"
---
# <a name="tutorial-create-a-net-class-library-using-visual-studio-for-mac"></a>教學課程：使用 Visual Studio for Mac 建立 .NET 類別庫

在本教學課程中，您會建立包含單一字串處理方法的類別庫。

「類別庫」會定義應用程式所呼叫的類型和方法。 如果程式庫以 .NET Standard 2.0 為目標，則可以由任何 .NET 執行 (，包括支援 .NET Standard 2.0 的 .NET Framework) 。 如果程式庫以 .NET 5 為目標，則可由任何目標為 .NET 5 的應用程式呼叫。 本教學課程說明如何以 .NET 5 為目標。

> [!NOTE]
> 我們非常重視您的意見反應。 您有兩種方式可以提供意見反應給 Visual Studio for Mac 開發小組：
>
> - 在 Visual Studio for Mac 中， **Help**  >  **Report a Problem** 從功能表中選取 [說明]，或從歡迎畫面回報 **問題**，這會開啟用來提出錯誤報表的視窗。 您可在[開發人員社群](https://aka.ms/feedback/report?space=41)入口網站追蹤您的意見反應。
> - 若要提出建議，請從功能表中 **選取 [** 說明]  >  **提供建議**，或從歡迎畫面 **提供** 建議，這會帶您前往 [Visual Studio for Mac 開發人員社群網頁](https://aka.ms/feedback/suggest?space=41)。

## <a name="prerequisites"></a>必要條件

* [安裝 Visual Studio for Mac 8.8 版或更新版本](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)。 選取安裝 .NET Core 的選項。 安裝 Xamarin 是適用于 .NET 開發的選擇性選項。 如需詳細資訊，請參閱下列資源：

  * [教學課程：安裝 Visual Studio for Mac](/visualstudio/mac/installation)。
  * [支援的 macOS 版本](../install/macos.md)。
  * [Visual Studio for Mac 支援的 .net 版本](/visualstudio/mac/net-core-support)。

## <a name="create-a-solution-with-a-class-library-project"></a>使用類別庫專案建立方案

Visual Studio 方案可作為一或多個專案的容器。 在方案中建立方案和類別庫專案。 您稍後會將其他相關的專案加入至相同的方案。

1. 開始 Visual Studio for Mac。

1. 在 [開始] 視窗中，選取 [ **新增專案**]。

1. 在 [**為新專案選擇範本**] 對話方塊中，選取 [ **Web 和主控台** 連結  >  **庫**  >  **類別庫**]，然後選取 **[下一步]**。

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="[新增專案] 對話方塊":::

1. 在 [ **設定您的新類別庫** ] 對話方塊中，選擇 [ **.net 5.0**]，然後選取 **[下一步**]。

1. 將專案命名為 "StringLibrary"，並將方案命名為 ">classlibraryprojects"。 在選取 **的方案目錄內保持建立專案目錄** 。 選取 [建立]。

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project-options.png" alt-text="Visual Studio for Mac [新增專案] 對話方塊選項":::

1. 從主功能表中，選取 [ **View**  >  **Solution**]，然後選取 [dock] 圖示，讓板保持開啟狀態。

   :::image type="content" source="media/library-with-visual-studio-mac/solution-dock-icon.png" alt-text="Solution pad 的停駐圖示":::

1. 在 **Solution** pad 中，展開 `StringLibrary` 節點以顯示範本 *Class1.cs* 所提供的類別檔案。 <kbd>ctrl</kbd>-按一下該檔案，從內容功能表中選取 [ **重新命名** ]，然後將檔案重新命名為 *StringLibrary.cs*。 開啟檔案，並以下列程式碼取代內容：

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

1. 按<kbd>⌘</kbd><kbd> (</kbd> <kbd>命令</kbd> + <kbd>S</kbd>) 來儲存檔案。

1. 選取 IDE 視窗下邊界中的 [錯誤]，以開啟 [錯誤] 面板。 選取 [建置輸出] 按鈕。

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-error-button.png" alt-text="Visual Studio Mac IDE 的下邊界，顯示 [錯誤] 按鈕":::

1. **Build**  >  從功能表選取 [**全部組建組建**]。

   解決方案隨即建置。 建置輸出面板會顯示建置成功。

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-build-panel.png" alt-text="[錯誤] 面板的 Visual Studio Mac [建置輸出] 窗格，其中包含「建置成功」訊息":::

## <a name="add-a-console-app-to-the-solution"></a>將主控台應用程式新增至解決方案

加入使用類別庫的主控台應用程式。 應用程式會提示使用者輸入字串，並報告字串是否以大寫字元開頭。

1. 在 **solution** pad 中， <kbd>ctrl +</kbd>按一下 `ClassLibraryProjects` 方案。 從 **Web 和主控台** **Console Application**  >  **應用程式** 範本選取範本，然後選取 [**下一步]**，以新增主控台應用程式專案。

1. 選取 [ **.net 5.0** ] 作為 **目標架構** ，然後選取 **[下一步]**。

1. 命名專案 **展示**。 選取 [建立] 以在解決方案中建立專案。

   :::image type="content" source="media/library-with-visual-studio-mac/add-showcase-project.png" alt-text="新增展示專案":::

1. 開啟 *Program.cs* 檔案。 以下列程式碼取代程式碼：

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   此程式會提示使用者輸入字串。 它會指出該字串開頭是否為大寫字元。 如果使用者按下 <kbd>enter</kbd> 鍵但未輸入字串，則應用程式會結束，且主控台視窗會關閉。

   該程式碼會使用 `row` 變數來維護寫入至主控台視窗的資料列數目計數。 只要超過或等於25，程式碼就會清除主控台視窗，並向使用者顯示訊息。

## <a name="add-a-project-reference"></a>新增專案參考

一開始，新的主控台應用程式專案沒有類別庫的存取權。 若要允許它呼叫類別庫中的方法，請建立類別庫專案的專案參考。

1. 在 [**方案**] 面板中， <kbd>ctrl +</kbd>按一下新 **展示** 專案的 [相依性 **]** 節點。 在內容功能表中，選取 [ **加入參考**]。

1. 在 [ **參考** ] 對話方塊中，選取 [ **StringLibrary** ]，然後選取 **[確定]**。

## <a name="run-the-app"></a>執行應用程式

1. <kbd>ctrl</kbd>-按一下 **展示** 專案，然後從內容功能表中選取 [ **執行專案** ]。

1. 輸入字串並按 <kbd>enter</kbd>鍵以嘗試程式，然後按 <kbd>enter</kbd> 鍵結束。

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-console-window.png" alt-text="Visual Studio for Mac 主控台視窗，顯示您的應用程式正在執行":::

## <a name="additional-resources"></a>其他資源

* [使用 .NET CLI 開發程式庫](libraries.md)
* [Visual Studio 2019 for Mac 版本資訊](/visualstudio/releasenotes/vs2019-mac-relnotes)
* [.NET Standard 支援的版本和平臺](../../standard/net-standard.md)。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已建立方案和程式庫專案，並新增了使用該程式庫的主控台應用程式專案。 在下一個教學課程中，您會將單元測試專案加入至方案。

> [!div class="nextstepaction"]
> [使用 Visual Studio for Mac 測試 .NET 類別庫](testing-library-with-visual-studio-mac.md)
