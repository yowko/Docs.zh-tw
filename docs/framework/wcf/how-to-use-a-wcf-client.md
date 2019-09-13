---
title: 教學課程：使用 Windows Communication Foundation 用戶端
ms.date: 03/19/2019
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: 5c280933c81ef54ba58181e3005e30775b9b8e42
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928891"
---
# <a name="tutorial-use-a-windows-communication-foundation-client"></a>教學課程：使用 Windows Communication Foundation 用戶端

本教學課程說明建立基本 Windows Communication Foundation （WCF）應用程式所需的五個工作中的最後一個。 如需教學課程的總覽，請[參閱教學課程：Windows Communication Foundation 應用程式](getting-started-tutorial.md)入門。

建立並設定 Windows Communication Foundation （WCF） proxy 之後，您可以建立用戶端實例並編譯用戶端應用程式。 接著，您可以使用它來與 WCF 服務進行通訊。 

在本教學課程中，您將了解如何：
> [!div class="checklist"]
>
> - 加入程式碼以使用 WCF 用戶端。
> - 測試 WCF 用戶端。

## <a name="add-code-to-use-the-wcf-client"></a>加入程式碼以使用 WCF 用戶端

用戶端程式代碼會執行下列步驟：

- 將 WCF 用戶端具現化。
- 從產生的 Proxy 呼叫服務作業。
- 完成作業呼叫之後關閉用戶端。

從**GettingStartedClient**專案開啟**Program.cs**或**Module1**檔案，並將其程式碼取代為下列程式碼：

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GettingStartedClient.ServiceReference1;

namespace GettingStartedClient
{
    class Program
    {
        static void Main(string[] args)
        {
            //Step 1: Create an instance of the WCF proxy.
            CalculatorClient client = new CalculatorClient();

            // Step 2: Call the service operations.
            // Call the Add service operation.
            double value1 = 100.00D;
            double value2 = 15.99D;
            double result = client.Add(value1, value2);
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

            // Call the Subtract service operation.
            value1 = 145.00D;
            value2 = 76.54D;
            result = client.Subtract(value1, value2);
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

            // Call the Multiply service operation.
            value1 = 9.00D;
            value2 = 81.25D;
            result = client.Multiply(value1, value2);
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

            // Call the Divide service operation.
            value1 = 22.00D;
            value2 = 7.00D;
            result = client.Divide(value1, value2);
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);

            // Step 3: Close the client to gracefully close the connection and clean up resources.
            Console.WriteLine("\nPress <Enter> to terminate the client.");
            Console.ReadLine();
            client.Close();
        }
    }
}
```

```vb
Imports System
Imports System.Collections.Generic
Imports System.Text
Imports System.ServiceModel
Imports GettingStartedClient.ServiceReference1

Module Module1

    Sub Main()
        ' Step 1: Create an instance of the WCF proxy.
        Dim Client As New CalculatorClient()

        ' Step 2: Call the service operations.
        ' Call the Add service operation.
        Dim value1 As Double = 100D
        Dim value2 As Double = 15.99D
        Dim result As Double = Client.Add(value1, value2)
        Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)

        ' Call the Subtract service operation.
        value1 = 145D
        value2 = 76.54D
        result = Client.Subtract(value1, value2)
        Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)

        ' Call the Multiply service operation.
        value1 = 9D
        value2 = 81.25D
        result = Client.Multiply(value1, value2)
        Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)

        ' Call the Divide service operation.
        value1 = 22D
        value2 = 7D
        result = Client.Divide(value1, value2)
        Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)

        ' Step 3: Close the client to gracefully close the connection and clean up resources.
        Console.WriteLine()
        Console.WriteLine("Press <Enter> to terminate the client.")
        Console.ReadLine()
        Client.Close()

    End Sub

End Module
```

請注意C# `Imports` `GettingStartedClient.ServiceReference1`（適用于 Visual）或（適用于 Visual Basic）語句（匯入）。 `using` 此語句會匯入 Visual Studio 以**加入服務參考**函數產生的程式碼。 程式碼會具現化 WCF proxy，並呼叫計算機服務所公開的每個服務作業。 接著，它會關閉 proxy 並結束程式。

## <a name="test-the-wcf-client"></a>測試 WCF 用戶端

### <a name="test-the-application-from-visual-studio"></a>從 Visual Studio 測試應用程式

1. 儲存並建立解決方案。

2. 選取 [ **GettingStartedLib** ] 資料夾，然後從快捷方式功能表選取 [**設定為啟始專案**]。

3. 從 [**啟始專案**] 中，從下拉式清單中選取 [ **GettingStartedLib** ]，然後選取 [**執行**] 或按**F5**。

### <a name="test-the-application-from-a-command-prompt"></a>從命令提示字元測試應用程式

1. 以系統管理員身分開啟命令提示字元，然後流覽至您的 Visual Studio 方案目錄。 

2. 若要啟動服務：輸入*GettingStartedHost\bin\Debug\GettingStartedHost.exe*。

3. 若要啟動用戶端：開啟另一個命令提示字元，流覽至您的 Visual Studio 方案目錄，然後輸入*GettingStartedClient\bin\Debug\GettingStartedClient.exe*。

   *GettingStartedHost*會產生下列輸出：

   ```text
   The service is ready.
   Press <Enter> to terminate the service.

   Received Add(100,15.99)
   Return: 115.99
   Received Subtract(145,76.54)
   Return: 68.46
   Received Multiply(9,81.25)
   Return: 731.25
   Received Divide(22,7)
   Return: 3.14285714285714
   ```

   *GettingStartedClient*會產生下列輸出：

   ```text
   Add(100,15.99) = 115.99
   Subtract(145,76.54) = 68.46
   Multiply(9,81.25) = 731.25
   Divide(22,7) = 3.14285714285714

   Press <Enter> to terminate the client.
   ```

## <a name="next-steps"></a>後續步驟

您現在已完成 WCF 開始使用教學課程中的所有工作。 在本教學課程中，您將了解如何：

在本教學課程中，您將了解如何：
> [!div class="checklist"]
>
> - 加入程式碼以使用 WCF 用戶端。
> - 測試 WCF 用戶端。

如果您在任何步驟中遇到問題或錯誤，請遵循疑難排解文章中的步驟來修正它們。

> [!div class="nextstepaction"]
> [開始使用 WCF 教學課程的疑難排解](troubleshooting-the-getting-started-tutorial.md)
