---
title: 使用 Visual Studio Code 建立 .NET 類別庫
description: 瞭解如何使用 Visual Studio Code 建立 .NET 類別庫。
ms.date: 11/18/2020
ms.openlocfilehash: 4daa077fc54da3de2f808d831e06ee5f9bb3bde7
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94916087"
---
# <a name="tutorial-create-a-net-class-library-using-visual-studio-code"></a>教學課程：使用 Visual Studio Code 建立 .NET 類別庫

在本教學課程中，您會建立包含單一字串處理方法的簡單公用程式程式庫。

「類別庫」會定義應用程式所呼叫的類型和方法。 如果程式庫以 .NET Standard 2.0 為目標，則可以由任何 .NET 執行 (，包括支援 .NET Standard 2.0 的 .NET Framework) 。 如果程式庫以 .NET 5 為目標，則可由任何目標為 .NET 5 的應用程式呼叫。 本教學課程說明如何以 .NET 5 為目標。

當您建立類別庫時，可以將它散發為協力廠商元件，或做為配套的元件，以及一或多個應用程式。

## <a name="prerequisites"></a>先決條件

1. 已安裝[c # 擴充](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)功能的[Visual Studio Code](https://code.visualstudio.com/) 。 如需有關如何在 Visual Studio Code 上安裝擴充功能的詳細資訊，請參閱 [VS Code 擴充功能 Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery)。
2. [.Net 5.0 SDK 或更新版本](https://dotnet.microsoft.com/download)

## <a name="create-a-solution"></a>建立方案

首先，建立空白的方案，將類別庫專案放置在中。 方案可作為一或多個專案的容器。 您會將其他相關的專案新增至相同的方案。

1. 啟動 Visual Studio Code。

1. **File**  >  從主功能表選取 [macOS) 上的 [開啟 **資料夾**] (**開啟 ...**

1. 在 [ **開啟資料夾** ] 對話方塊中，建立 *>classlibraryprojects* 資料夾，然後按一下 [ **選取資料夾** (在 macOS) **開啟** ]。

1. 從主功能表中選取 [ **View** terminal]，以在 Visual Studio Code 中開啟 **終端** 機  >  **Terminal** 。

   **終端** 機會在 *>classlibraryprojects* 資料夾中使用命令提示字元開啟。

1. 在 **終端** 機中，輸入下列命令：

   ```dotnetcli
   dotnet new sln
   ```

   終端機輸出如下列範例所示：

   ```output
   The template "Solution File" was created successfully.
   ```

## <a name="create-a-class-library-project"></a>建立類別庫專案

將名為 "StringLibrary" 的新 .NET 類別庫專案加入至方案。

1. 在終端機中執行下列命令，以建立程式庫專案：

   ```dotnetcli
   dotnet new classlib -o StringLibrary
   ```

   `-o`或 `--output` 命令指定要放置所產生輸出的位置。

   終端機輸出如下列範例所示：

   ```output
   The template "Class library" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on StringLibrary\StringLibrary.csproj...
     Determining projects to restore...
     Restored C:\Projects\ClassLibraryProjects\StringLibrary\StringLibrary.csproj (in 328 ms).
   Restore succeeded.
   ```

1. 執行下列命令，以將程式庫專案新增至方案：

   ```dotnetcli
   dotnet sln add StringLibrary/StringLibrary.csproj
   ```

   終端機輸出如下列範例所示：

   ```output
   Project `StringLibrary\StringLibrary.csproj` added to the solution.
   ```

1. 請檢查以確定程式庫以 .NET 5 為目標。 在 [ **Explorer**] 中，開啟 [ *StringLibrary]/[StringLibrary*]。

   `TargetFramework`元素會顯示專案的目標為 .net 5.0。

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>
       <TargetFramework>net5.0</TargetFramework>
     </PropertyGroup>

   </Project>
   ```

1. 開啟 *Class1.cs* ，並將程式碼取代為下列程式碼。

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

   類別庫（class library） `UtilityLibraries.StringLibrary` 包含名為的方法 `StartsWithUpper` 。 這個方法會傳回 <xref:System.Boolean> 值，指出目前字串實例的開頭是否為大寫字元。 Unicode 標準會區別大寫和小寫字元。 如果是大寫字元，<xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> 方法會傳回 `true`。

1. 儲存檔案。

1. 執行下列命令以建立方案，並確認專案編譯時沒有錯誤。

   ```dotnetcli
   dotnet build
   ```

   終端機輸出如下列範例所示：

   ```output
   Microsoft (R) Build Engine version 16.7.0+b89cb5fde for .NET
   Copyright (C) Microsoft Corporation. All rights reserved.
     Determining projects to restore...
     All projects are up-to-date for restore.
     StringLibrary -> C:\Projects\ClassLibraryProjects\StringLibrary\bin\Debug\net5.0\StringLibrary.dll
   Build succeeded.
       0 Warning(s)
       0 Error(s)
   Time Elapsed 00:00:02.78
   ```

## <a name="add-a-console-app-to-the-solution"></a>將主控台應用程式新增至解決方案

加入使用類別庫的主控台應用程式。 應用程式會提示使用者輸入字串，並報告字串是否以大寫字元開頭。

1. 在終端機中執行下列命令，以建立主控台應用程式專案：

   ```dotnetcli
   dotnet new console -o ShowCase
   ```

   終端機輸出如下列範例所示：

   ```output
   The template "Console Application" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on ShowCase\ShowCase.csproj...  
     Determining projects to restore...
     Restored C:\Projects\ClassLibraryProjects\ShowCase\ShowCase.csproj (in 210 ms).
   Restore succeeded.
   ```

1. 執行下列命令，以將主控台應用程式專案新增至方案：

   ```dotnetcli
   dotnet sln add ShowCase/ShowCase.csproj
   ```

   終端機輸出如下列範例所示：

   ```output
   Project `ShowCase\ShowCase.csproj` added to the solution.
   ```

1. 開啟 [ *展示]/[Program* ]，並將所有程式碼取代為下列程式碼。

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   該程式碼會使用 `row` 變數來維護寫入至主控台視窗的資料列數目計數。 只要超過或等於25，程式碼就會清除主控台視窗，並向使用者顯示訊息。

   此程式會提示使用者輸入字串。 它會指出該字串開頭是否為大寫字元。 如果使用者按下 <kbd>Enter</kbd> 鍵但未輸入字串，則應用程式會結束，且主控台視窗會關閉。

1. 儲存您的變更。

## <a name="add-a-project-reference"></a>新增專案參考

一開始，新的主控台應用程式專案沒有類別庫的存取權。 若要允許它呼叫類別庫中的方法，請建立類別庫專案的專案參考。

1. 執行下列命令：

   ```dotnetcli
   dotnet add ShowCase/ShowCase.csproj reference StringLibrary/StringLibrary.csproj
   ```

   終端機輸出如下列範例所示：

   ```output
   Reference `..\StringLibrary\StringLibrary.csproj` added to the project.
   ```

## <a name="run-the-app"></a>執行應用程式

1. 在終端中執行下列命令：

   ```dotnetcli
   dotnet run --project ShowCase/ShowCase.csproj
   ```

1. 輸入字串並按 <kbd>enter</kbd>鍵以嘗試程式，然後按 <kbd>enter</kbd> 鍵結束。

   終端機輸出如下列範例所示：

   ```output
   Press <Enter> only to exit; otherwise, enter a string and press <Enter>:

   A string that starts with an uppercase letter
   Input: A string that starts with an uppercase letter
   Begins with uppercase? : Yes

   a string that starts with a lowercase letter
   Input: a string that starts with a lowercase letter
   Begins with uppercase? : No
   ```

## <a name="additional-resources"></a>其他資源

* [使用 .NET CLI 開發程式庫](libraries.md)

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已建立解決方案、新增程式庫專案，並加入使用該程式庫的主控台應用程式專案。 在下一個教學課程中，您會將單元測試專案加入至方案。

> [!div class="nextstepaction"]
> [使用 Visual Studio Code 以 .NET 測試 .NET 類別庫](testing-library-with-visual-studio-code.md)
