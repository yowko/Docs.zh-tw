---
title: 使用 Visual Studio Code 建立 .NET 主控台應用程式
description: 瞭解如何使用 Visual Studio Code 和 .NET CLI 來建立 .NET 主控台應用程式。
ms.date: 11/17/2020
ms.openlocfilehash: dbbdf88b0c84089249eb7e446c25eddc11543c1a
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94915865"
---
# <a name="tutorial-create-a-net-console-application-using-visual-studio-code"></a>教學課程：使用 Visual Studio Code 建立 .NET 主控台應用程式

本教學課程說明如何使用 Visual Studio Code 和 .NET CLI 來建立和執行 .NET 主控台應用程式。 專案工作（例如建立、編譯和執行專案）是使用 .NET CLI 來完成。 您可以使用不同的程式碼編輯器來進行本教學課程，並在您想要的情況下在終端機中執行命令。

## <a name="prerequisites"></a>先決條件

1. 已安裝[c # 擴充](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)功能的[Visual Studio Code](https://code.visualstudio.com/) 。 如需有關如何在 Visual Studio Code 上安裝擴充功能的詳細資訊，請參閱 [VS Code 擴充功能 Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery)。
2. [.Net 5.0 SDK 或更新版本](https://dotnet.microsoft.com/download)

## <a name="create-the-app"></a>建立應用程式

建立名為 "HelloWorld" 的 .NET 主控台應用程式專案。

1. 啟動 Visual Studio Code。

1. **File**  >  從主功能表選取 [ **File** 檔案 **開啟資料夾** (檔案開啟  >  **...** ] macOS) 。

1. 在 [ **開啟資料夾** ] 對話方塊中，建立 *HelloWorld* 資料夾，然後按一下 [ **選取資料夾** (在 macOS) **開啟** ]。

   資料夾名稱預設會變成專案名稱和命名空間名稱。 您稍後會在教學課程中假設專案命名空間為的程式碼中加入程式碼 `HelloWorld` 。

1. 從主功能表中選取 [ **View** terminal]，以在 Visual Studio Code 中開啟 **終端** 機  >  **Terminal** 。

   **終端** 機會在 *HelloWorld* 資料夾中使用命令提示字元開啟。

1. 在 **終端** 機中，輸入下列命令：

   ```dotnetcli
   dotnet new console
   ```

此範本會建立簡單的 "Hello World" 應用程式。 它會呼叫 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 方法，以 :::no-loc text="Hello World!"::: 在主控台視窗中顯示 ""。

範本 `Program` 程式碼會使用單一方法定義類別， `Main` 這個方法會採用 <xref:System.String> 陣列作為引數：

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

`Main` 是應用程式進入點，是執行階段在啟動應用程式時會自動呼叫的方法。 在應用程式啟動時所提供的所有命令列引數，都會在 *args* 陣列中提供。

## <a name="run-the-app"></a>執行應用程式

在 **終端** 機中執行下列命令：

```dotnetcli
dotnet run
```

程式會顯示 "Hello World！" 並結束。

![DotNet 執行命令](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="enhance-the-app"></a>增強應用程式

增強應用程式以提示使用者輸入其名稱，並將它與日期和時間一起顯示。

1. 按一下 *Program.cs* 來開啟它。

   在 Visual Studio Code 中第一次開啟 C# 檔案時，會在編輯器中載入 [OmniSharp](https://www.omnisharp.net/)。

   ![開啟 Program.cs 檔案](media/with-visual-studio-code/open-program-cs.png)

1. 當 Visual Studio Code 提示您新增遺失的資產來建立和偵測應用程式時，請選取 **[是]** 。

   ![遺失資產的提示](media/with-visual-studio-code/missing-assets.png)

1. 以 `Main` 下列程式碼取代 *Program.cs* 中的方法內容，這是呼叫的行 `Console.WriteLine` ：

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::

   這段程式碼會在主控台視窗中顯示提示，並等候使用者輸入字串，然後按 <kbd>Enter</kbd> 鍵。 它會將此字串儲存在名為的變數中 `name` 。 此程式碼也會擷取 <xref:System.DateTime.Now?displayProperty=nameWithType> 屬性的值，其中包含目前的當地時間，並將它指派至名稱為 `date` 的變數。 它會在主控台視窗中顯示這些值。 最後，它會在主控台視窗中顯示提示，並呼叫 <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> 方法來等候使用者輸入。

   `\n`代表換行字元。

   字串前面的貨幣符號 (`$`) 可讓您在字串中將運算式（例如變數名稱）放在大括弧中。 運算式值會插入字串以取代運算式。 這個語法稱為 [插補字串](../../csharp/language-reference/tokens/interpolated.md)。

1. 儲存您的變更。

   > [!IMPORTANT]
   > 在 Visual Studio Code 中，您必須明確地儲存變更。 不同于 Visual Studio，當您建立並執行應用程式時，不會自動儲存檔案變更。

1. 重新執行程式：

   ```dotnetcli
   dotnet run
   ```

1. 輸入名稱並按 <kbd>enter</kbd> 鍵，以回應提示。

   :::image type="content" source="media/debugging-with-visual-studio-code/run-modified-program.png" alt-text="已修改之程式輸出的終端視窗":::

1. 按任意鍵以結束該程式。

## <a name="additional-resources"></a>其他資源

- [設定 Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview)

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已建立 .NET 主控台應用程式。 在下一個教學課程中，您將會對應用程式進行偵錯工具。

> [!div class="nextstepaction"]
> [使用 Visual Studio Code 來對 .NET 主控台應用程式進行偵錯工具](debugging-with-visual-studio-code.md)
