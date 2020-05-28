---
title: 在 Visual Studio 中建立 .NET Standard 類別庫
description: 瞭解如何使用 Visual Studio 建立 .NET Standard 類別庫。
ms.date: 05/21/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 2afe11ad75fc36a67efed48d56dbafb11bceaf2a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005227"
---
# <a name="tutorial-create-a-net-standard-library-in-visual-studio"></a>教學課程：在 Visual Studio 中建立 .NET Standard 程式庫

「類別庫」** 會定義應用程式所呼叫的類型和方法。 以 .NET Standard 2.0 為目標的類別庫，可讓任何支援該版本 .NET Standard 的 .NET 部署呼叫您的程式庫。 當您完成類別庫時，您可以決定要將它散發為協力廠商元件，還是要將它併入作為一或多個應用程式隨附的元件。

> [!NOTE]
> 如需所支援的 .NET Standard 版本和平臺清單，請參閱[.NET Standard](../../standard/net-standard.md)。

在本教學課程中，您會建立包含單一字串處理方法的簡單公用程式程式庫。 您可以將它實作為[擴充方法](../../csharp/programming-guide/classes-and-structs/extension-methods.md)，讓您可以如同類別的成員一樣呼叫它 <xref:System.String> 。

## <a name="prerequisites"></a>必要條件

