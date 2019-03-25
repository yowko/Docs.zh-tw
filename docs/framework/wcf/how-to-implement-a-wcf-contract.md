---
title: 教學課程：實作 Windows Communication Foundation 服務合約
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: fcf96af11bae701585acd92001c8000125858449
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410078"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="ab108-102">教學課程：實作 Windows Communication Foundation 服務合約</span><span class="sxs-lookup"><span data-stu-id="ab108-102">Tutorial: Implement a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="ab108-103">本教學課程說明建立基本的 Windows Communication Foundation (WCF) 應用程式所需的五個工作的第二個。</span><span class="sxs-lookup"><span data-stu-id="ab108-103">This tutorial describes the second of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="ab108-104">如需教學課程的概觀，請參閱[教學課程：開始使用 Windows Communication Foundation 應用程式](getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="ab108-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="ab108-105">建立 WCF 應用程式的下一個步驟是新增程式碼來實作您在上一個步驟中建立的 WCF 服務介面。</span><span class="sxs-lookup"><span data-stu-id="ab108-105">The next step for creating a WCF application is to add code to implement the WCF service interface that you created in the previous step.</span></span> <span data-ttu-id="ab108-106">在此步驟中，您會建立名為類別`CalculatorService`它會實作使用者定義`ICalculator`介面。</span><span class="sxs-lookup"><span data-stu-id="ab108-106">In this step, you create a class named `CalculatorService` that implements the user-defined `ICalculator` interface.</span></span> <span data-ttu-id="ab108-107">下列程式碼中的每個方法呼叫計算機作業，並將文字寫入至主控台，以進行測試。</span><span class="sxs-lookup"><span data-stu-id="ab108-107">Each method in the following code calls a calculator operation and writes text to the console to test it.</span></span> 

<span data-ttu-id="ab108-108">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="ab108-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="ab108-109">將實作 WCF 服務合約的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ab108-109">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="ab108-110">建置方案。</span><span class="sxs-lookup"><span data-stu-id="ab108-110">Build the solution.</span></span>

## <a name="add-code-to-implement-the-wcf-service-contract"></a><span data-ttu-id="ab108-111">加入程式碼來實作 WCF 服務合約</span><span class="sxs-lookup"><span data-stu-id="ab108-111">Add code to implement the WCF service contract</span></span>

<span data-ttu-id="ab108-112">在  **GettingStartedLib**，開啟**Service1.cs**或是**Service1.vb**檔案，並以下列程式碼取代其程式碼：</span><span class="sxs-lookup"><span data-stu-id="ab108-112">In **GettingStartedLib**, open the **Service1.cs** or **Service1.vb** file and replace its code with the following code:</span></span>

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

## <a name="edit-appconfig"></a><span data-ttu-id="ab108-113">編輯 App.config</span><span class="sxs-lookup"><span data-stu-id="ab108-113">Edit App.config</span></span>

<span data-ttu-id="ab108-114">編輯**App.config**中**GettingStartedLib**以反映所做的變更您對程式碼。</span><span class="sxs-lookup"><span data-stu-id="ab108-114">Edit **App.config** in **GettingStartedLib** to reflect the changes you made to the code.</span></span>
   - <span data-ttu-id="ab108-115">視覺效果C#專案：</span><span class="sxs-lookup"><span data-stu-id="ab108-115">For Visual C# projects:</span></span>
       - <span data-ttu-id="ab108-116">變更至第 14 行 `<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="ab108-116">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
       - <span data-ttu-id="ab108-117">變更第 17 行至 `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="ab108-117">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
       - <span data-ttu-id="ab108-118">變更到第 22 行 `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="ab108-118">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>

   - <span data-ttu-id="ab108-119">如果是 Visual Basic 專案：</span><span class="sxs-lookup"><span data-stu-id="ab108-119">For Visual Basic projects:</span></span>
       - <span data-ttu-id="ab108-120">變更至第 14 行 `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="ab108-120">Change line 14 to `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span></span>
       - <span data-ttu-id="ab108-121">變更第 17 行至 `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="ab108-121">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
       - <span data-ttu-id="ab108-122">變更到第 22 行 `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="ab108-122">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span></span>


## <a name="compile-the-code"></a><span data-ttu-id="ab108-123">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="ab108-123">Compile the code</span></span>

<span data-ttu-id="ab108-124">建置方案，以確認沒有任何編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="ab108-124">Build the solution to verify there aren't any compilation errors.</span></span> <span data-ttu-id="ab108-125">如果您使用 Visual Studio 中，在**建置**功能表中，選取**建置方案**(或按下**Ctrl**+**Shift** + **B**)。</span><span class="sxs-lookup"><span data-stu-id="ab108-125">If you're using Visual Studio, on the **Build** menu select **Build Solution** (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="next-steps"></a><span data-ttu-id="ab108-126">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ab108-126">Next steps</span></span>

<span data-ttu-id="ab108-127">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="ab108-127">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="ab108-128">將實作 WCF 服務合約的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ab108-128">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="ab108-129">建置方案。</span><span class="sxs-lookup"><span data-stu-id="ab108-129">Build the solution.</span></span>

<span data-ttu-id="ab108-130">請前進到下一個教學課程，以了解如何執行 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="ab108-130">Advance to the next tutorial to learn how to run the WCF service.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ab108-131">教學課程：裝載和執行基本的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="ab108-131">Tutorial: Host and run a basic WCF service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)
