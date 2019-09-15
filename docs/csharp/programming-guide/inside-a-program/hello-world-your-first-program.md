---
title: Hello World--在 Windows 或 Mac 上使用 Visual Studio 的第一個C#程式-程式設計指南
ms.custom: seodec18
ms.date: 09/12/2019
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 0807e46d36a4cf031bc44ae0dc4efab79dd51d03
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991334"
---
# <a name="hello-world----your-first-program"></a>Hello World--您的第一個程式

在本文中，您將使用 Visual Studio 來建立傳統的「Hello World！」 程式。 Visual Studio 是一種專業整合式開發環境（IDE），具有專為 .NET 開發所設計的許多功能。 您只會使用 Visual Studio 中的幾項功能來建立此程式。 若要深入瞭解 Visual Studio，請參閱[使用 Visual C#和 Visual Basic 消費者入門](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)。

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="create-a-new-application"></a>建立新的應用程式

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

啟動 Visual Studio。 您會在 Windows 上看到下列影像：

![Visual Studio Windows 上的歡迎畫面](./media/hello-world-your-first-program/visual-studio-windows-start-screen.png)

選取影像右下角的 [**建立新專案**]。 Visual Studio 會顯示 [**新增專案**] 對話方塊：

![在 Windows 上 Visual Studio 新增專案畫面](./media/hello-world-your-first-program/visual-studio-windows-new-project.png)

> [!NOTE]
> 如果這是您第一次啟動 Visual Studio，[**最近使用的專案範本**] 清單會是空的。

在 [新增專案] 對話方塊中，選擇 [主控台應用程式（.NET Core）]，然後按 **[下一步]** 。 為您的專案命名，例如 "HelloWorld"，然後按 [**建立**]。

Visual Studio 會開啟您的專案。 它已經是基本的「Hello World！」 為例。 按`Ctrl`  + 以執行您的專案。`F5` Visual Studio 會建立您的專案，並將原始程式碼轉換成可執行檔。 然後，它會啟動執行新應用程式的命令視窗。 您應該會在視窗中看到下列文字：

```console
Hello World!

C:\Program Files\dotnet\dotnet.exe (process 11964) exited with code 0.
Press any key to close this window . . .
```

按下任意鍵即可關閉視窗。

# <a name="macostabmacos"></a>[macOS](#tab/macos)

啟動 Visual Studio for Mac。 您會在 Mac 上看到下列影像：

![Visual Studio Mac 上的歡迎使用畫面](./media/hello-world-your-first-program/visual-studio-mac-start-screen.png)

> [!NOTE]
> 如果這是您第一次啟動 Visual Studio for Mac，[**最近使用的專案**] 清單會是空的。

選取影像右上角的 [**新增**]。 Visual Studio for Mac 會顯示 [**新增專案**] 對話方塊：

![在 Mac 上 Visual Studio 新增專案 畫面](./media/hello-world-your-first-program/visual-studio-mac-new-project.png)

在 [新增專案] 對話方塊中，選擇 [.NET Core] 和 [主控台應用程式]，然後按 **[下一步]** 。 您必須選取目標 framework。 預設值是正常的，因此請按 [下一步]。 為您的專案命名，例如 "HelloWorld"，然後按 [**建立**]。 您可以使用預設的專案位置。 請勿將這個專案加入至原始檔控制。

Visual Studio for Mac 會開啟您的專案。 它已經是基本的「Hello World！」 為例。 按`Ctrl` 以執行 + 您的專案。 +  `Fn` `F5` Visual Studio for Mac 會建立您的專案，並將原始程式碼轉換成可執行檔。 然後，它會啟動執行新應用程式的命令視窗。 您應該會在視窗中看到下列文字：

```console
Hello World!

Press any key to close this window . . .
```

按下鍵以結束會話。

---

## <a name="elements-of-a-c-program"></a>C#程式的元素

讓我們來檢查這個程式的重要部分。 第一行包含註解。 字元 `//` 會將該行的其餘部分轉換成註解。

[!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

您也可以用 `/*` 和 `*/` 字元括住它，註解文字區塊。 這在下列範例中顯示。

[!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

C# 主控台應用程式必須包含 `Main` 方法，控制項在此開始和結束。 `Main` 方法是您建立物件和執行其他方法的所在。

`Main` 方法是位於類別或結構內的[靜態](../../language-reference/keywords/static.md)方法。 在上一個 "Hello World!" 範例中，它位於名為 `Hello` 的類別中。 您可以下列方式之一宣告 `Main` 方法：

- 它會傳回 `void`。 這表示您的程式不會傳回值。

[!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- 它也可以傳回整數。 整數是應用程式的結束**代碼**。

[!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- 使用任一傳回型別，它可以接受引數。

[!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

-或-

[!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

`Main` 方法的參數 `args`，是包含用來叫用程式的命令列引數的 `string` 陣列。

如需如何使用命令列引數的詳細資訊，請參閱[Main （）和命令列引數](../main-and-command-args/index.md)中的範例。

## <a name="input-and-output"></a>輸入和輸出

C# 程式通常會使用 .NET Framework 執行階段程式庫所提供的輸入/輸出服務。 陳述式 `System.Console.WriteLine("Hello World!");` 使用 <xref:System.Console.WriteLine%2A> 方法。 這是執行階段程式庫中 <xref:System.Console> 類別的其中一個輸出方法。 它會在標準輸出資料流中顯示其字串參數，後面接著新行。 其他 <xref:System.Console> 方法可供不同的輸入和輸出作業使用。 如果您在程式開始處包含 `using System;` 指示詞，就可以直接使用 <xref:System> 類別和方法，而不必完整限定它們。 例如，您可以呼叫 `Console.WriteLine` 而不用呼叫 `System.Console.WriteLine`：

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

如需輸入/輸出方法的詳細資訊，請參閱 <xref:System.IO>。

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [範例與教學課程](../../../samples-and-tutorials/index.md)
- [Main() 和命令列引數](../main-and-command-args/index.md)
- [Visual C# 和 Visual Basic 使用者入門](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
