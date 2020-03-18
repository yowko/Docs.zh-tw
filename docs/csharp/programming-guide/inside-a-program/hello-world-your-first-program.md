---
title: 你好世界 - 您的第一個程式使用視覺工作室在Windows或Mac - C# 程式設計指南
ms.date: 09/12/2019
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 910fa4af1b4e45ce627b589a06910dc168490047
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712139"
---
# <a name="hello-world----your-first-program"></a>你好世界 - 你的第一個程式

在本文中，您將使用 Visual Studio 創建傳統的"你好世界！ 程式。 Visual Studio 是一款專業的整合式開發環境 （IDE），具有許多專為 .NET 開發而設計的功能。 您將只使用 Visual Studio 中的幾個功能來創建此程式。 要瞭解有關視覺化工作室的更多，請參閱[使用視覺化 C# 入門](/visualstudio/ide/quickstart-csharp-console)。

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="create-a-new-application"></a>建立新的應用程式

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

啟動 Visual Studio。 您將在 Windows 上看到以下圖像：

![Windows 上的視覺化工作室歡迎畫面](./media/hello-world-your-first-program/visual-studio-windows-start-screen.png)

選擇**在圖像右下角創建新專案**。 視覺化工作室顯示**新專案**對話方塊：

![視窗視覺工作室新專案螢幕](./media/hello-world-your-first-program/visual-studio-windows-new-project.png)

> [!NOTE]
> 如果這是您第一次啟動 Visual Studio，則 **"最近專案範本"** 清單為空。

在新專案對話方塊中，選擇"主控台應用 （.NET 核心）"，然後按 **"下一步**"。 為專案命名，如"HelloWorld"，然後按 **"創建**"。

視覺化工作室將打開您的專案。 這已經是一個基本的"你好世界！ 為例。 `Ctrl`  + 按`F5`以運行專案。 Visual Studio 構建您的專案，將原始程式碼轉換為可執行檔。 然後，它會啟動運行新應用程式的命令視窗。 您應該在視窗中看到以下文本：

```console
Hello World!

C:\Program Files\dotnet\dotnet.exe (process 11964) exited with code 0.
Press any key to close this window . . .
```

按下任意鍵即可關閉視窗。

# <a name="macos"></a>[macOS](#tab/macos)

啟動 Mac 視覺工作室。 您將在 Mac 上看到以下圖像：

![Mac 上的視覺工作室歡迎畫面](./media/hello-world-your-first-program/visual-studio-mac-start-screen.png)

> [!NOTE]
> 如果這是您第一次為 Mac 啟動 Visual Studio，則 **"最近專案**"清單為空。

在圖像的右上角選擇 **"新建**"。 Mac 視覺化工作室顯示 **"新專案**"對話方塊：

![Mac 上的視覺化工作室新專案螢幕](./media/hello-world-your-first-program/visual-studio-mac-new-project.png)

在新專案對話方塊中，選擇".NET 核心"和"主控台應用"，然後按 **"下一步**"。 您需要選擇目標框架。 預設值正常，因此請按下一步。 為專案命名，如"HelloWorld"，然後按 **"創建**"。 您可以使用預設專案位置。 不要將此專案添加到原始程式碼管理。

Mac 視覺化工作室將打開您的專案。 這已經是一個基本的"你好世界！ 為例。 `Ctrl`  + 按`Fn`以 +  `F5` 適用于 Mac 的 Visual Studio 構建您的專案，將原始程式碼轉換為可執行檔。 然後，它會啟動運行新應用程式的命令視窗。 您應該在視窗中看到以下文本：

```console
Hello World!

Press any key to close this window . . .
```

按鍵結束會話。

---

## <a name="elements-of-a-c-program"></a>C# 程式的元素

讓我們來研究一下這個程式的重要部分。 第一行包含註解。 字元 `//` 會將該行的其餘部分轉換成註解。

[!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

您也可以用 `/*` 和 `*/` 字元括住它，註解文字區塊。 下列範例會顯示這一點。

[!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

C# 主控台應用程式必須包含 `Main` 方法，控制項在此開始和結束。 `Main` 方法是您建立物件和執行其他方法的所在。

`Main` 方法是位於類別或結構內的[靜態](../../language-reference/keywords/static.md)方法。 在上一個 "Hello World!" 範例中，它位於名為 `Hello` 的類別中。 您可以下列方式之一宣告 `Main` 方法：

- 它會傳回 `void`。 這意味著您的程式不會傳回值。

[!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- 它也可以傳回整數。 整數是應用程式的**結束代碼**。

[!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- 使用任一傳回型別，它可以接受引數。

[!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

-或-

[!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

`Main` 方法的參數 `args`，是包含用來叫用程式的命令列引數的 `string` 陣列。

有關如何使用命令列參數的詳細資訊，請參閱[Main（） 和命令列參數中的示例](../main-and-command-args/index.md)。

## <a name="input-and-output"></a>輸入和輸出

C# 程式通常會使用 .NET Framework 執行階段程式庫所提供的輸入/輸出服務。 陳述式 `System.Console.WriteLine("Hello World!");` 使用 <xref:System.Console.WriteLine%2A> 方法。 這是執行階段程式庫中 <xref:System.Console> 類別的其中一個輸出方法。 它會在標準輸出資料流中顯示其字串參數，後面接著新行。 其他 <xref:System.Console> 方法可供不同的輸入和輸出作業使用。 如果您在程式開始處包含 `using System;` 指示詞，就可以直接使用 <xref:System> 類別和方法，而不必完整限定它們。 例如，您可以呼叫 `Console.WriteLine` 而不用呼叫 `System.Console.WriteLine`：

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

如需輸入/輸出方法的詳細資訊，請參閱 <xref:System.IO>。

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [示例和教程](../../../samples-and-tutorials/index.md)
- [Main() 和命令列引數](../main-and-command-args/index.md)
- [Visual C# 使用者入門](/visualstudio/ide/quickstart-csharp-console)
