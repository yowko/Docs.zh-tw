---
title: "在 Visual Studio 2017 中使用 C# 和 .NET Core 建置類別庫"
description: "了解如何使用 Visual Studio 2017 建置以 C# 撰寫的類別庫"
keywords: ".NET Core, .NET 標準類別庫, Visual Studio 2017"
author: stevehoag
ms.author: shoag
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: c849ca26-6a25-4d35-9544-f343af88e0e7
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 28fa60cdcf8e0056314af271208759eadd8503a5
ms.lasthandoff: 03/13/2017

---

# <a name="building-a-class-library-with-c-and-net-core-in-visual-studio-2017"></a>在 Visual Studio 2017 中使用 C# 和 .NET Core 建置類別庫 #

類別庫會定義可從任何應用程式呼叫的型別和方法。 使用 .NET Core 開發的類別庫支援 .NET 標準程式庫，其允許支援該 .NET 標準程式庫版本的任何 .NET 平台呼叫您的類別庫。 當您完成類別庫時，您可以決定要將它發佈為協力廠商元件，或要將它加入做為一個或多個應用程式隨附的元件。

> [!NOTE]
> 如需 .NET 標準版本與所支援平台的清單，請參閱 [.NET 標準程式庫](../../standard/library.md)。

在本主題中，我們將建立含有單一字串處理方法的簡單公用程式類別庫。 我們將它實作為[擴充方法](../../csharp/programming-guide/classes-and-structs/extension-methods.md)，讓它可以如同 @System.String 類別的成員一般來呼叫。

## <a name="creating-a-class-library-solution"></a>建立類別庫方案 ##

讓我們開始建立類別庫專案和其相關專案的方案。 Visual Studio 方案只能做為一個或多個專案的容器。 建立方案：

1. 在 Visual Studio 功能表列上，依序選擇 [檔案]****、[新增]****、[專案]****。

1. 在 [新專案]**** 對話方塊中，展開 [其他專案類型]**** 節點，然後選擇 [Visual Studio 方案]****，如下圖所示。

   ![Image](./media/solution.jpg)

1. 將方案命名為 "ClassLibraryProjects"，然後選擇 [確定]**** 按鈕。 其結果如下圖所示。

   ![Image](./media/vs_with_solution.jpg)

## <a name="creating-the-class-library-project"></a>建立類別庫專案 ##

現在我們可以建立類別庫專案︰

1. 在 [方案總管]**** 中，開啟 [ClassLibraryProject]**** 節點的操作功能表，然後依序選擇 [加入]****、[新增專案]****。

1. 在 [新增專案]**** 對話方塊中，展開 [.NET Core]**** 節點，然後選擇 [類別庫 (.NET 標準)]**** 專案範本。

1. 在 [名稱]**** 文字方塊中，輸入 "StringLibrary" 做為專案名稱，如下圖所示。

   ![Image](./media/lib_project.jpg)

1. 選擇 [確定]**** 以建立類別庫專案。 其結果如下圖所示。

   ![Image](./media/class_library.jpg)

1. 以下面程式碼取代程式碼視窗中的程式碼：

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs#1)]

   類別庫 `UtilityLibraries.StringLibrary` 包含一個名為 `StartsWithUpper` 的方法，它會傳回 @System.Boolean 值，指出目前的字串執行個體是否以大寫字元開頭。 哪些字元要為大寫是由 Unicode 標準所定義。 在 .NET Core 中，如果字元是大寫，[Char.IsUpper](xref:System.Char.IsUpper(System.Char)) 方法會傳回 `true`。

1. 在功能表列上，選擇 [建置] ****、[建置方案] ****。 專案應該會編譯而不會發生錯誤。

## <a name="the-next-step"></a>後續步驟 ##

到目前為止，我們已成功建置類別庫。 但因為我們尚未呼叫它的任何方法，所以它能否正常運作還不得而知。 開發程式庫的下一個步驟是使用 [C# 單元測試專案](testing-library-with-visual-studio.md)來加以測試。



