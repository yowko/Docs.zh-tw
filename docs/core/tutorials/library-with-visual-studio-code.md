---
title: 在 Visual Studio Code 中建立 .NET Standard 類別庫
description: 瞭解如何使用 Visual Studio Code 建立 .NET Standard 類別庫。
ms.date: 05/29/2020
ms.openlocfilehash: 5720ac374d50ef27a07d463e57af1bd95a352d83
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446948"
---
# <a name="tutorial-create-a-net-standard-library-in-visual-studio-code"></a>教學課程：在 Visual Studio Code 中建立 .NET Standard 程式庫

「類別庫」** 會定義應用程式所呼叫的類型和方法。 以 .NET Standard 2.0 為目標的類別庫，可讓任何支援該版本 .NET Standard 的 .NET 部署呼叫您的程式庫。 當您完成類別庫時，您可以決定是否要將它散發為 NuGet 套件，或將它包含在一或多個應用程式的配套元件中。

> [!NOTE]
> 如需所支援的 .NET Standard 版本和平臺清單，請參閱[.NET Standard](../../standard/net-standard.md)。

在本教學課程中，您會建立包含單一字串處理方法的簡單公用程式程式庫。 您可以將它實作為[擴充方法](../../csharp/programming-guide/classes-and-structs/extension-methods.md)，讓您可以如同類別的成員一樣呼叫它 <xref:System.String> 。

## <a name="prerequisites"></a>先決條件

