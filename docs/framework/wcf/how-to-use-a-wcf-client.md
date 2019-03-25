---
title: 教學課程：使用 Windows Communication Foundation 用戶端
ms.date: 03/19/2019
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: 4d883277f795ea84c59aee91ffcb9b9802b0933b
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411716"
---
# <a name="tutorial-use-a-windows-communication-foundation-client"></a><span data-ttu-id="2a7e1-102">教學課程：使用 Windows Communication Foundation 用戶端</span><span class="sxs-lookup"><span data-stu-id="2a7e1-102">Tutorial: Use a Windows Communication Foundation client</span></span>

<span data-ttu-id="2a7e1-103">本教學課程說明建立基本的 Windows Communication Foundation (WCF) 應用程式所需的五個工作的最後一個。</span><span class="sxs-lookup"><span data-stu-id="2a7e1-103">This tutorial describes the last of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="2a7e1-104">如需教學課程的概觀，請參閱[教學課程：開始使用 Windows Communication Foundation 應用程式](getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="2a7e1-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="2a7e1-105">您已建立並設定 Windows Communication Foundation (WCF) proxy 之後，您會建立用戶端執行個體，並編譯用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="2a7e1-105">After you've created and configured a Windows Communication Foundation (WCF) proxy, you create a client instance and compile the client application.</span></span> <span data-ttu-id="2a7e1-106">您再使用它來與 WCF 服務進行通訊。</span><span class="sxs-lookup"><span data-stu-id="2a7e1-106">You then use it to communicate with the WCF service.</span></span> 

<span data-ttu-id="2a7e1-107">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="2a7e1-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="2a7e1-108">加入程式碼使用 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="2a7e1-108">Add code to use the WCF client.</span></span>
> - <span data-ttu-id="2a7e1-109">測試 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="2a7e1-109">Test the WCF client.</span></span>

## <a name="add-code-to-use-the-wcf-client"></a><span data-ttu-id="2a7e1-110">加入程式碼來使用 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="2a7e1-110">Add code to use the WCF client</span></span>

<span data-ttu-id="2a7e1-111">用戶端程式碼會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="2a7e1-111">The client code does the following steps:</span></span>
- <span data-ttu-id="2a7e1-112">具現化 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="2a7e1-112">Instantiates the WCF client.</span></span>
- <span data-ttu-id="2a7e1-113">從產生的 Proxy 呼叫服務作業。</span><span class="sxs-lookup"><span data-stu-id="2a7e1-113">Calls the service operations from the generated proxy.</span></span>
- <span data-ttu-id="2a7e1-114">完成作業呼叫之後，請關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="2a7e1-114">Closes the client after the operation call is completed.</span></span>

<span data-ttu-id="2a7e1-115">開啟**Program.cs**或是**Module1.vb**從檔案**GettingStartedClient**專案，並以下列程式碼取代其程式碼：</span><span class="sxs-lookup"><span data-stu-id="2a7e1-115">Open the **Program.cs** or **Module1.vb** file from the **GettingStartedClient** project and replace its code with the following code:</span></span>

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

<span data-ttu-id="2a7e1-116">請注意`using`(視覺效果C#) 或`Imports`（適用於 Visual Basic) 陳述式匯入`GettingStartedClient.ServiceReference1`。</span><span class="sxs-lookup"><span data-stu-id="2a7e1-116">Notice the `using` (for Visual C#) or `Imports` (for Visual Basic) statement that imports `GettingStartedClient.ServiceReference1`.</span></span> <span data-ttu-id="2a7e1-117">此陳述式匯入 Visual Studio 產生的程式碼**加入服務參考**函式。</span><span class="sxs-lookup"><span data-stu-id="2a7e1-117">This statement imports the code that Visual Studio generated with the **Add Service Reference** function.</span></span> <span data-ttu-id="2a7e1-118">程式碼會具現化 WCF proxy，並呼叫每個計算機服務所公開的服務作業。</span><span class="sxs-lookup"><span data-stu-id="2a7e1-118">The code instantiates the WCF proxy and calls each of the service operations that the calculator service exposes.</span></span> <span data-ttu-id="2a7e1-119">然後，它會關閉 proxy 並結束程式。</span><span class="sxs-lookup"><span data-stu-id="2a7e1-119">It then closes the proxy and ends the program.</span></span>

## <a name="test-the-wcf-client"></a><span data-ttu-id="2a7e1-120">測試 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="2a7e1-120">Test the WCF client</span></span>

### <a name="test-the-application-from-visual-studio"></a><span data-ttu-id="2a7e1-121">測試應用程式從 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2a7e1-121">Test the application from Visual Studio</span></span>

1. <span data-ttu-id="2a7e1-122">儲存並建置方案。</span><span class="sxs-lookup"><span data-stu-id="2a7e1-122">Save and build the solution.</span></span>

2. <span data-ttu-id="2a7e1-123">選取  **GettingStartedLib**資料夾，然後再選取**設定為啟始專案**從捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="2a7e1-123">Select the **GettingStartedLib** folder, and then select **Set as Startup Project** from the shortcut menu.</span></span>

3. <span data-ttu-id="2a7e1-124">從**啟始專案**，選取**GettingStartedLib**從下拉式清單中，然後選取**執行**，或按**F5**。</span><span class="sxs-lookup"><span data-stu-id="2a7e1-124">From **Startup Projects**, select **GettingStartedLib** from the drop-down list, then select **Run** or press **F5**.</span></span>

### <a name="test-the-application-from-a-command-prompt"></a><span data-ttu-id="2a7e1-125">測試應用程式，從命令提示字元</span><span class="sxs-lookup"><span data-stu-id="2a7e1-125">Test the application from a command prompt</span></span>

1. <span data-ttu-id="2a7e1-126">開啟命令提示字元，身為管理員，，然後瀏覽至您的 Visual Studio 方案目錄。</span><span class="sxs-lookup"><span data-stu-id="2a7e1-126">Open a command prompt as an administrator, and then navigate to your Visual Studio solution directory.</span></span> 

2. <span data-ttu-id="2a7e1-127">若要啟動服務：請輸入*GettingStartedHost\bin\Debug\GettingStartedHost.exe*。</span><span class="sxs-lookup"><span data-stu-id="2a7e1-127">To start the service: Enter *GettingStartedHost\bin\Debug\GettingStartedHost.exe*.</span></span>

3. <span data-ttu-id="2a7e1-128">若要啟動用戶端：開啟另一個命令提示字元，瀏覽至您的 Visual Studio 方案目錄，然後輸入*GettingStartedClient\bin\Debug\GettingStartedClient.exe*。</span><span class="sxs-lookup"><span data-stu-id="2a7e1-128">To start the client: Open another command prompt, navigate to your Visual Studio solution directory, then enter *GettingStartedClient\bin\Debug\GettingStartedClient.exe*.</span></span>

   <span data-ttu-id="2a7e1-129">*GettingStartedHost.exe*產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="2a7e1-129">*GettingStartedHost.exe* produces the following output:</span></span>

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

   <span data-ttu-id="2a7e1-130">*GettingStartedClient.exe*產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="2a7e1-130">*GettingStartedClient.exe* produces the following output:</span></span>

   ```text
   Add(100,15.99) = 115.99
   Subtract(145,76.54) = 68.46
   Multiply(9,81.25) = 731.25
   Divide(22,7) = 3.14285714285714

   Press <Enter> to terminate the client.
   ```

## <a name="next-steps"></a><span data-ttu-id="2a7e1-131">後續步驟</span><span class="sxs-lookup"><span data-stu-id="2a7e1-131">Next steps</span></span>

<span data-ttu-id="2a7e1-132">您現在已在 WCF 快速入門教學課程中完成所有工作。</span><span class="sxs-lookup"><span data-stu-id="2a7e1-132">You've now completed all the tasks in the WCF get started tutorial.</span></span> <span data-ttu-id="2a7e1-133">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="2a7e1-133">In this tutorial, you learned how to:</span></span>

<span data-ttu-id="2a7e1-134">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="2a7e1-134">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="2a7e1-135">加入程式碼使用 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="2a7e1-135">Add code to use the WCF client.</span></span>
> - <span data-ttu-id="2a7e1-136">測試 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="2a7e1-136">Test the WCF client.</span></span>

<span data-ttu-id="2a7e1-137">如果您有問題或錯誤中的任何步驟，請依照下列修正它們的疑難排解文件中的步驟。</span><span class="sxs-lookup"><span data-stu-id="2a7e1-137">If you have problems or errors in any of the steps, follow the steps in the troubleshooting article to fix them.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2a7e1-138">疑難排解 Get 開始使用 WCF 的教學課程</span><span class="sxs-lookup"><span data-stu-id="2a7e1-138">Troubleshoot the Get started with WCF tutorials</span></span>](troubleshooting-the-getting-started-tutorial.md)

