---
title: 教程：實現 Windows 通信基礎服務協定
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: debdeeac7064f5bae21622b2d9de84a4d8a0e66f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184060"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="f9129-102">教程：實現 Windows 通信基礎服務協定</span><span class="sxs-lookup"><span data-stu-id="f9129-102">Tutorial: Implement a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="f9129-103">本教程介紹創建基本 Windows 通信基礎 （WCF） 應用程式所需的五項任務中的第二個。</span><span class="sxs-lookup"><span data-stu-id="f9129-103">This tutorial describes the second of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="f9129-104">有關教程的概述，請參閱[教程：開始使用 Windows 通信基礎應用程式](getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="f9129-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="f9129-105">創建 WCF 應用程式的下一步是添加代碼以實現您在上一步中創建的 WCF 服務介面。</span><span class="sxs-lookup"><span data-stu-id="f9129-105">The next step for creating a WCF application is to add code to implement the WCF service interface that you created in the previous step.</span></span> <span data-ttu-id="f9129-106">在此步驟中，您將創建一個名為`CalculatorService`實現使用者定義的`ICalculator`介面的類。</span><span class="sxs-lookup"><span data-stu-id="f9129-106">In this step, you create a class named `CalculatorService` that implements the user-defined `ICalculator` interface.</span></span> <span data-ttu-id="f9129-107">以下代碼中的每個方法調用計算機操作，並將文本寫入主控台以進行測試。</span><span class="sxs-lookup"><span data-stu-id="f9129-107">Each method in the following code calls a calculator operation and writes text to the console to test it.</span></span>

<span data-ttu-id="f9129-108">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="f9129-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="f9129-109">添加代碼以實現 WCF 服務協定。</span><span class="sxs-lookup"><span data-stu-id="f9129-109">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="f9129-110">建置方案。</span><span class="sxs-lookup"><span data-stu-id="f9129-110">Build the solution.</span></span>

## <a name="add-code-to-implement-the-wcf-service-contract"></a><span data-ttu-id="f9129-111">添加代碼以實現 WCF 服務協定</span><span class="sxs-lookup"><span data-stu-id="f9129-111">Add code to implement the WCF service contract</span></span>

<span data-ttu-id="f9129-112">在**入門計畫中**，打開**Service1.cs**或**Service1.vb**檔，並將其代碼替換為以下代碼：</span><span class="sxs-lookup"><span data-stu-id="f9129-112">In **GettingStartedLib**, open the **Service1.cs** or **Service1.vb** file and replace its code with the following code:</span></span>

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

## <a name="edit-appconfig"></a><span data-ttu-id="f9129-113">編輯應用程式.配置</span><span class="sxs-lookup"><span data-stu-id="f9129-113">Edit App.config</span></span>

<span data-ttu-id="f9129-114">在**入門Lib**中編輯**App.config，** 以反映對代碼所做的更改。</span><span class="sxs-lookup"><span data-stu-id="f9129-114">Edit **App.config** in **GettingStartedLib** to reflect the changes you made to the code.</span></span>

- <span data-ttu-id="f9129-115">對於視覺化 C# 專案：</span><span class="sxs-lookup"><span data-stu-id="f9129-115">For Visual C# projects:</span></span>
  - <span data-ttu-id="f9129-116">將行 14 更改為`<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="f9129-116">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="f9129-117">將行 17 更改為`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="f9129-117">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="f9129-118">將行 22 更改為`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="f9129-118">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>

- <span data-ttu-id="f9129-119">如果是 Visual Basic 專案：</span><span class="sxs-lookup"><span data-stu-id="f9129-119">For Visual Basic projects:</span></span>
  - <span data-ttu-id="f9129-120">將行 14 更改為`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="f9129-120">Change line 14 to `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="f9129-121">將行 17 更改為`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="f9129-121">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="f9129-122">將行 22 更改為`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="f9129-122">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="f9129-123">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="f9129-123">Compile the code</span></span>

<span data-ttu-id="f9129-124">生成解決方案以驗證沒有任何編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="f9129-124">Build the solution to verify there aren't any compilation errors.</span></span> <span data-ttu-id="f9129-125">如果您使用的是視覺化工作室，請在 **"生成"** 功能表上選擇 **"生成解決方案**"（或按**Ctrl**+**Shift**+**B**）。</span><span class="sxs-lookup"><span data-stu-id="f9129-125">If you're using Visual Studio, on the **Build** menu select **Build Solution** (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="next-steps"></a><span data-ttu-id="f9129-126">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f9129-126">Next steps</span></span>

<span data-ttu-id="f9129-127">在本教學課程中，您已了解如何：</span><span class="sxs-lookup"><span data-stu-id="f9129-127">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="f9129-128">添加代碼以實現 WCF 服務協定。</span><span class="sxs-lookup"><span data-stu-id="f9129-128">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="f9129-129">建置方案。</span><span class="sxs-lookup"><span data-stu-id="f9129-129">Build the solution.</span></span>

<span data-ttu-id="f9129-130">請先到下一教程，瞭解如何運行 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="f9129-130">Advance to the next tutorial to learn how to run the WCF service.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f9129-131">教程：託管並運行基本的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="f9129-131">Tutorial: Host and run a basic WCF service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)
