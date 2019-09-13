---
title: 教學課程：執行 Windows Communication Foundation 服務合約
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: 05923dc0a2223da5e5fcda483abc1ee1dd2d643f
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928702"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="5f241-102">教學課程：執行 Windows Communication Foundation 服務合約</span><span class="sxs-lookup"><span data-stu-id="5f241-102">Tutorial: Implement a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="5f241-103">本教學課程說明建立基本 Windows Communication Foundation （WCF）應用程式所需的五個工作中的第二個。</span><span class="sxs-lookup"><span data-stu-id="5f241-103">This tutorial describes the second of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="5f241-104">如需教學課程的總覽，請[參閱教學課程：Windows Communication Foundation 應用程式](getting-started-tutorial.md)入門。</span><span class="sxs-lookup"><span data-stu-id="5f241-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="5f241-105">建立 WCF 應用程式的下一個步驟是加入程式碼，以執行您在上一個步驟中建立的 WCF 服務介面。</span><span class="sxs-lookup"><span data-stu-id="5f241-105">The next step for creating a WCF application is to add code to implement the WCF service interface that you created in the previous step.</span></span> <span data-ttu-id="5f241-106">在此步驟中，您會建立名`CalculatorService`為的類別，以執行`ICalculator`使用者定義的介面。</span><span class="sxs-lookup"><span data-stu-id="5f241-106">In this step, you create a class named `CalculatorService` that implements the user-defined `ICalculator` interface.</span></span> <span data-ttu-id="5f241-107">下列程式碼中的每個方法都會呼叫計算機作業，並將文字寫入主控台以進行測試。</span><span class="sxs-lookup"><span data-stu-id="5f241-107">Each method in the following code calls a calculator operation and writes text to the console to test it.</span></span> 

<span data-ttu-id="5f241-108">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="5f241-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="5f241-109">加入程式碼來執行 WCF 服務合約。</span><span class="sxs-lookup"><span data-stu-id="5f241-109">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="5f241-110">建置方案。</span><span class="sxs-lookup"><span data-stu-id="5f241-110">Build the solution.</span></span>

## <a name="add-code-to-implement-the-wcf-service-contract"></a><span data-ttu-id="5f241-111">加入程式碼來執行 WCF 服務合約</span><span class="sxs-lookup"><span data-stu-id="5f241-111">Add code to implement the WCF service contract</span></span>

<span data-ttu-id="5f241-112">在**GettingStartedLib**中，開啟**Service1.cs**或**Service1**檔案，並將其程式碼取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="5f241-112">In **GettingStartedLib**, open the **Service1.cs** or **Service1.vb** file and replace its code with the following code:</span></span>

```csharp
using System;
using System.ServiceModel;

namespace GettingStartedLib
{
    public class CalculatorService : ICalculator
    {
        public double Add(double n1, double n2)
        {
            double result = n1 + n2;
            Console.WriteLine("Received Add({0},{1})", n1, n2);
            // Code added to write output to the console window.
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Subtract(double n1, double n2)
        {
            double result = n1 - n2;
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Multiply(double n1, double n2)
        {
            double result = n1 * n2;
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Divide(double n1, double n2)
        {
            double result = n1 / n2;
            Console.WriteLine("Received Divide({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
    }
}
```

```vb
Imports System.ServiceModel

Namespace GettingStartedLib

    Public Class CalculatorService
        Implements ICalculator

        Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add
            Dim result As Double = n1 + n2
            ' Code added to write output to the console window.
            Console.WriteLine("Received Add({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result
        End Function

        Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract
            Dim result As Double = n1 - n2
            Console.WriteLine("Received Subtract({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply
            Dim result As Double = n1 * n2
            Console.WriteLine("Received Multiply({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide
            Dim result As Double = n1 / n2
            Console.WriteLine("Received Divide({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function
    End Class
End Namespace
```

## <a name="edit-appconfig"></a><span data-ttu-id="5f241-113">編輯 App.config</span><span class="sxs-lookup"><span data-stu-id="5f241-113">Edit App.config</span></span>

<span data-ttu-id="5f241-114">編輯**GettingStartedLib**中的 app.config，以反映您對**程式**代碼所做的變更。</span><span class="sxs-lookup"><span data-stu-id="5f241-114">Edit **App.config** in **GettingStartedLib** to reflect the changes you made to the code.</span></span>

- <span data-ttu-id="5f241-115">針對 Visual C#專案：</span><span class="sxs-lookup"><span data-stu-id="5f241-115">For Visual C# projects:</span></span>
  - <span data-ttu-id="5f241-116">將第14行變更為`<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="5f241-116">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="5f241-117">將第17行變更為`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="5f241-117">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="5f241-118">將第22行變更為`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="5f241-118">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>

- <span data-ttu-id="5f241-119">如果是 Visual Basic 專案：</span><span class="sxs-lookup"><span data-stu-id="5f241-119">For Visual Basic projects:</span></span>
  - <span data-ttu-id="5f241-120">將第14行變更為`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="5f241-120">Change line 14 to `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="5f241-121">將第17行變更為`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="5f241-121">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="5f241-122">將第22行變更為`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="5f241-122">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="5f241-123">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="5f241-123">Compile the code</span></span>

<span data-ttu-id="5f241-124">建立解決方案，以確認沒有任何編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="5f241-124">Build the solution to verify there aren't any compilation errors.</span></span> <span data-ttu-id="5f241-125">如果您使用 Visual Studio，請在 [**建立**] 功能表上選取 [**建立方案**] （或按**Ctrl** + **Shift** + **B**）。</span><span class="sxs-lookup"><span data-stu-id="5f241-125">If you're using Visual Studio, on the **Build** menu select **Build Solution** (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="next-steps"></a><span data-ttu-id="5f241-126">後續步驟</span><span class="sxs-lookup"><span data-stu-id="5f241-126">Next steps</span></span>

<span data-ttu-id="5f241-127">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="5f241-127">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="5f241-128">加入程式碼來執行 WCF 服務合約。</span><span class="sxs-lookup"><span data-stu-id="5f241-128">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="5f241-129">建置方案。</span><span class="sxs-lookup"><span data-stu-id="5f241-129">Build the solution.</span></span>

<span data-ttu-id="5f241-130">請前進到下一個教學課程，以瞭解如何執行 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="5f241-130">Advance to the next tutorial to learn how to run the WCF service.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5f241-131">教學課程：裝載和執行基本 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="5f241-131">Tutorial: Host and run a basic WCF service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)
