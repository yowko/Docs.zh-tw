---
title: 教學課程：執行 Windows Communication Foundation 服務合約
description: 瞭解如何加入程式碼，將 WCF 服務介面實作為一系列文章的一部分，協助您開始建立 WCF 應用程式。
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: 89f97610cccd42c2a5d298baa667327d077fd472
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244643"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="eaefe-103">教學課程：執行 Windows Communication Foundation 服務合約</span><span class="sxs-lookup"><span data-stu-id="eaefe-103">Tutorial: Implement a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="eaefe-104">本教學課程說明建立基本 Windows Communication Foundation （WCF）應用程式所需的五個工作中的第二個。</span><span class="sxs-lookup"><span data-stu-id="eaefe-104">This tutorial describes the second of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="eaefe-105">如需教學課程的總覽，請參閱[教學課程：開始使用 Windows Communication Foundation 應用程式](getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="eaefe-105">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="eaefe-106">建立 WCF 應用程式的下一個步驟是加入程式碼，以執行您在上一個步驟中建立的 WCF 服務介面。</span><span class="sxs-lookup"><span data-stu-id="eaefe-106">The next step for creating a WCF application is to add code to implement the WCF service interface that you created in the previous step.</span></span> <span data-ttu-id="eaefe-107">在此步驟中，您會建立名為的類別，以執行 `CalculatorService` 使用者定義的 `ICalculator` 介面。</span><span class="sxs-lookup"><span data-stu-id="eaefe-107">In this step, you create a class named `CalculatorService` that implements the user-defined `ICalculator` interface.</span></span> <span data-ttu-id="eaefe-108">下列程式碼中的每個方法都會呼叫計算機作業，並將文字寫入主控台以進行測試。</span><span class="sxs-lookup"><span data-stu-id="eaefe-108">Each method in the following code calls a calculator operation and writes text to the console to test it.</span></span>

<span data-ttu-id="eaefe-109">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="eaefe-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="eaefe-110">加入程式碼來執行 WCF 服務合約。</span><span class="sxs-lookup"><span data-stu-id="eaefe-110">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="eaefe-111">建置方案。</span><span class="sxs-lookup"><span data-stu-id="eaefe-111">Build the solution.</span></span>

## <a name="add-code-to-implement-the-wcf-service-contract"></a><span data-ttu-id="eaefe-112">加入程式碼來執行 WCF 服務合約</span><span class="sxs-lookup"><span data-stu-id="eaefe-112">Add code to implement the WCF service contract</span></span>

<span data-ttu-id="eaefe-113">在**GettingStartedLib**中，開啟**Service1.cs**或**Service1**檔案，並將其程式碼取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="eaefe-113">In **GettingStartedLib**, open the **Service1.cs** or **Service1.vb** file and replace its code with the following code:</span></span>

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

## <a name="edit-appconfig"></a><span data-ttu-id="eaefe-114">編輯 App.config</span><span class="sxs-lookup"><span data-stu-id="eaefe-114">Edit App.config</span></span>

<span data-ttu-id="eaefe-115">編輯**GettingStartedLib**中的**App.config** ，以反映您對程式碼所做的變更。</span><span class="sxs-lookup"><span data-stu-id="eaefe-115">Edit **App.config** in **GettingStartedLib** to reflect the changes you made to the code.</span></span>

- <span data-ttu-id="eaefe-116">針對 Visual c # 專案：</span><span class="sxs-lookup"><span data-stu-id="eaefe-116">For Visual C# projects:</span></span>
  - <span data-ttu-id="eaefe-117">將第14行變更為`<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="eaefe-117">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="eaefe-118">將第17行變更為`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="eaefe-118">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="eaefe-119">將第22行變更為`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="eaefe-119">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>

- <span data-ttu-id="eaefe-120">如果是 Visual Basic 專案：</span><span class="sxs-lookup"><span data-stu-id="eaefe-120">For Visual Basic projects:</span></span>
  - <span data-ttu-id="eaefe-121">將第14行變更為`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="eaefe-121">Change line 14 to `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="eaefe-122">將第17行變更為`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="eaefe-122">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="eaefe-123">將第22行變更為`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="eaefe-123">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="eaefe-124">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="eaefe-124">Compile the code</span></span>

<span data-ttu-id="eaefe-125">建立解決方案，以確認沒有任何編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="eaefe-125">Build the solution to verify there aren't any compilation errors.</span></span> <span data-ttu-id="eaefe-126">如果您使用 Visual Studio，請在 [**建立**] 功能表上選取 [**建立方案**] （或按**Ctrl** + **Shift** + **B**）。</span><span class="sxs-lookup"><span data-stu-id="eaefe-126">If you're using Visual Studio, on the **Build** menu select **Build Solution** (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="next-steps"></a><span data-ttu-id="eaefe-127">後續步驟</span><span class="sxs-lookup"><span data-stu-id="eaefe-127">Next steps</span></span>

<span data-ttu-id="eaefe-128">在本教學課程中，您已了解如何：</span><span class="sxs-lookup"><span data-stu-id="eaefe-128">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="eaefe-129">加入程式碼來執行 WCF 服務合約。</span><span class="sxs-lookup"><span data-stu-id="eaefe-129">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="eaefe-130">建置方案。</span><span class="sxs-lookup"><span data-stu-id="eaefe-130">Build the solution.</span></span>

<span data-ttu-id="eaefe-131">請前進到下一個教學課程，以瞭解如何執行 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="eaefe-131">Advance to the next tutorial to learn how to run the WCF service.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="eaefe-132">教學課程：裝載和執行基本 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="eaefe-132">Tutorial: Host and run a basic WCF service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)
