---
title: 教學課程：使用 Windows Communication Foundation 用戶端
ms.date: 03/19/2019
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: fa9aa3612a8dc72623fc4ea4b1ea337ac773fa26
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61928839"
---
# <a name="tutorial-use-a-windows-communication-foundation-client"></a>教學課程：使用 Windows Communication Foundation 用戶端

本教學課程說明建立基本的 Windows Communication Foundation (WCF) 應用程式所需的五個工作的最後一個。 如需教學課程的概觀，請參閱[教學課程：開始使用 Windows Communication Foundation 應用程式](getting-started-tutorial.md)。

您已建立並設定 Windows Communication Foundation (WCF) proxy 之後，您會建立用戶端執行個體，並編譯用戶端應用程式。 您再使用它來與 WCF 服務進行通訊。 

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> - 加入程式碼使用 WCF 用戶端。
> - 測試 WCF 用戶端。

## <a name="add-code-to-use-the-wcf-client"></a>加入程式碼來使用 WCF 用戶端

用戶端程式碼會執行下列步驟：
- 具現化 WCF 用戶端。
- 從產生的 Proxy 呼叫服務作業。
- 完成作業呼叫之後，請關閉用戶端。

開啟**Program.cs**或是**Module1.vb**從檔案**GettingStartedClient**專案，並以下列程式碼取代其程式碼：

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

請注意`using`(視覺效果C#) 或`Imports`（適用於 Visual Basic) 陳述式匯入`GettingStartedClient.ServiceReference1`。 此陳述式匯入 Visual Studio 產生的程式碼**加入服務參考**函式。 程式碼會具現化 WCF proxy，並呼叫每個計算機服務所公開的服務作業。 然後，它會關閉 proxy 並結束程式。

## <a name="test-the-wcf-client"></a>測試 WCF 用戶端

### <a name="test-the-application-from-visual-studio"></a>測試應用程式從 Visual Studio

1. 儲存並建置方案。

2. 選取  **GettingStartedLib**資料夾，然後再選取**設定為啟始專案**從捷徑功能表。

3. 從**啟始專案**，選取**GettingStartedLib**從下拉式清單中，然後選取**執行**，或按**F5**。

### <a name="test-the-application-from-a-command-prompt"></a>測試應用程式，從命令提示字元

1. 開啟命令提示字元，身為管理員，，然後瀏覽至您的 Visual Studio 方案目錄。 

2. 若要啟動服務：請輸入*GettingStartedHost\bin\Debug\GettingStartedHost.exe*。

3. 若要啟動用戶端：開啟另一個命令提示字元，瀏覽至您的 Visual Studio 方案目錄，然後輸入*GettingStartedClient\bin\Debug\GettingStartedClient.exe*。

   *GettingStartedHost.exe*產生下列輸出：

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

   *GettingStartedClient.exe*產生下列輸出：

   ```text
   Add(100,15.99) = 115.99
   Subtract(145,76.54) = 68.46
   Multiply(9,81.25) = 731.25
   Divide(22,7) = 3.14285714285714

   Press <Enter> to terminate the client.
   ```

## <a name="next-steps"></a>後續步驟

您現在已在 WCF 快速入門教學課程中完成所有工作。 在本教學課程中，您將了解如何：

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> - 加入程式碼使用 WCF 用戶端。
> - 測試 WCF 用戶端。

如果您有問題或錯誤中的任何步驟，請依照下列修正它們的疑難排解文件中的步驟。

> [!div class="nextstepaction"]
> [疑難排解 Get 開始使用 WCF 的教學課程](troubleshooting-the-getting-started-tutorial.md)
