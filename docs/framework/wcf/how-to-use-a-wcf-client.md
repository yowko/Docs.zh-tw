---
title: 教學課程：使用 Windows Communication Foundation 用戶端
description: 瞭解如何建立用戶端實例、編譯應用程式，以及與服務進行通訊，這是關於建立 WCF 應用程式的一系列文章的一部分。
ms.date: 03/19/2019
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: 5c94d5f8af679580c4194aaaadeda759098953d2
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244331"
---
# <a name="tutorial-use-a-windows-communication-foundation-client"></a><span data-ttu-id="1eb47-103">教學課程：使用 Windows Communication Foundation 用戶端</span><span class="sxs-lookup"><span data-stu-id="1eb47-103">Tutorial: Use a Windows Communication Foundation client</span></span>

<span data-ttu-id="1eb47-104">本教學課程說明建立基本 Windows Communication Foundation （WCF）應用程式所需的五個工作中的最後一個。</span><span class="sxs-lookup"><span data-stu-id="1eb47-104">This tutorial describes the last of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="1eb47-105">如需教學課程的總覽，請參閱[教學課程：開始使用 Windows Communication Foundation 應用程式](getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="1eb47-105">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="1eb47-106">建立並設定 Windows Communication Foundation （WCF） proxy 之後，您可以建立用戶端實例並編譯用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="1eb47-106">After you've created and configured a Windows Communication Foundation (WCF) proxy, you create a client instance and compile the client application.</span></span> <span data-ttu-id="1eb47-107">接著，您可以使用它來與 WCF 服務進行通訊。</span><span class="sxs-lookup"><span data-stu-id="1eb47-107">You then use it to communicate with the WCF service.</span></span>

<span data-ttu-id="1eb47-108">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="1eb47-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="1eb47-109">加入程式碼以使用 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="1eb47-109">Add code to use the WCF client.</span></span>
> - <span data-ttu-id="1eb47-110">測試 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="1eb47-110">Test the WCF client.</span></span>

## <a name="add-code-to-use-the-wcf-client"></a><span data-ttu-id="1eb47-111">加入程式碼以使用 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="1eb47-111">Add code to use the WCF client</span></span>

<span data-ttu-id="1eb47-112">用戶端程式代碼會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="1eb47-112">The client code does the following steps:</span></span>

- <span data-ttu-id="1eb47-113">將 WCF 用戶端具現化。</span><span class="sxs-lookup"><span data-stu-id="1eb47-113">Instantiates the WCF client.</span></span>
- <span data-ttu-id="1eb47-114">從產生的 Proxy 呼叫服務作業。</span><span class="sxs-lookup"><span data-stu-id="1eb47-114">Calls the service operations from the generated proxy.</span></span>
- <span data-ttu-id="1eb47-115">完成作業呼叫之後關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="1eb47-115">Closes the client after the operation call is completed.</span></span>

<span data-ttu-id="1eb47-116">從**GettingStartedClient**專案開啟**Program.cs**或**Module1**檔案，並將其程式碼取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="1eb47-116">Open the **Program.cs** or **Module1.vb** file from the **GettingStartedClient** project and replace its code with the following code:</span></span>

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

<span data-ttu-id="1eb47-117">請注意 `using` （適用于 Visual c #）或 `Imports` （適用于 Visual Basic）可匯入的語句 `GettingStartedClient.ServiceReference1` 。</span><span class="sxs-lookup"><span data-stu-id="1eb47-117">Notice the `using` (for Visual C#) or `Imports` (for Visual Basic) statement that imports `GettingStartedClient.ServiceReference1`.</span></span> <span data-ttu-id="1eb47-118">此語句會匯入 Visual Studio 以**加入服務參考**函數產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1eb47-118">This statement imports the code that Visual Studio generated with the **Add Service Reference** function.</span></span> <span data-ttu-id="1eb47-119">程式碼會具現化 WCF proxy，並呼叫計算機服務所公開的每個服務作業。</span><span class="sxs-lookup"><span data-stu-id="1eb47-119">The code instantiates the WCF proxy and calls each of the service operations that the calculator service exposes.</span></span> <span data-ttu-id="1eb47-120">接著，它會關閉 proxy 並結束程式。</span><span class="sxs-lookup"><span data-stu-id="1eb47-120">It then closes the proxy and ends the program.</span></span>

## <a name="test-the-wcf-client"></a><span data-ttu-id="1eb47-121">測試 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="1eb47-121">Test the WCF client</span></span>

### <a name="test-the-application-from-visual-studio"></a><span data-ttu-id="1eb47-122">從 Visual Studio 測試應用程式</span><span class="sxs-lookup"><span data-stu-id="1eb47-122">Test the application from Visual Studio</span></span>

1. <span data-ttu-id="1eb47-123">儲存並建置方案。</span><span class="sxs-lookup"><span data-stu-id="1eb47-123">Save and build the solution.</span></span>

2. <span data-ttu-id="1eb47-124">選取 [ **GettingStartedLib** ] 資料夾，然後從快捷方式功能表選取 [**設定為啟始專案**]。</span><span class="sxs-lookup"><span data-stu-id="1eb47-124">Select the **GettingStartedLib** folder, and then select **Set as Startup Project** from the shortcut menu.</span></span>

3. <span data-ttu-id="1eb47-125">從 [**啟始專案**] 中，從下拉式清單中選取 [ **GettingStartedLib** ]，然後選取 [**執行**] 或按**F5**。</span><span class="sxs-lookup"><span data-stu-id="1eb47-125">From **Startup Projects**, select **GettingStartedLib** from the drop-down list, then select **Run** or press **F5**.</span></span>

### <a name="test-the-application-from-a-command-prompt"></a><span data-ttu-id="1eb47-126">從命令提示字元測試應用程式</span><span class="sxs-lookup"><span data-stu-id="1eb47-126">Test the application from a command prompt</span></span>

1. <span data-ttu-id="1eb47-127">以系統管理員身分開啟命令提示字元，然後流覽至您的 Visual Studio 方案目錄。</span><span class="sxs-lookup"><span data-stu-id="1eb47-127">Open a command prompt as an administrator, and then navigate to your Visual Studio solution directory.</span></span>

2. <span data-ttu-id="1eb47-128">若要啟動服務：輸入*GettingStartedHost\bin\Debug\GettingStartedHost.exe*。</span><span class="sxs-lookup"><span data-stu-id="1eb47-128">To start the service: Enter *GettingStartedHost\bin\Debug\GettingStartedHost.exe*.</span></span>

3. <span data-ttu-id="1eb47-129">若要啟動用戶端：開啟另一個命令提示字元，流覽至您的 Visual Studio 方案目錄，然後輸入*GettingStartedClient\bin\Debug\GettingStartedClient.exe*。</span><span class="sxs-lookup"><span data-stu-id="1eb47-129">To start the client: Open another command prompt, navigate to your Visual Studio solution directory, then enter *GettingStartedClient\bin\Debug\GettingStartedClient.exe*.</span></span>

   <span data-ttu-id="1eb47-130">*GettingStartedHost.exe*會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="1eb47-130">*GettingStartedHost.exe* produces the following output:</span></span>

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

   <span data-ttu-id="1eb47-131">*GettingStartedClient.exe*會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="1eb47-131">*GettingStartedClient.exe* produces the following output:</span></span>

   ```text
   Add(100,15.99) = 115.99
   Subtract(145,76.54) = 68.46
   Multiply(9,81.25) = 731.25
   Divide(22,7) = 3.14285714285714

   Press <Enter> to terminate the client.
   ```

## <a name="next-steps"></a><span data-ttu-id="1eb47-132">接下來的步驟</span><span class="sxs-lookup"><span data-stu-id="1eb47-132">Next steps</span></span>

<span data-ttu-id="1eb47-133">您現在已完成 WCF 開始使用教學課程中的所有工作。</span><span class="sxs-lookup"><span data-stu-id="1eb47-133">You've now completed all the tasks in the WCF get started tutorial.</span></span> <span data-ttu-id="1eb47-134">在本教學課程中，您已了解如何：</span><span class="sxs-lookup"><span data-stu-id="1eb47-134">In this tutorial, you learned how to:</span></span>

<span data-ttu-id="1eb47-135">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="1eb47-135">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="1eb47-136">加入程式碼以使用 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="1eb47-136">Add code to use the WCF client.</span></span>
> - <span data-ttu-id="1eb47-137">測試 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="1eb47-137">Test the WCF client.</span></span>

<span data-ttu-id="1eb47-138">如果您在任何步驟中遇到問題或錯誤，請遵循疑難排解文章中的步驟來修正它們。</span><span class="sxs-lookup"><span data-stu-id="1eb47-138">If you have problems or errors in any of the steps, follow the steps in the troubleshooting article to fix them.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1eb47-139">開始使用 WCF 教學課程的疑難排解</span><span class="sxs-lookup"><span data-stu-id="1eb47-139">Troubleshoot the Get started with WCF tutorials</span></span>](troubleshooting-the-getting-started-tutorial.md)
