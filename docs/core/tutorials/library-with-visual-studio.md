---
title: 使用 Visual Studio 建立 .NET 類別庫
description: 瞭解如何使用 Visual Studio 建立 .NET 類別庫。
ms.date: 08/07/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet,contperfq1
ms.openlocfilehash: 6a3f61525ca86afc9ee71d56cbc9450862760ba4
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599508"
---
# <a name="tutorial-create-a-net-class-library-using-visual-studio"></a>教學課程：使用 Visual Studio 建立 .NET 類別庫

在本教學課程中，您會建立簡單的類別庫，其中包含單一字串處理方法。

「類別庫」會定義應用程式所呼叫的類型和方法。 如果程式庫以 .NET Standard 2.0 為目標，則可以由任何 .NET 執行 (，包括支援 .NET Standard 2.0 的 .NET Framework) 。 如果程式庫以 .NET 5 為目標，則可由任何目標為 .NET 5 的應用程式呼叫。 本教學課程說明如何以 .NET 5 為目標。

當您建立類別庫時，可以將它發佈為 NuGet 套件，或作為與使用它之應用程式配套的元件。

## <a name="prerequisites"></a>必要條件

- 已安裝 **.Net Core 跨平臺開發** 工作負載的 [Visual Studio 2019 16.8 版或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。 當您選取此工作負載時，會自動安裝 .NET 5.0 SDK。 本教學課程假設您已啟用在 **新的專案中顯示所有 .Net Core 範本**，如 [教學課程：使用 Visual Studio 建立 .net 主控台應用程式](with-visual-studio.md)中所示。

## <a name="create-a-solution"></a>建立方案

首先，建立空白的方案，將類別庫專案放置在中。 Visual Studio 方案可作為一或多個專案的容器。 您會將其他相關的專案新增至相同的方案。

若要建立空白的方案：

1. 啟動 Visual Studio。

2. 在 [開始] 視窗中，選擇 [ **建立新專案**]。

3. 在 [ **建立新專案** ] 頁面的 [搜尋] 方塊中，輸入 [ **方案** ]。 選擇 [ **空白方案** ] 範本，然後選擇 [ **下一步]**。

   :::image type="content" source="media/library-with-visual-studio/blank-solution.png" alt-text="Visual Studio 中的空白方案範本":::

4. 在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入 **>classlibraryprojects** 。 接著，選擇 [建立]  。

## <a name="create-a-class-library-project"></a>建立類別庫專案

1. 將名為 "StringLibrary" 的新 .NET 類別庫專案加入至方案。

   1. 以滑鼠右鍵按一下 **方案總管** 中的方案，然後選取 [**加入**  >  **新專案**]。

   1. 在 [ **加入新的專案** ] 頁面上，于 [搜尋] 方塊中輸入 **library** 。 從 [語言] 清單中選擇 [ **c #** ] 或 [ **Visual Basic** ，然後從 [平臺] 清單中選擇 [ **所有平臺** ]。 選擇 [ **類別庫** ] 範本，然後選擇 [ **下一步]**。

   1. 在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入 **StringLibrary** ，然後選擇 [**下一步]**。

   1. 在 [ **其他資訊** ] 頁面上，選取 [ **.Net 5.0 (目前的)**]，然後選擇 [ **建立**]。

1. 請檢查以確定程式庫以正確的 .NET 版本為目標。 以滑鼠右鍵按一下 **方案總管** 中的程式庫專案，然後選取 [ **屬性**]。 [ **目標 Framework** ] 文字方塊會顯示專案的目標為 .net 5.0。

1. 如果您是使用 Visual Basic，請清除 [ **根命名空間** ] 文字方塊中的文字。

   :::image type="content" source="./media/library-with-visual-studio/vb/library-project-properties.png" alt-text="類別庫的專案屬性":::

   Visual Basic 會針對每個專案自動建立對應至專案名稱的命名空間。 在本教學課程中，您會使用程式碼檔案中的關鍵字來定義最上層命名空間 [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) 。

1. 以下列程式碼取代 *Class1.cs*  或 *Class1* 程式碼視窗中的程式碼，然後儲存檔案。 如果未顯示您想要使用的語言，請變更頁面頂端的語言選取器。

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibrary/Class1.vb":::

   類別庫（class library） `UtilityLibraries.StringLibrary` 包含名為的方法 `StartsWithUpper` 。 這個方法會傳回 <xref:System.Boolean> 值，指出目前字串實例的開頭是否為大寫字元。 Unicode 標準會區別大寫和小寫字元。 如果是大寫字元，<xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> 方法會傳回 `true`。

   `StartsWithUpper` 會實作為 [擴充方法](../../csharp/programming-guide/classes-and-structs/extension-methods.md) ，如此您就可以呼叫它，就如同它是類別的成員一樣 <xref:System.String> 。

1. 在功能表列上，選取 [**組建**  >  **組建方案**] 或按 <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>B</kbd> ，確認專案編譯時沒有發生錯誤。

## <a name="add-a-console-app-to-the-solution"></a>將主控台應用程式新增至解決方案

加入使用類別庫的主控台應用程式。 應用程式會提示使用者輸入字串，並報告字串是否以大寫字元開頭。

1. 將名為 "展示" 的新 .NET 主控台應用程式加入至方案。

   1. 以滑鼠右鍵按一下 **方案總管** 中的方案，然後選取 [**加入**  >  **新專案**]。

   1. 在 [ **新增專案** ] 頁面的 [搜尋] 方塊中，輸入 **主控台** 。 從 [語言] 清單中選擇 [ **c #** ] 或 [ **Visual Basic** ，然後從 [平臺] 清單中選擇 [ **所有平臺** ]。

   1. 選擇 [ **主控台應用程式** ] 範本，然後選擇 [ **下一步]**。

   1. 在 [**設定您的新專案**] 頁面上，于 [**專案名稱**] 方塊中輸入 **展示**。 然後選擇 [下一步]  。

   1. 在 [**其他資訊**] 頁面上，選取 [**目標 Framework** ] 方塊中的 [ **.net 5.0 (目前)** 。 接著，選擇 [建立]  。

1. 在 *Program.cs* 或 .vb 檔案的 *程式* 代碼視窗中，以下列程式碼取代所有程式碼。

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/ShowCase/Program.vb":::

   該程式碼會使用 `row` 變數來維護寫入至主控台視窗的資料列數目計數。 只要超過或等於25，程式碼就會清除主控台視窗，並向使用者顯示訊息。

   此程式會提示使用者輸入字串。 它會指出該字串開頭是否為大寫字元。 如果使用者按下 <kbd>Enter</kbd> 鍵但未輸入字串，則應用程式會結束，且主控台視窗會關閉。

## <a name="add-a-project-reference"></a>新增專案參考

一開始，新的主控台應用程式專案沒有類別庫的存取權。 若要允許它呼叫類別庫中的方法，請建立類別庫專案的專案參考。

1. 在 **方案總管** 中，以滑鼠右鍵按一下專案的 [相依性 `ShowCase` ] 節點，然後選取 [**加入專案參考** **]** 。

   :::image type="content" source="media/library-with-visual-studio/add-reference-context-menu.png" alt-text="在 Visual Studio 中新增參考內容功能表":::

1. 在 [ **參考管理員** ] 對話方塊中，選取 [ **StringLibrary** ] 專案，然後選取 **[確定]**。

   :::image type="content" source="media/library-with-visual-studio/manage-project-references.png" alt-text="已選取 StringLibrary 的 [參考管理員] 對話方塊":::

## <a name="run-the-app"></a>執行應用程式

1. 在方案總管 中，以滑鼠右鍵按一下 **ShowCase** 專案，然後在內容功能表中選取 [設定為啟始專案]。

   :::image type="content" source="media/library-with-visual-studio/set-startup-project-context-menu.png" alt-text="用來設定啟始專案的 Visual Studio 專案內容功能表":::

1. 按下<kbd>Ctrl</kbd> + <kbd>F5</kbd>以編譯並執行程式，而不需進行任何偵錯工具。

   :::image type="content" source="media/library-with-visual-studio/visual-studio-project-toolbar.png" alt-text="顯示 [調試] 按鈕 Visual Studio 專案工具列":::

1. 輸入字串並按 <kbd>enter</kbd>鍵以嘗試程式，然後按 <kbd>enter</kbd> 鍵結束。

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="具有正在執行展示的主控台視窗":::

## <a name="additional-resources"></a>其他資源

* [使用 .NET CLI 開發程式庫](libraries.md)
* [.NET Standard 支援的版本和平臺](../../standard/net-standard.md)。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已建立類別庫。 在下一個教學課程中，您將瞭解如何對類別庫進行單元測試。

> [!div class="nextstepaction"]
> [使用 Visual Studio 對 .NET 類別庫進行單元測試](testing-library-with-visual-studio.md)

或者，您可以略過自動化單元測試，並瞭解如何藉由建立 NuGet 套件來共用程式庫：

> [!div class="nextstepaction"]
> [使用 Visual Studio 建立及發行套件](/nuget/quickstart/create-and-publish-a-package-using-visual-studio)

或瞭解如何發佈主控台應用程式。 如果您從本教學課程所建立的方案發佈主控台應用程式，類別庫會將它當作 *.dll* 檔來使用。

> [!div class="nextstepaction"]
> [使用 Visual Studio 發佈 .NET 主控台應用程式](publishing-with-visual-studio.md)
