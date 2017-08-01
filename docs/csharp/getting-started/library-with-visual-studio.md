---
title: "在 Visual Studio 2017 中使用 C# 和 .NET Core 建置類別庫"
description: "了解如何使用 Visual Studio 2017 建置以 C# 撰寫的類別庫"
keywords: ".NET Core, .NET 標準類別庫, Visual Studio 2017"
author: BillWagner
ms.author: wiwagn
ms.date: 04/17/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: c849ca26-6a25-4d35-9544-f343af88e0e7
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 709b05dc9baeae1e99481a37287b91730b395f63
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---

# <a name="building-a-class-library-with-c-and-net-core-in-visual-studio-2017"></a>在 Visual Studio 2017 中使用 C# 和 .NET Core 建置類別庫

「類別庫」會定義應用程式所呼叫的類型和方法。 使用 .NET Core 開發的類別庫支援 .NET Standard，其允許支援該 .NET Standard 版本的任何 .NET 平台呼叫您的類別庫。 當您完成類別庫時，您可以決定要將它散發為協力廠商元件，還是要將它併入作為一或多個應用程式隨附的元件。

> [!NOTE]
> 如需 .NET 標準版本與所支援平台的清單，請參閱 [.NET 標準](../../standard/net-standard.md)。

在本主題中，您將建立含有單一字串處理方法的簡單公用程式類別庫。 您將它實作為[擴充方法](../../csharp/programming-guide/classes-and-structs/extension-methods.md)，以便可以如同 @System.String 類別的成員一般來進行呼叫。

## <a name="creating-a-class-library-solution"></a>建立類別庫方案

請開始建立類別庫專案和其相關專案的方案。 Visual Studio 方案只能做為一個或多個專案的容器。 建立方案：

1. 在 Visual Studio 功能表列上，選擇 [檔案]  >  [新增]   >  [專案]。

1. 在 [新增專案] 對話方塊中，展開 [其他專案類型] 節點，並選取 [Visual Studio 方案]。 將方案命名為 "ClassLibraryProjects"，然後選取 [確定] 按鈕。

   ![[新增專案] 對話方塊](./media/library-with-visual-studio/newproject.png)

## <a name="creating-the-class-library-project"></a>建立類別庫專案

建立您的類別庫專案：

1. 在方案總管  中，以滑鼠右鍵按一下 **ClassLibraryProjects** 方案檔，然後從內容功能表中，選取 [新增]  >  [新增專案]。

1. 在 [新增專案] 對話方塊中，選取 [.NET Core] 節點，接著選取 [類別庫 (.NET Core)] 專案範本。 在 [名稱] 文字方塊中，輸入 "StringLibrary" 作為專案名稱。 選取 [確定] 以建立類別庫專案。

   ![[新增專案] 對話方塊](./media/library-with-visual-studio/libproject.png)

   ![Visual Studio 應用程式視窗顯示預設的類別庫範本程式碼](./media/library-with-visual-studio/stringlibrary.png)

1. 以下列程式碼取代程式碼視窗中的程式碼，並儲存檔案：

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs#1)]

   類別庫 `UtilityLibraries.StringLibrary` 包含一個名為 `StartsWithUpper` 的方法，它會傳回 @System.Boolean 值，指出目前的字串執行個體是否以大寫字元開頭。 Unicode 標準會區別大寫和小寫字元。 在 .NET Core 中，如果字元是大寫，[`Char.IsUpper`](xref:System.Char.IsUpper(System.Char)) 方法會傳回 `true`。

1. 在功能表列中，選取 [組建]  >  [組建方案]。 專案應該會編譯而不會發生錯誤。

   ![輸出窗格顯示組建成功](./media/library-with-visual-studio/buildsucceeds.png)

## <a name="next-step"></a>後續步驟

您已成功組建類別庫。 因為您尚未呼叫它的任何方法，所以它能否正常運作還不得而知。 開發類別庫的下一個步驟是使用 [C# 單元測試專案](testing-library-with-visual-studio.md)來加以測試。