1. 已安裝[c # 擴充](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)功能的[Visual Studio Code](https://code.visualstudio.com/) 。 如需有關如何在 Visual Studio Code 上安裝延伸模組的詳細資訊，請參閱[VS Code 延伸模組 Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery)。
2. [.Net Core 3.1 SDK 或更新版本](https://dotnet.microsoft.com/download)

## <a name="create-a-solution"></a>建立方案

一開始先建立一個空白的方案，將類別庫專案放入中。 解決方案會當做一個或多個專案的容器。 您會在相同的方案中加入其他相關的專案。

1. 開啟 Visual Studio Code。

1. **File**  >  從主功能表選取 [檔案] [**開啟資料夾**] / [**開啟 ...** ]，建立*ClassLibraryProjects*資料夾，然後按一下 [**選取資料夾**] [ / **開啟**]。

1. 從主功能表選取 [**查看**終端機]，以在 Visual Studio Code 中開啟**終端**機  >  **Terminal** 。

   **終端**機會在*ClassLibraryProjects*資料夾中以命令提示字元開啟。

1. 在**終端**機中，輸入下列命令：

   ```dotnetcli
   dotnet new sln
   ```

   終端機輸出如下列範例所示：

   ```
   The template "Solution File" was created successfully.
   ```

## <a name="create-a-class-library-project"></a>建立類別庫專案

將名為 "StringLibrary" 的新 .NET Standard 類別庫專案加入至方案。

1. 在終端機中，執行下列命令以建立程式庫專案：

   ```dotnetcli
   dotnet new classlib -o StringLibrary
   ```

   終端機輸出如下列範例所示：

   ```
   The template "Class library" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on StringLibrary\StringLibrary.csproj...
     Determining projects to restore...
     Restore completed in 328.13 ms for C:\Projects\ClassLibraryProjects\StringLibrary\StringLibrary.csproj.
   Restore succeeded.
   ```

1. 執行下列命令，將程式庫專案新增至方案：

   ```dotnetcli
   dotnet sln add StringLibrary/StringLibrary.csproj
   ```

   終端機輸出如下列範例所示：

   ```
   Project `StringLibrary\StringLibrary.csproj` added to the solution.
   ```

1. 請檢查並確定程式庫的目標是正確的 .NET Standard 版本。 在**Explorer**中，開啟*StringLibrary/StringLibrary*。

   `TargetFramework`元素會顯示專案的目標為 .NET Standard 2.0。

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>
       <TargetFramework>netstandard2.0</TargetFramework>
     </PropertyGroup>

   </Project>
   ```

1. 開啟*Class1.cs* ，並將程式碼取代為下列程式碼。

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

   類別庫 `UtilityLibraries.StringLibrary` 包含名為的方法 `StartsWithUpper` 。 這個方法會傳回 <xref:System.Boolean> 值，指出目前的字串實例是否以大寫字元開頭。 Unicode 標準會區別大寫和小寫字元。 如果是大寫字元，<xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> 方法會傳回 `true`。

1. 儲存檔案。

1. 執行下列命令來建立方案，並確認專案編譯無誤。

   ```dotnetcli
   dotnet build
   ```

   終端機輸出如下列範例所示：

   ```
   Microsoft (R) Build Engine version 16.6.0 for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.
     Determining projects to restore...
     All projects are up-to-date for restore.
     You are using a preview version of .NET Core. See: https://aka.ms/dotnet-core-preview
     StringLibrary -> C:\Projects\ClassLibraryProjects\StringLibrary\bin\Debug\netstandard2.0\StringLibrary.dll
   Build succeeded.
       0 Warning(s)
       0 Error(s)
   Time Elapsed 00:00:02.78
   ```

## <a name="add-a-console-app-to-the-solution"></a>將主控台應用程式新增至解決方案

新增使用類別庫的主控台應用程式。 應用程式會提示使用者輸入字串，並報告字串是否以大寫字元開頭。

1. 在終端機中，執行下列命令來建立主控台應用程式專案：

   ```dotnetcli
   dotnet new console -o ShowCase
   ```

   終端機輸出如下列範例所示：

   ```
   The template "Console Application" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on ShowCase\ShowCase.csproj...  
     Determining projects to restore...
     Restore completed in 210.78 ms for C:\Projects\ClassLibraryProjects\ShowCase\ShowCase.csproj.
   Restore succeeded.
   ```

1. 執行下列命令，將主控台應用程式專案新增至方案：

   ```dotnetcli
   dotnet sln add ShowCase/ShowCase.csproj
   ```

   終端機輸出如下列範例所示：

   ```
   Project `ShowCase\ShowCase.csproj` added to the solution.
   ```

1. 一開始，新的主控台應用程式專案無法存取類別庫。 若要讓它能夠呼叫類別庫中的方法，請執行下列命令來建立類別庫專案的專案參考：

   ```dotnetcli
   dotnet add ShowCase/Showcase.csproj reference StringLibrary/StringLibrary.csproj
   ```

   終端機輸出如下列範例所示：

   ```
   Reference `..\StringLibrary\StringLibrary.csproj` added to the project.
   ```

1. 開啟 [*展示/程式 .cs* ]，並將所有程式碼取代為下列程式碼。

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   該程式碼會使用 `row` 變數來維護寫入至主控台視窗的資料列數目計數。 當它大於或等於25時，程式碼就會清除主控台視窗，並向使用者顯示訊息。

   此程式會提示使用者輸入字串。 它會指出該字串開頭是否為大寫字元。 如果使用者在未輸入字串的情況下按 Enter 鍵，應用程式就會結束，而且主控台視窗會關閉。

1. 儲存您的變更。

1. 執行程式。

   ```dotnetcli
   dotnet run --project ShowCase/ShowCase.csproj
   ```

1. 輸入字串並按<kbd>enter</kbd>鍵以嘗試程式，然後按<kbd>enter</kbd>結束。

   終端機輸出如下列範例所示：

   ```
   Press <Enter> only to exit; otherwise, enter a string and press <Enter>:

   A string that starts with an uppercase letter
   Input: A string that starts with an uppercase letter
   Begins with uppercase? : Yes

   A string that starts with a lowercase letter
   Input: A string that starts with a lowercase letter
   Begins with uppercase? : Yes
   ```

## <a name="additional-resources"></a>其他資源

* [使用 .NET Core CLI 開發程式庫](libraries.md)

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已建立解決方案、新增程式庫專案，以及加入使用該程式庫的主控台應用程式專案。 在下一個教學課程中，您會將單元測試專案加入至方案。

> [!div class="nextstepaction"]
> [在 Visual Studio Code 中使用 .NET Core 測試 .NET Standard 程式庫](testing-library-with-visual-studio-code.md)
