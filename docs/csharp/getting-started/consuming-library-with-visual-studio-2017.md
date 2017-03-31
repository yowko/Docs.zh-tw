---
title: "在 Visual Studio 2017 中透過 .NET Core 使用類別庫"
description: "了解如何使用 Visual Studio 2017 來呼叫類別庫中的成員"
keywords: ".NET Core, .NET Core 類別庫, .NET Standard, .NET Standard 類別庫散發"
author: stevehoag
ms.author: shoag
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: d7b94076-1108-4174-94e7-a18f00072bb7
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 0b42eeb0149feec09ddacba98383da3abd53bb5e
ms.lasthandoff: 03/13/2017

---

# <a name="consuming-a-class-library-with-net-core-in-visual-studio-2017"></a>在 Visual Studio 2017 中透過 .NET Core 使用類別庫 #

在您依照[在 Visual Studio 2017 中使用 .NET Core 來建置 C# 類別庫 (英文)](./library-with-visual-studio-2017.md) 和[在 Visual Studio 2017 中使用 .NET Core 來測試類別庫 (英文)](testing-library-with-visual-studio.md) 中的步驟操作來建置和測試您的類別庫，並且也已建置該類別庫的發行版本之後，下一個步驟就是讓它可供呼叫端使用。 執行這項作業的方法有兩種：

- 如果該類別庫將供單一方案使用 (例如，如果它是單一大型應用程式中的元件)，您可以直接將它以專案的形式包含在您的方案中。

- 如果該類別庫將可供一般存取，則可藉由 NuGet 套件的形式來散發它。

## <a name="including-a-library-as-a-project-in-a-solution"></a>將類別庫以專案形式包含在方案中 ##

就像我們將單元測試包含在與類別庫相同的方案中一樣，我們也可以將應用程式包含在方案中。 例如，讓我們在提示使用者輸入字串並回報其第一個字元是否是大寫的主控台應用程式中，使用我們的類別庫：

1. 開啟在[在 Visual Studio 2017 中使用 .NET Core 來建置 C# 類別庫 (英文)](./library-with-visual-studio-2017.md) 主題中建立的 `ClassLibraryProjects` 方案，然後在 [方案總管] 中，開啟 [ClassLibraryProjects]**** 節點的操作功能表，並選擇 [新增]**** > [新增專案]****。

1. 在 [新增專案]**** 對話方塊中，展開 [Visual C#]**** 和 [.NET Core]**** 節點，然後選擇 [主控台應用程式 (.NET Core)]**** 專案範本，如下圖所示。

   ![Image](./media/use-library.jpg)

1. 在 [名稱]**** 文字方塊中，輸入 `ShowCase`，然後選擇 [確定]**** 按鈕。

1. 在 [方案總管] 中，開啟 [ShowCase]**** 專案節點的操作功能表，然後選擇 [設定為啟始專案]****。

1. 一開始，我們的專案並無法存取類別庫。 若要讓它呼叫類別庫中的方法，請在 [方案總管]**** 中，開啟 [ShowCase]**** 專案中 [相依性]**** 節點的操作功能表，然後選擇 [加入參考]****。

1. 在 [參考管理員]**** 對話方塊中，如下圖所示，選擇 [StringLibrary]**** (我們的類別庫專案)，然後選擇 [確定]**** 按鈕。

   ![Image](./media/add-lib-ref.jpg)

1. 在 'program.cs' 檔案的程式碼視窗中，以下列程式碼取代所有程式碼：

 [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs#1)]

   此程式碼會使用 [Console.WindowHeight](xref:System.Console.WindowHeight) 屬性來判斷主控台視窗有多少資料列。 每當 [Console.CursorTop](xref:System.Console.CursorTop) 屬性大於或等於主控台視窗中的資料列總數時，程式碼都會清除主控台視窗並對使用者重新顯示訊息。

   此程式本身會直接提示使用者輸入字串。 接著，它會指出該字串開頭是否為大寫字元。 如果使用者沒有輸入字串就按 **Enter** 鍵，主控台視窗就會關閉且應用程式會終止。

1. 必要時，變更工具列以編譯 `ShowCase` 專案的 [偵錯]**** 版本，如下圖所示。

   ![Image](./media/showcase-toolbar.jpg)

1. 按一下 [ShowCase]**** 按鈕上的綠色箭號，以編譯並執行程式。

接著，您便可以依照[使用 Visual Studio 2017 針對您的 C# Hello World 應用程式進行偵錯 (英文)](debugging-with-visual-studio-2017.md) 和[使用 Visual Studio 2017 來發佈您的 Hello World 應用程式 (英文)](publishing-with-visual-studio-2017.md) 中所列的步驟操作，對使用此類別庫的應用程式進行偵錯並在最後將它發佈。

## <a name="distributing-the-library-in-a-nuget-package"></a>以 NuGet 套件散發類別庫 ##

您可以藉由 NuGet 套件的形式散發類別庫，讓您的類別庫可供更廣泛地使用。 Visual Studio 不支援建立 NuGet 套件。 若要建立該套件，您需使用 [`dotnet.exe` 命令列公用程式](../../core/tools/dotnet.md)，如下所示：

1. 開啟主控台視窗。 例如，在 Windows 工具列的 [請隨意提出問題]**** 文字方塊中輸入 `Command Prompt`，然後選擇 [命令提示字元]**** 傳統型應用程式來開啟主控台視窗。

1. 瀏覽至您類別庫的專案目錄。 通常，除非您已重新設定檔案位置，否則它會位於 `Documents\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary` 目錄中。 此目錄包含您的原始程式碼和專案檔 `StringLibrary.csproj`。

1. 發出命令 `dotnet.exe pack --no-build`。 `dotnet.exe` 公用程式會產生一個副檔名為 .nupkg 的套件。

   > [!TIP]
   > 如果包含 `dotnet.exe` 的目錄不在您的路徑中，則您可以在主控台視窗中輸入 `where dotnet.exe` 來尋找其位置。

如需有關建立 NuGet 套件的詳細資訊，請參閱[如何使用跨平台工具建立 NuGet 套件](../../core/deploying/creating-nuget-packages.md)。
