---
title: 在 Visual Studio 中建立 .NET Standard 類別庫
description: 瞭解如何使用 Visual Studio 來建立以C#或 Visual Basic 撰寫的 .NET Standard 類別庫
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 748a1499e0c3a4a41613a69b715dbcfbd585bfe3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714012"
---
# <a name="build-a-net-standard-library-in-visual-studio"></a>在 Visual Studio 中建立 .NET Standard 程式庫

「類別庫」會定義應用程式所呼叫的類型和方法。 以 .NET Standard 2.0 為目標的類別庫，可讓任何支援該版本 .NET Standard 的 .NET 部署呼叫您的程式庫。 當您完成類別庫時，您可以決定要將它散發為協力廠商元件，還是要將它併入作為一或多個應用程式隨附的元件。

> [!NOTE]
> 如需所支援的 .NET Standard 版本和平臺清單，請參閱[.NET Standard](../../standard/net-standard.md)。

在本主題中，您將建立含有單一字串處理方法的簡單公用程式類別庫。 您將它實作為[擴充方法](../../csharp/programming-guide/classes-and-structs/extension-methods.md)，以便可以如同 <xref:System.String> 類別的成員一般來進行呼叫。

## <a name="create-a-visual-studio-solution"></a>建立 Visual Studio 解決方案

一開始先建立一個空白的方案，將類別庫專案放入中。 Visual Studio 方案會當做一個或多個專案的容器。 如果您繼續進行教學課程系列，您會將其他的相關專案新增至相同的方案。

若要建立空白解決方案：

1. 開啟 Visual Studio。

2. 在開始視窗中，選擇 [建立新專案]。

3. 在 [**建立新專案**] 頁面的 [搜尋] 方塊中，輸入 [**方案**]。 選擇 [**空白解決方案**] 範本，然後選擇 [**下一步]** 。

   ![Visual Studio 中的空白方案範本](media/library-with-visual-studio/blank-solution.png)

4. 在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入**ClassLibraryProjects** 。 接著，選擇 [建立]。

> [!TIP]
> 您也可以略過此步驟，並在下一個步驟中建立專案時，讓 Visual Studio 為您建立解決方案。 在 [**設定您的新專案**] 頁面上尋找解決方案選項。

## <a name="create-a-class-library-project"></a>建立類別庫專案

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. 將名為C# "StringLibrary" 的新 .NET Standard 類別庫專案加入至方案。

   1. 以滑鼠右鍵按一下**方案總管**中的方案，然後選取 [**加入** > **新增專案**]。

   1. 在 [**加入新專案**] 頁面的 [搜尋] 方塊中，輸入 [連結**庫**]。 從**C#** [語言] 清單中選擇，然後從 [平臺] 清單中選擇 [**所有平臺**]。 選擇 [**類別庫（.NET Standard）** ] 範本，然後選擇 **[下一步]** 。

   1. 在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入**StringLibrary** 。 接著，選擇 [建立]。

1. 請檢查並確定程式庫的目標是正確的 .NET Standard 版本。 以滑鼠右鍵按一下**方案總管**中的 [程式庫] 專案，然後選取 [**屬性**]。 [**目標 Framework** ] 文字方塊會顯示專案的目標為 .NET Standard 2.0。

   ![類別庫的專案屬性](./media/library-with-visual-studio/library-project-properties.png)

1. 以下列程式碼取代程式碼視窗中的程式碼，並儲存檔案：

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   類別庫（`UtilityLibraries.StringLibrary`）包含名為 `StartsWithUpper`的方法。 這個方法會傳回 <xref:System.Boolean> 值，指出目前的字串實例是否以大寫字元開頭。 Unicode 標準會區別大寫和小寫字元。 如果是大寫字元，<xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> 方法會傳回 `true`。

1. 在功能表列中，選取 [組建] >  [組建方案]。

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. 將名為 "StringLibrary" 的新 Visual Basic .NET Standard 類別庫專案加入至方案。

   1. 以滑鼠右鍵按一下**方案總管**中的方案，然後選取 [**加入** > **新增專案**]。

   1. 在 [**加入新專案**] 頁面的 [搜尋] 方塊中，輸入 [連結**庫**]。 從 [語言] 清單中選擇 [ **Visual Basic** ]，然後從 [平臺] 清單中選擇 [**所有平臺**]。 選擇 [**類別庫（.NET Standard）** ] 範本，然後選擇 **[下一步]** 。

   1. 在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入**StringLibrary** 。 接著，選擇 [建立]。

1. 請檢查並確定程式庫的目標是正確的 .NET Standard 版本。 以滑鼠右鍵按一下**方案總管**中的 [程式庫] 專案，然後選取 [**屬性**]。 [**目標 Framework** ] 文字方塊會顯示專案的目標為 .NET Standard 2.0。

   ![類別庫的專案屬性](./media/library-with-visual-studio/vb/library-project-properties.png)

1. 在 [**屬性**] 對話方塊中，清除 [**根命名空間**] 文字方塊中的文字。 針對每個專案，Visual Basic 會自動建立對應至專案名稱的命名空間。 在本教學課程中，您會使用程式碼檔案中的[`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md)關鍵字來定義最上層命名空間。

1. 以下列程式碼取代程式碼視窗中的程式碼，並儲存檔案：

   [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   類別庫（`UtilityLibraries.StringLibrary`）包含名為 `StartsWithUpper`的方法。 這個方法會傳回 <xref:System.Boolean> 值，指出目前的字串實例是否以大寫字元開頭。 Unicode 標準會區別大寫和小寫字元。 如果是大寫字元，<xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> 方法會傳回 `true`。

1. 在功能表列中，選取 [組建] >  [組建方案]。

---

   專案應該會編譯而不會發生錯誤。

## <a name="next-steps"></a>後續步驟

您已成功組建類別庫。 因為您尚未呼叫它的任何方法，所以它能否正常運作還不得而知。 開發程式庫的下一個步驟是測試它。

> [!div class="nextstepaction"]
> [建立單元測試專案](testing-library-with-visual-studio.md)
