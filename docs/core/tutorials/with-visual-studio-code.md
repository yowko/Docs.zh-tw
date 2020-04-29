---
title: C# 與 Visual Studio Code 使用者入門
description: 了解如何在 C# 中使用 Visual Studio Code 建立並偵錯您的第一個 .NET Core 應用程式。
author: kendrahavens
ms.date: 04/23/2020
ms.openlocfilehash: 3dd7c4602fbb27e29bad977f8d3df34b6061bc23
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506874"
---
# <a name="get-started-with-c-and-visual-studio-code"></a>C# 與 Visual Studio Code 使用者入門

.NET Core 提供快速且模組化的平台，可建立在 Windows、Linux 和 macOS 上執行的應用程式。 搭配使用 Visual Studio Code 與 C# 擴充功能，以取得具備 C# IntelliSense (智慧型程式碼完成) 與偵錯完整支援的強大編輯體驗。

## <a name="prerequisites"></a>先決條件

1. 安裝 [Visual Studio Code](https://code.visualstudio.com/)。
2. 安裝 [.NET Core SDK](https://dotnet.microsoft.com/download)。
3. 安裝適用於 Visual Studio Code 的 [C# 擴充功能](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) \(英文\)。 如需如何在 Visual Studio Code 上安裝擴充功能的詳細資訊，請參閱 [VS Code 擴充功能市集](https://code.visualstudio.com/docs/editor/extension-gallery) \(英文\)。

## <a name="hello-world"></a>Hello World

開始使用 .NET Core 上的簡單 "Hello World" 程式：

1. 開啟專案：

    - 開啟 Visual Studio Code。
    - 從主**功能表選取 [** 檔案] [**開啟資料夾**]。 > 
    - 建立名為*HelloWorld*的資料夾，然後按一下 [**選取資料夾**]。 資料夾名稱預設會成為專案名稱和命名空間名稱。 您稍後會在本教學課程中新增程式碼，假設專案`HelloWorld`命名空間為。

1. 初始化 C# 專案：

    - 從主功能表選取 [**查看** > **終端**機]，從 Visual Studio Code 開啟終端機。
    - 在終端機視窗中， `dotnet new console`輸入。

      此命令會在您的資料夾中建立*Program.cs*檔案，其中已撰寫簡單的 "Hello World" 程式，以及名為*HelloWorld*的 c # 專案檔。

      ![DotNet 新增命令](media/with-visual-studio-code/dotnet-new-command.png)

1. 執行 "Hello World" 程式︰

    - 在終端機視窗中， `dotnet run`輸入。

      ![DotNet 執行命令](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="debug"></a>偵錯

1. 按一下 *Program.cs* 來開啟它。 在 Visual Studio Code 中第一次開啟 C# 檔案時，會在編輯器中載入 [OmniSharp](https://www.omnisharp.net/)。

    ![開啟 Program.cs 檔案](media/with-visual-studio-code/open-program-cs.png)

1. Visual Studio Code 會提示您新增遺失的資產，以建立及偵錯工具。 選取 [是]  。

    ![遺失資產的提示](media/with-visual-studio-code/missing-assets.png)

1. 若要開啟 [偵錯] 檢視，請按一下左側功能表上的 [偵錯] 圖示。

    ![在 Visual Studio Code 中開啟 [偵錯] 索引標籤](media/with-visual-studio-code/open-debug-tab.png)

1. 尋找窗格頂端的綠色箭頭。 請確定其旁邊的下拉式選已選取 [ **.Net Core 啟動] （主控台）** 。

    ![在 Visual Studio Code 中選取 .NET Core](media/with-visual-studio-code/select-net-core.png)

1. 按一下第 9 行旁邊的 [編輯器邊界]**** (編輯器中行號左側空白處)，將中斷點新增至您的專案，或將文字游標移至編輯器中的第 9 行，然後按 <kbd>F9</kbd> 鍵。

    ![設定中斷點](media/with-visual-studio-code/set-breakpoint-vs-code.png)

1. 若要開始進行調試，請按<kbd>F5</kbd>或選取綠色箭號。 當偵錯程式到達您在上一個步驟中設定的中斷點時，它會停止您程式的執行。
    - 在偵錯工具中，您可以在左上方窗格中，或使用 debug 主控台來查看您的本機變數。

1. 選取頂端的藍色箭頭以繼續偵錯，或選取頂端的紅色正方形以停止偵錯。

    ![在 Visual Studio Code 中執行和偵錯](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> 如需在 Visual Studio Code 中使用 OmniSharp 進行 .NET Core 偵錯的詳細資訊與疑難排解祕訣，請參閱 [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md) (設定 .NET Core 偵錯工具的指示)。

## <a name="add-a-class"></a>新增類別

1. 若要加入新的類別，請以滑鼠右鍵按一下*Program.cs*下方的 VSCode Explorer，然後選取 [**新增**檔案]。 這會在您於 VSCode 中開啟的資料夾內新增檔案。
1. 將檔案命名為*MyClass.cs*。 您必須在結尾加上 `.cs` 副檔名來儲存它，系統才能將它辨識為 csharp 檔案。
1. 新增下列程式碼，以建立您的第一個類別。

    ``` csharp
    using System;

    namespace HelloWorld
    {
        public class MyClass
        {
            public string ReturnMessage()
            {
                return "Happy coding!";
            }
        }
    }
    ```

1. 將 Program.cs 中的程式碼`Main`取代為下列程式碼， *Program.cs*以從您的方法呼叫新的類別：

    ```csharp
    using System;

    namespace HelloWorld
    {
        class Program
        {
            static void Main(string[] args)
            {
                var c1 = new MyClass();
                Console.WriteLine($"Hello World! {c1.ReturnMessage()}");
            }
        }
    }
    ```

1. 儲存您的變更。

1. 再次執行程式。

    ```dotnetcli
    dotnet run
    ```

    新訊息隨即出現，並附上附加的字串。

    ```console
    Hello World! Happy coding!
    ```

## <a name="faq"></a>常見問題集

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a>我缺少在 Visual Studio Code 中建置及偵錯 C# 所需的資產。 我的偵錯工具顯示「沒有組態」。

Visual Studio Code C# 延伸模組可為您產生用於建置和偵錯的資產。 Visual Studio Code 會在您第一次開啟 C# 專案時，提示您產生這些資產。 如果您當時未產生資產，仍可以透過開啟 [命令選擇區] ([檢視] > [命令選擇區]****)，然後鍵入 ">.NET: Generate Assets for Build and Debug" 來執行此命令。 選取此程式會產生*vscode*、*啟動 json*和您需要的*json*設定檔案。

## <a name="see-also"></a>請參閱

- [設定 Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview)
- [在 Visual Studio Code 中偵錯](https://code.visualstudio.com/Docs/editor/debugging)