- 已安裝 **.Net Core 跨平臺開發**工作負載的[Visual Studio 2019 16.6 版或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。 當您選取此工作負載時，會自動安裝 .NET Core 3.1 SDK。

  如需詳細資訊，請參閱[安裝 .NET Core SDK](../install/sdk.md?pivots=os-windows)一文中的[install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio)一節。

## <a name="create-a-visual-studio-solution"></a>建立 Visual Studio 解決方案

一開始先建立一個空白的方案，將類別庫專案放入中。 Visual Studio 方案會當做一個或多個專案的容器。 您會在相同的方案中加入其他相關的專案。

若要建立空白解決方案：

1. 開啟 Visual Studio。

2. 在 [開始] 視窗中，選擇 [**建立新專案**]。

3. 在 [**建立新專案**] 頁面的 [搜尋] 方塊中，輸入 [**方案**]。 選擇 [**空白解決方案**] 範本，然後選擇 [**下一步]**。

   ![Visual Studio 中的空白方案範本](media/library-with-visual-studio/blank-solution.png)

4. 在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入**ClassLibraryProjects** 。 接著，選擇 [建立]  。

## <a name="create-a-class-library-project"></a>建立類別庫專案

1. 將名為 "StringLibrary" 的新 .NET Standard 類別庫專案加入至方案。

   1. 以滑鼠右鍵按一下**方案總管**中的方案，然後選取 [**加入**  >  **新專案**]。

   1. 在 [**加入新專案**] 頁面的 [搜尋] 方塊中，輸入 [連結**庫**]。 選擇 [語言] 清單中的 [ **c #** ] 或 [ **Visual Basic** ，然後從 [平臺] 清單中選擇 [**所有平臺**]。 選擇 [**類別庫（.NET Standard）** ] 範本，然後選擇 **[下一步]**。

   1. 在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入**StringLibrary** 。 然後選擇 [**建立**]。

1. 請檢查並確定程式庫的目標是正確的 .NET Standard 版本。 以滑鼠右鍵按一下**方案總管**中的 [程式庫] 專案，然後選取 [**屬性**]。 [**目標 Framework** ] 文字方塊會顯示專案的目標為 .NET Standard 2.0。

   ![類別庫的專案屬性](./media/library-with-visual-studio/library-project-properties.png)

1. 如果您使用的是 Visual Basic，請清除 [**根命名空間**] 文字方塊中的文字。

   ![類別庫的專案屬性](./media/library-with-visual-studio/vb/library-project-properties.png)

   針對每個專案，Visual Basic 會自動建立對應至專案名稱的命名空間。 在本教學課程中，您會使用程式碼檔案中的關鍵字來定義最上層命名空間 [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) 。

1. 使用下列程式碼取代*Class1.cs*或*Class1*的程式碼視窗中的程式碼，並儲存檔案。 如果未顯示您想要使用的語言，請變更頁面頂端的 [語言選取器]。

   [!code-csharp[](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]
   [!code-vb[](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   類別庫 `UtilityLibraries.StringLibrary` 包含名為的方法 `StartsWithUpper` 。 這個方法會傳回 <xref:System.Boolean> 值，指出目前的字串實例是否以大寫字元開頭。 Unicode 標準會區別大寫和小寫字元。 如果是大寫字元，<xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> 方法會傳回 `true`。

1. 在功能表列上，選取 [**組建**] [組建  >  **方案**] 以確認專案編譯無誤。

## <a name="add-a-console-app-to-the-solution"></a>將主控台應用程式新增至解決方案

在主控台應用程式中使用類別庫，以提示使用者輸入字串，並報告字串是否以大寫字元開頭。

1. 將名為 "展示" 的新 .NET Core 主控台應用程式加入至方案。

   1. 以滑鼠右鍵按一下**方案總管**中的方案，然後選取 [**加入**  >  **新專案**]。

   1. 在 [**加入新專案**] 頁面的 [搜尋] 方塊中，輸入**主控台**。 選擇 [語言] 清單中的 [ **c #** ] 或 [ **Visual Basic** ，然後從 [平臺] 清單中選擇 [**所有平臺**]。

   1. 選擇 [**主控台應用程式（.Net Core）** ] 範本，然後選擇 [**下一步]**。

   1. 在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入**展示**。 接著，選擇 [建立]  。

1. 在方案總管**** 中，以滑鼠右鍵按一下 **ShowCase** 專案，然後在內容功能表中選取 [設定為啟始專案]****。

   ![Visual Studio 專案操作功能表來設定啟始專案](media/library-with-visual-studio/set-startup-project-context-menu.png)

1. 一開始，新的主控台應用程式專案無法存取類別庫。 若要讓它能夠呼叫類別庫中的方法，請建立類別庫專案的專案參考。 在**方案總管**中，以滑鼠右鍵按一下專案的 [相依性 `ShowCase` ] 節點，然後選取 [**加入專案參考** **]** 。

   ![Visual Studio 中的 [新增參考] 內容功能表](media/library-with-visual-studio/add-reference-context-menu.png)

1. 在 [**參考管理員**] 對話方塊中，選取 [ **StringLibrary** ] 專案，然後選取 **[確定]**。

   ![已選取 StringLibrary 的參考管理員對話方塊](media/library-with-visual-studio/manage-project-references.png)

1. 在*Program.cs*或*Program .Vb*檔案的程式碼視窗中，將所有程式碼取代為下列程式碼。

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   該程式碼會使用 `row` 變數來維護寫入至主控台視窗的資料列數目計數。 當它大於或等於25時，程式碼就會清除主控台視窗，並向使用者顯示訊息。

   此程式會提示使用者輸入字串。 它會指出該字串開頭是否為大寫字元。 如果使用者在未輸入字串的情況下按 Enter 鍵，應用程式就會結束，而且主控台視窗會關閉。

1. 必要時，變更工具列以編譯 `ShowCase` 專案的 [偵錯]**** 版本。 選取 **ShowCase** 按鈕上的綠色箭號，以編譯並執行程式。

   ![顯示調試按鈕的 Visual Studio 專案工具列](media/library-with-visual-studio/visual-studio-project-toolbar.png)

1. 輸入字串並按**enter**鍵以嘗試程式，然後按**enter**結束。

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="展示執行中的主控台視窗":::

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已建立解決方案、新增程式庫專案，以及加入使用該程式庫的主控台應用程式專案。 在下一個教學課程中，您會將單元測試專案加入至方案。

> [!div class="nextstepaction"]
> [在 Visual Studio 中使用 .NET Core 測試 .NET Standard 程式庫](testing-library-with-visual-studio.md)
