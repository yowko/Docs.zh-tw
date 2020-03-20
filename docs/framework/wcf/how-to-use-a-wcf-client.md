---
title: 教程：使用 Windows 通信基礎用戶端
ms.date: 03/19/2019
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: d2357c134aef8da204dcdb19d6c1fc93cfdc068c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184017"
---
# <a name="tutorial-use-a-windows-communication-foundation-client"></a><span data-ttu-id="bbaf2-102">教程：使用 Windows 通信基礎用戶端</span><span class="sxs-lookup"><span data-stu-id="bbaf2-102">Tutorial: Use a Windows Communication Foundation client</span></span>

<span data-ttu-id="bbaf2-103">本教程介紹創建基本 Windows 通信基礎 （WCF） 應用程式所需的五個任務中的最後一個任務。</span><span class="sxs-lookup"><span data-stu-id="bbaf2-103">This tutorial describes the last of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="bbaf2-104">有關教程的概述，請參閱[教程：開始使用 Windows 通信基礎應用程式](getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="bbaf2-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="bbaf2-105">創建並配置 Windows 通信基礎 （WCF） 代理後，將創建用戶端實例並編譯用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="bbaf2-105">After you've created and configured a Windows Communication Foundation (WCF) proxy, you create a client instance and compile the client application.</span></span> <span data-ttu-id="bbaf2-106">然後，使用它與 WCF 服務進行通信。</span><span class="sxs-lookup"><span data-stu-id="bbaf2-106">You then use it to communicate with the WCF service.</span></span>

<span data-ttu-id="bbaf2-107">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="bbaf2-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="bbaf2-108">添加代碼以使用 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="bbaf2-108">Add code to use the WCF client.</span></span>
> - <span data-ttu-id="bbaf2-109">測試 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="bbaf2-109">Test the WCF client.</span></span>

## <a name="add-code-to-use-the-wcf-client"></a><span data-ttu-id="bbaf2-110">添加代碼以使用 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="bbaf2-110">Add code to use the WCF client</span></span>

<span data-ttu-id="bbaf2-111">用戶端代碼執行以下步驟：</span><span class="sxs-lookup"><span data-stu-id="bbaf2-111">The client code does the following steps:</span></span>

- <span data-ttu-id="bbaf2-112">具現化 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="bbaf2-112">Instantiates the WCF client.</span></span>
- <span data-ttu-id="bbaf2-113">從產生的 Proxy 呼叫服務作業。</span><span class="sxs-lookup"><span data-stu-id="bbaf2-113">Calls the service operations from the generated proxy.</span></span>
- <span data-ttu-id="bbaf2-114">操作調用完成後關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="bbaf2-114">Closes the client after the operation call is completed.</span></span>

<span data-ttu-id="bbaf2-115">從**入門用戶端**專案中打開**Program.cs**或**Module1.vb**檔，並將其代碼替換為以下代碼：</span><span class="sxs-lookup"><span data-stu-id="bbaf2-115">Open the **Program.cs** or **Module1.vb** file from the **GettingStartedClient** project and replace its code with the following code:</span></span>

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

<span data-ttu-id="bbaf2-116">請注意導入`using``GettingStartedClient.ServiceReference1`的 （用於視覺`Imports`C#） 或 （用於可視基本）語句。</span><span class="sxs-lookup"><span data-stu-id="bbaf2-116">Notice the `using` (for Visual C#) or `Imports` (for Visual Basic) statement that imports `GettingStartedClient.ServiceReference1`.</span></span> <span data-ttu-id="bbaf2-117">此語句導入 Visual Studio 使用**添加服務引用**函數生成的代碼。</span><span class="sxs-lookup"><span data-stu-id="bbaf2-117">This statement imports the code that Visual Studio generated with the **Add Service Reference** function.</span></span> <span data-ttu-id="bbaf2-118">代碼具現化 WCF 代理並調用計算機服務公開的每個服務操作。</span><span class="sxs-lookup"><span data-stu-id="bbaf2-118">The code instantiates the WCF proxy and calls each of the service operations that the calculator service exposes.</span></span> <span data-ttu-id="bbaf2-119">然後關閉代理並結束程式。</span><span class="sxs-lookup"><span data-stu-id="bbaf2-119">It then closes the proxy and ends the program.</span></span>

## <a name="test-the-wcf-client"></a><span data-ttu-id="bbaf2-120">測試 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="bbaf2-120">Test the WCF client</span></span>

### <a name="test-the-application-from-visual-studio"></a><span data-ttu-id="bbaf2-121">從視覺化工作室測試應用程式</span><span class="sxs-lookup"><span data-stu-id="bbaf2-121">Test the application from Visual Studio</span></span>

1. <span data-ttu-id="bbaf2-122">儲存並建置方案。</span><span class="sxs-lookup"><span data-stu-id="bbaf2-122">Save and build the solution.</span></span>

2. <span data-ttu-id="bbaf2-123">選擇 **"入門專案"** 資料夾，然後從快顯功能表中選擇 **"設置為啟動專案**"。</span><span class="sxs-lookup"><span data-stu-id="bbaf2-123">Select the **GettingStartedLib** folder, and then select **Set as Startup Project** from the shortcut menu.</span></span>

3. <span data-ttu-id="bbaf2-124">從**啟動專案**，從下拉清單中選擇 **"入門Lib"，** 然後選擇 **"運行"** 或按**F5**。</span><span class="sxs-lookup"><span data-stu-id="bbaf2-124">From **Startup Projects**, select **GettingStartedLib** from the drop-down list, then select **Run** or press **F5**.</span></span>

### <a name="test-the-application-from-a-command-prompt"></a><span data-ttu-id="bbaf2-125">從命令提示符測試應用程式</span><span class="sxs-lookup"><span data-stu-id="bbaf2-125">Test the application from a command prompt</span></span>

1. <span data-ttu-id="bbaf2-126">以管理員身份打開命令提示，然後導航到視覺化工作室解決方案目錄。</span><span class="sxs-lookup"><span data-stu-id="bbaf2-126">Open a command prompt as an administrator, and then navigate to your Visual Studio solution directory.</span></span>

2. <span data-ttu-id="bbaf2-127">要啟動服務：輸入*入門主機\bin\調試\入門Host.exe。*</span><span class="sxs-lookup"><span data-stu-id="bbaf2-127">To start the service: Enter *GettingStartedHost\bin\Debug\GettingStartedHost.exe*.</span></span>

3. <span data-ttu-id="bbaf2-128">要啟動用戶端：打開另一個命令提示符，導航到視覺化工作室解決方案目錄，然後輸入*入門用戶端\bin_Debug_獲取啟動用戶端.exe。*</span><span class="sxs-lookup"><span data-stu-id="bbaf2-128">To start the client: Open another command prompt, navigate to your Visual Studio solution directory, then enter *GettingStartedClient\bin\Debug\GettingStartedClient.exe*.</span></span>

   <span data-ttu-id="bbaf2-129">*入門Host.exe*生成以下輸出：</span><span class="sxs-lookup"><span data-stu-id="bbaf2-129">*GettingStartedHost.exe* produces the following output:</span></span>

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

   <span data-ttu-id="bbaf2-130">*入門用戶端.exe*生成以下輸出：</span><span class="sxs-lookup"><span data-stu-id="bbaf2-130">*GettingStartedClient.exe* produces the following output:</span></span>

   ```text
   Add(100,15.99) = 115.99
   Subtract(145,76.54) = 68.46
   Multiply(9,81.25) = 731.25
   Divide(22,7) = 3.14285714285714

   Press <Enter> to terminate the client.
   ```

## <a name="next-steps"></a><span data-ttu-id="bbaf2-131">後續步驟</span><span class="sxs-lookup"><span data-stu-id="bbaf2-131">Next steps</span></span>

<span data-ttu-id="bbaf2-132">現在，您已經完成了 WCF 入門教程中的所有任務。</span><span class="sxs-lookup"><span data-stu-id="bbaf2-132">You've now completed all the tasks in the WCF get started tutorial.</span></span> <span data-ttu-id="bbaf2-133">在本教學課程中，您已了解如何：</span><span class="sxs-lookup"><span data-stu-id="bbaf2-133">In this tutorial, you learned how to:</span></span>

<span data-ttu-id="bbaf2-134">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="bbaf2-134">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="bbaf2-135">添加代碼以使用 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="bbaf2-135">Add code to use the WCF client.</span></span>
> - <span data-ttu-id="bbaf2-136">測試 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="bbaf2-136">Test the WCF client.</span></span>

<span data-ttu-id="bbaf2-137">如果任一步驟中存在問題或錯誤，請按照疑難排解文章中的步驟進行修復。</span><span class="sxs-lookup"><span data-stu-id="bbaf2-137">If you have problems or errors in any of the steps, follow the steps in the troubleshooting article to fix them.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bbaf2-138">使用 WCF 教程對入門進行故障排除</span><span class="sxs-lookup"><span data-stu-id="bbaf2-138">Troubleshoot the Get started with WCF tutorials</span></span>](troubleshooting-the-getting-started-tutorial.md)
