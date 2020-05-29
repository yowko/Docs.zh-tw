---
title: 使用 Visual Studio Code 建立具有 .NET Core 的主控台應用程式
description: 瞭解如何使用 Visual Studio Code 和 .NET Core CLI 建立 .NET Core 主控台應用程式。
ms.date: 05/22/2020
ms.openlocfilehash: 673c4a639a2cab26261b7cdafd5d8e20acfafb94
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201693"
---
# <a name="tutorial-create-a-console-application-with-net-core-using-visual-studio-code"></a>教學課程：使用 Visual Studio Code 建立具有 .NET Core 的主控台應用程式

本教學課程說明如何使用 Visual Studio Code 和 .NET Core CLI 來建立和執行 .NET Core 主控台應用程式。 專案工作（例如建立、編譯和執行專案）是使用 CLI 來完成，因此，您可以使用不同的程式碼編輯器來遵循此教學課程，並視需要在終端機中執行命令。

## <a name="prerequisites"></a>Prerequisites

1. 已安裝[c # 擴充](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)功能的[Visual Studio Code](https://code.visualstudio.com/) 。 如需有關如何在 Visual Studio Code 上安裝延伸模組的詳細資訊，請參閱[VS Code 延伸模組 Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery)。
2. [.Net Core 3.1 SDK 或更新版本](https://dotnet.microsoft.com/download)

## <a name="create-the-app"></a>建立應用程式

1. 開啟 Visual Studio Code。

1. 建立專案。

   1. **File**  >  從主功能表選取 [檔案] [**開啟資料夾**] / [**開啟 ...** ]，建立*HelloWorld*資料夾，然後按一下 [**選取資料夾**] [ / **開啟**]。

      資料夾名稱預設會成為專案名稱和命名空間名稱。 您稍後會在本教學課程中新增程式碼，假設專案命名空間為 `HelloWorld` 。

   1. 從主功能表選取 [**查看**終端機]，以在 Visual Studio Code 中開啟**終端**機  >  **Terminal** 。

      **終端**機會在*HelloWorld*資料夾中以命令提示字元開啟。

   1. 在**終端**機中，輸入下列命令：

      ```dotnetcli
      dotnet new console
      ```

適用于 .NET Core 的主控台應用程式範本會定義一個類別， `Program` 其中包含單一方法，其 `Main` 採用 <xref:System.String> 陣列做為引數。 *Program.cs*檔案包含下列程式碼：

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

此範本會建立一個簡單的應用程式， <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 以呼叫方法來顯示 "Hello World！" 。

## <a name="run-the-app"></a>執行應用程式

在**終端**機中執行下列命令：

```dotnetcli
dotnet run
```

程式會顯示 "Hello World！" 和結束。

![DotNet 執行命令](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="enhance-the-app"></a>增強應用程式

增強應用程式，以提示使用者輸入其名稱，並連同日期和時間一起顯示。

1. 按一下 *Program.cs* 來開啟它。

   在 Visual Studio Code 中第一次開啟 C# 檔案時，會在編輯器中載入 [OmniSharp](https://www.omnisharp.net/)。

   ![開啟 Program.cs 檔案](media/with-visual-studio-code/open-program-cs.png)

1. 當 Visual Studio Code 提示您新增遺失的資產，以建立和偵錯工具時，請選取 **[是]** 。

   ![遺失資產的提示](media/with-visual-studio-code/missing-assets.png)

1. 以 `Main` 下列程式碼取代*Program.cs*中方法的內容，這目前只是呼叫的那一行 `Console.WriteLine` ：

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="Snippet1":::

   此程式碼會在主控台中顯示「What is your name?」， 在主控台視窗中，等候使用者輸入後面接著**Enter**鍵的字串。 它會將此字串儲存在名為的變數中 `name` 。 此程式碼也會擷取 <xref:System.DateTime.Now?displayProperty=nameWithType> 屬性的值，其中包含目前的當地時間，並將它指派至名稱為 `date` 的變數。 最後，它會在主控台視窗中顯示這些值。

   `\n`代表換行字元。

   字串前面的貨幣符號（ `$` ）可讓您在字串中的大括弧內放置運算式，例如變數名稱。 運算式值會插入字串中，以取代運算式。 此語法稱為「插入[字串](../../csharp/language-reference/tokens/interpolated.md)」。

1. 儲存您的變更。

   > [!IMPORTANT]
   > 在 Visual Studio Code 中，您必須明確地儲存變更。 不同于 Visual Studio，當您建立並執行應用程式時，不會自動儲存檔案變更。

1. 再次執行程式：

   ```dotnetcli
   dotnet run
   ```

1. 輸入名稱並按**enter**鍵，以回應提示。

   :::image type="content" source="media/debugging-with-visual-studio-code/run-modified-program.png" alt-text="已修改程式輸出的終端機視窗":::

1. 按任意鍵以結束程式。

## <a name="additional-resources"></a>其他資源

- [設定 Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview)

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已建立 .NET Core 應用程式。 在下一個教學課程中，您會對應用程式進行 debug。

> [!div class="nextstepaction"]
> [使用 Visual Studio Code 來調試 .NET Core 主控台應用程式](debugging-with-visual-studio-code.md)
