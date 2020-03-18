---
title: 在視覺化工作室中構建 .NET 標準類庫
description: 瞭解如何使用 Visual Studio 構建以 C# 或視覺化基本編寫的 .NET 標準類庫
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 748a1499e0c3a4a41613a69b715dbcfbd585bfe3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714012"
---
# <a name="build-a-net-standard-library-in-visual-studio"></a>在視覺化工作室中構建 .NET 標準庫

「類別庫」** 會定義應用程式所呼叫的類型和方法。 以 .NET 標準 2.0 為目標的類庫允許支援 .NET 標準版本的任何 .NET 實現調用庫。 當您完成類別庫時，您可以決定要將它散發為協力廠商元件，還是要將它併入作為一或多個應用程式隨附的元件。

> [!NOTE]
> 有關 .NET 標準版本及其支援的平臺的清單，請參閱[.NET 標準](../../standard/net-standard.md)。

在本主題中，您將建立含有單一字串處理方法的簡單公用程式類別庫。 您將它實作為[擴充方法](../../csharp/programming-guide/classes-and-structs/extension-methods.md)，以便可以如同 <xref:System.String> 類別的成員一般來進行呼叫。

## <a name="create-a-visual-studio-solution"></a>創建視覺化工作室解決方案

首先創建一個空白解決方案來放入類庫專案。 Visual Studio 解決方案用作一個或多個專案的容器。 如果繼續教程系列，您將向同一解決方案添加其他相關專案。

要創建空白解決方案，

1. 開啟 Visual Studio。

2. 在啟動視窗中，選擇 **"創建新專案**"。

3. 在"**創建新專案**"頁上，在搜索框中輸入**解決方案**。 選擇 **"空白解決方案"** 範本，然後選擇 **"下一步**"。

   ![Visual Studio 中的空白方案範本](media/library-with-visual-studio/blank-solution.png)

4. 在"**配置新專案**"頁上，在 **"專案名稱**"框中輸入**類庫專案**。 然後，選擇 **"創建**"。

> [!TIP]
> 您還可以跳過此步驟，讓 Visual Studio 在下一步中創建專案時為您創建解決方案。 在 **"配置新專案**"頁上查找解決方案選項。

## <a name="create-a-class-library-project"></a>建立類別庫專案

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C#](#tab/csharp)

1. 向解決方案添加新的 C# .NET 標準類庫專案，稱為"StringLibrary"。

   1. 按右鍵**解決方案資源管理器**中的解決方案，然後選擇"**添加新** > **專案**"。

   1. 在"**添加新專案**"頁上，在搜索框中輸入**庫**。 從"語言"清單中選擇**C#，** 然後從"平臺"清單中選擇 **"所有平臺**"。 選擇**類庫 （.NET 標準）** 範本，然後選擇 **"下一步**"。

   1. 在"**配置新專案**"頁上，在 **"專案名稱**"框中輸入**字串庫**。 然後，選擇 **"創建**"。

1. 檢查以確保庫面向正確的版本 .NET 標準。 按右鍵**解決方案資源管理器**中的庫專案，然後選擇**屬性**。 "**目標框架**"文字方塊顯示專案目標 .NET 標準 2.0。

   ![類別庫的專案屬性](./media/library-with-visual-studio/library-project-properties.png)

1. 以下列程式碼取代程式碼視窗中的程式碼，並儲存檔案：

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   類庫`UtilityLibraries.StringLibrary`包含名為 的方法`StartsWithUpper`。 此方法返回指示<xref:System.Boolean>當前字串實例是否以大寫字元開頭的值。 Unicode 標準會區別大寫和小寫字元。 如果是大寫字元，<xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> 方法會傳回 `true`。

1. 在功能表列上，選擇 **"生成** > **解決方案**"。

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. 向解決方案添加新的 Visual Basic .NET 標準類庫專案，該專案名為"StringLibrary"。

   1. 按右鍵**解決方案資源管理器**中的解決方案，然後選擇"**添加新** > **專案**"。

   1. 在"**添加新專案**"頁上，在搜索框中輸入**庫**。 從"語言"清單中選擇 **"視覺化基礎知識**"，然後從"平臺"清單中選擇 **"所有平臺**"。 選擇**類庫 （.NET 標準）** 範本，然後選擇 **"下一步**"。

   1. 在"**配置新專案**"頁上，在 **"專案名稱**"框中輸入**字串庫**。 然後，選擇 **"創建**"。

1. 檢查以確保庫面向正確的版本 .NET 標準。 按右鍵**解決方案資源管理器**中的庫專案，然後選擇**屬性**。 "**目標框架**"文字方塊顯示專案目標 .NET 標準 2.0。

   ![類別庫的專案屬性](./media/library-with-visual-studio/vb/library-project-properties.png)

1. 在"**屬性"** 對話方塊中，清除 **"根命名空間**"文字方塊中的文本。 對於每個專案，Visual Basic 會自動創建對應于專案名稱的命名空間。 在本教程中，通過使用代碼檔中的[`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md)關鍵字定義頂級命名空間。

1. 以下列程式碼取代程式碼視窗中的程式碼，並儲存檔案：

   [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   類庫`UtilityLibraries.StringLibrary`包含名為 的方法`StartsWithUpper`。 此方法返回指示<xref:System.Boolean>當前字串實例是否以大寫字元開頭的值。 Unicode 標準會區別大寫和小寫字元。 如果是大寫字元，<xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> 方法會傳回 `true`。

1. 在功能表列上，選擇 **"生成** > **解決方案**"。

---

   專案應該會編譯而不會發生錯誤。

## <a name="next-steps"></a>後續步驟

您已成功組建類別庫。 因為您尚未呼叫它的任何方法，所以它能否正常運作還不得而知。 開發庫的下一步是對其進行測試。

> [!div class="nextstepaction"]
> [創建單元測試專案](testing-library-with-visual-studio.md)
