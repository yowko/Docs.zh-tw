---
title: 在 Visual Studio 2017 中建置 Visual Basic .NET Core 類別庫
description: 了解如何使用 Visual Studio 2017 建置以 Visual Basic 撰寫的 .NET Core 類別庫
author: rpetrusha
ms.author: ronpet
ms.date: 08/07/2017
dev_langs:
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: fa1387eba60b4bf181df254e00bb3fdbe55bdaf6
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144698"
---
# <a name="build-a-class-library-with-visual-basic-and-the-net-core-sdk-in-visual-studio-2017"></a>在 Visual Studio 2017 中使用 Visual Basic 和 .NET Core SDK 來建置類別庫

「類別庫」會定義應用程式所呼叫的類型和方法。 以 .NET Standard 2.0 為目標的類別庫，允許支援該 .NET Standard 版本的任何 .NET 實作呼叫您的類別庫。 當您完成類別庫時，您可以決定要將它散發為協力廠商元件，還是要將它併入作為一或多個應用程式隨附的元件。

> [!NOTE]
> 如需 .NET 標準版本與所支援平台的清單，請參閱 [.NET 標準](../../standard/net-standard.md)。

在本主題中，您將建立含有單一字串處理方法的簡單公用程式類別庫。 您將它實作為[擴充方法](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)，以便可以如同 <xref:System.String> 類別的成員一般來進行呼叫。

## <a name="creating-a-class-library-solution"></a>建立類別庫方案

請開始建立類別庫專案和其相關專案的方案。 Visual Studio 方案只能做為一個或多個專案的容器。 建立方案：

1. 在 Visual Studio 功能表列上，選擇 [檔案]  >  [新增]   >  [專案]。

1. 在 **[新增專案]** 對話方塊中，展開 **[其他專案類型]** 節點，並選取 **[Visual Studio 方案]**。 將方案命名為 "ClassLibraryProjects"，然後選取 [確定] 按鈕。

   ![[新增專案] 對話方塊](./media/library-with-visual-studio/newproject.png)

## <a name="creating-the-class-library-project"></a>建立類別庫專案

建立您的類別庫專案：

1. 在 **方案總管** 中，以滑鼠右鍵按一下 **ClassLibraryProjects** 方案檔，然後從內容功能表中，選取 **[新增]** > **[新增專案]**。

1. 在 [新增專案] 對話方塊中，展開 [Visual Basic] 節點，然後選取後面跟著 [類別庫 (.NET Standard)] 專案範本的 [.NET Standard] 節點。 在 [名稱] 文字方塊中，輸入 "StringLibrary" 作為專案名稱。 選取 [確定] 以建立類別庫專案。

   ![[新增專案] 對話方塊](./media/vb-library-with-visual-studio/libproject.png)

   然後在 Visual Studio 開發環境中開啟程式碼視窗。 
 
   ![Visual Studio 應用程式視窗顯示預設的類別庫範本程式碼](./media/vb-library-with-visual-studio/stringlibrary.png)

1. 請檢查以確定程式庫以正確的 .NET Standard 版本為目標。 在**方案總管**視窗中，以滑鼠右鍵按一下程式庫專案，然後選取 [屬性]。 [目標 Framework] 文字方塊顯示我們的目標是 .NET Standard 2.0。

   ![類別庫的專案屬性](./media/library-with-visual-studio/properties.png)

1. 此外，在 [屬性] 對話方塊中，清除 [根命名空間] 文字方塊中的文字。 Visual Basic 會自動為每個專案建立對應專案名稱的命名空間，而在原始程式碼檔案中定義的任何命名空間都是該命名空間的父代。 我們想要使用 [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) 關鍵字定義最上層命名空間。
  
1. 以下列程式碼取代程式碼視窗中的程式碼，並儲存檔案：

  [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   類別庫 `UtilityLibraries.StringLibrary` 包含一個名為 `StartsWithUpper` 的方法，它會傳回 <xref:System.Boolean> 值，指出目前的字串執行個體是否以大寫字元開頭。 Unicode 標準會區別大寫和小寫字元。 如果是大寫字元，<xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> 方法會傳回 `true`。

1. 在功能表列中，選取 [組建]  >  [組建方案]。 專案應該會編譯而不會發生錯誤。

   ![輸出窗格顯示組建成功](./media/library-with-visual-studio/buildsucceeds.png)



## <a name="next-step"></a>後續步驟

您已成功組建類別庫。 因為您尚未呼叫它的任何方法，所以它能否正常運作還不得而知。 開發程式庫的下一個步驟是使用[單元測試專案](testing-library-with-visual-studio.md)來測試它。
