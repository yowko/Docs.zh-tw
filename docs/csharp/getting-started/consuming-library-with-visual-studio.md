---
title: "在 Visual Studio 2017 中使用 .NET Core 使用類別庫 | Microsoft Docs"
description: "了解如何使用 Visual Studio 2017 來呼叫類別庫中的成員。"
keywords: ".NET Core, .NET Core 類別庫, .NET Standard, .NET Standard 類別庫散發"
author: BillWagner
ms.author: wiwang
ms.date: 04/17/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: d7b94076-1108-4174-94e7-a18f00072bb7
ms.translationtype: Human Translation
ms.sourcegitcommit: 4437ce5d344cf06d30e31911def6287999fc6ffc
ms.openlocfilehash: 5ad07e4116c75eb9b9d513c2a4fe43dfe62660d5
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017

---

# 在 Visual Studio 2017 中透過 .NET Core 使用類別庫
<a id="consuming-a-class-library-with-net-core-in-visual-studio-2017" class="xliff"></a>

在您遵循[在 Visual Studio 2017 中使用 .NET Core 組置 C# 類別庫](./library-with-visual-studio.md)和[在 Visual Studio 2017 中使用 .NET Core 測試類別庫](testing-library-with-visual-studio.md)中的步驟操作來組置和測試您的類別庫，並且也已組置該類別庫的發行版本之後，下一個步驟就是讓它可供呼叫端使用。 執行這項作業的方法有兩種：

* 如果該類別庫將供單一方案使用 (例如，如果它是單一大型應用程式中的元件)，您可以直接將它以專案的形式包含在您的方案中。

* 如果該類別庫將可供一般存取，則可藉由 NuGet 套件的形式來散發它。

## 將類別庫以專案形式包含在方案中
<a id="including-a-library-as-a-project-in-a-solution" class="xliff"></a>

就像您將單元測試包含在與類別庫相同的方案中一樣，您也可以將應用程式包含在該方案中。 例如，您可以在提示使用者輸入字串並回報其第一個字元是否為大寫的主控台應用程式中，使用您的類別庫：

1. 開啟您[在 Visual Studio 2017 中使用 .NET Core 組置 C# 類別庫](./library-with-visual-studio.md)主題中建立的 `ClassLibraryProjects` 方案。 在方案總管 中，以滑鼠右鍵按一下 **ClassLibraryProjects** 方案，然後從內容功能表中，選取 [新增]  >  [新增專案]。

1. 在 [新增專案] 對話方塊中，選取 [.NET Core] 節點，接著選取 [主控台應用程式 (.NET Core)] 專案範本。 在 [名稱] 文字方塊中，輸入 "ShowCase"，然後選取 [確定] 按鈕。

   ![[新增專案] 對話方塊](./media/consuming-library-with-visual-studio/addnewproject.png)

1. 在方案總管 中，以滑鼠右鍵按一下 **ShowCase** 專案，然後在內容功能表中選取 [設定為啟始專案]。

   ![ShowCase 內容功能表](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. 一開始，您的專案並無法存取類別庫。 若要讓它在您的類別庫中呼叫方法，您可以建立類別庫的參考。 在方案總管 中，以滑鼠右鍵按一下 `ShowCase` 專案的 [相依性] 節點，然後選取 [新增參考]。

   ![ShowCase 相依性內容功能表](./media/consuming-library-with-visual-studio/addreference.png)

1. 在 [參考管理員] 對話方塊中，選取**StringLibrary**、您的類別庫專案，然後選取 [確定] 按鈕。

   ![參考管理員](./media/consuming-library-with-visual-studio/referencemanager.png)

1. 在 *Program.cs* 檔案的程式碼視窗中，以下列程式碼取代所有程式碼：

 [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs#1)]

   此程式碼會使用 [Console.WindowHeight](xref:System.Console.WindowHeight) 屬性來判斷主控台視窗有多少資料列。 每當 [Console.CursorTop](xref:System.Console.CursorTop) 屬性大於或等於主控台視窗中的資料列數目時，程式碼都會清除主控台視窗並向使用者顯示訊息。

   此程式會提示使用者輸入字串。 它會指出該字串開頭是否為大寫字元。 如果使用者沒有輸入字串就按 Enter 鍵，應用程式就會終止且主控台視窗會關閉。

1. 必要時，變更工具列以編譯 `ShowCase` 專案的 [偵錯] 版本。 選取 **ShowCase** 按鈕上的綠色箭號，以編譯並執行程式。

   ![Image](./media/consuming-library-with-visual-studio/toolbar.png)

您可以遵循[使用 Visual Studio 2017 針對 C# Hello World 應用程式進行偵錯](debugging-with-visual-studio.md)和[使用 Visual Studio 2017 發行 Hello World 應用程式](publishing-with-visual-studio.md)中的步驟操作，對使用此類別庫的應用程式進行偵錯並加以發行。

## 以 NuGet 套件散發類別庫
<a id="distributing-the-library-in-a-nuget-package" class="xliff"></a>

您可以藉由 NuGet 套件的形式發行類別庫，讓您的類別庫可供廣泛使用。 Visual Studio 不支援建立 NuGet 套件。 若要建立該套件，您需使用 [`dotnet` 命令列公用程式](../../core/tools/dotnet.md)：

1. 開啟主控台視窗。 例如，在 Windows 工作列的 [請隨意提出問題] 文字方塊中，輸入`Command Prompt` (或 `cmd` 簡稱)，然後選取 [命令提示字元] 桌面應用程式，或按 Enter 鍵 (如果已在搜尋結果中選取該應用程式) 來開啟主控台視窗。

1. 瀏覽至您類別庫的專案目錄。 除非您已重新設定一般檔案位置，否則該位置會是 *Documents\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary* 目錄。 此目錄包含您的原始程式碼和專案檔 *StringLibrary.csproj*。

1. 發出命令 `dotnet pack --no-build`。 `dotnet` 公用程式會產生一個副檔名為 *.nupkg* 的套件。

   > [!TIP]
   > 如果包含 *dotnet.exe* 的目錄不在您的 PATH 中，則您可以在主控台視窗中輸入 `where dotnet.exe` 來尋找其位置。

如需有關建立 NuGet 套件的詳細資訊，請參閱[如何使用跨平台工具建立 NuGet 套件](../../core/deploying/creating-nuget-packages.md)。

