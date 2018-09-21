---
title: HOW TO：實作 Windows Communication Foundation 服務合約
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: 569de6f49b56b46ccfeb22e9f0bd25bcf339b7e0
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46528784"
---
# <a name="how-to-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="a27f0-102">HOW TO：實作 Windows Communication Foundation 服務合約</span><span class="sxs-lookup"><span data-stu-id="a27f0-102">How to: Implement a Windows Communication Foundation Service Contract</span></span>

<span data-ttu-id="a27f0-103">這是建立基本 Windows Communication Foundation (WCF) 服務和用戶端可呼叫服務所需的六個工作的第二個。</span><span class="sxs-lookup"><span data-stu-id="a27f0-103">This is the second of six tasks required to create a basic Windows Communication Foundation (WCF) service and a client that can call the service.</span></span> <span data-ttu-id="a27f0-104">如需這六項工作的概觀，請參閱 <<c0> [ 入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)主題。</span><span class="sxs-lookup"><span data-stu-id="a27f0-104">For an overview of all six tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>

<span data-ttu-id="a27f0-105">建立 WCF 應用程式的下一步是實作服務介面。</span><span class="sxs-lookup"><span data-stu-id="a27f0-105">The next step in creating a WCF application is to implement the service interface.</span></span> <span data-ttu-id="a27f0-106">其中包含建立名稱為 `CalculatorService` 的類別，該類別會實作使用者定義的 `ICalculator` 介面。</span><span class="sxs-lookup"><span data-stu-id="a27f0-106">This involves creating a class called `CalculatorService` that implements the user-defined `ICalculator` interface..</span></span>

## <a name="to-implement-a-wcf-service-contract"></a><span data-ttu-id="a27f0-107">實作 WCF 服務合約</span><span class="sxs-lookup"><span data-stu-id="a27f0-107">To implement a WCF service contract</span></span>

<span data-ttu-id="a27f0-108">開啟 Service1.cs 或 Service1.vb 檔案，並加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="a27f0-108">Open the Service1.cs or Service1.vb file and add the following code:</span></span>

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

<span data-ttu-id="a27f0-109">每個方法會實作計算機作業，並將一些文字寫入主控台以簡化測試。</span><span class="sxs-lookup"><span data-stu-id="a27f0-109">Each method implements the calculator operation and writes some text to the console to make testing easier.</span></span>

## <a name="example"></a><span data-ttu-id="a27f0-110">範例</span><span class="sxs-lookup"><span data-stu-id="a27f0-110">Example</span></span>

<span data-ttu-id="a27f0-111">下列程式碼同時說明可定義合約的介面，以及介面的實作。</span><span class="sxs-lookup"><span data-stu-id="a27f0-111">The following code shows both the interface that defines the contract and the implementation of the interface.</span></span>

```csharp
using System;
using System.ServiceModel;

namespace GettingStartedLib
{
    [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
    public interface ICalculator
    {
        [OperationContract]
        double Add(double n1, double n2);
        [OperationContract]
        double Subtract(double n1, double n2);
        [OperationContract]
        double Multiply(double n1, double n2);
        [OperationContract]
        double Divide(double n1, double n2);
    }
}
```

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

    <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
    Public Interface ICalculator

        <OperationContract()> _
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()> _
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()> _
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()> _
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
    End Interface
End Namespace
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

## <a name="compile-the-code"></a><span data-ttu-id="a27f0-112">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="a27f0-112">Compile the code</span></span>

<span data-ttu-id="a27f0-113">建置方案，以確保沒有任何編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="a27f0-113">Build the solution to ensure there are no compilation errors.</span></span> <span data-ttu-id="a27f0-114">如果您使用 Visual Studio 中，在**建置**功能表中，選取**建置方案**(或按下**Ctrl**+**Shift** + **B**)。</span><span class="sxs-lookup"><span data-stu-id="a27f0-114">If you're using Visual Studio, on the **Build** menu select **Build Solution** (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="next-steps"></a><span data-ttu-id="a27f0-115">後續步驟</span><span class="sxs-lookup"><span data-stu-id="a27f0-115">Next steps</span></span>

<span data-ttu-id="a27f0-116">現在，服務合約已建立且已實作。</span><span class="sxs-lookup"><span data-stu-id="a27f0-116">Now the service contract is created and implemented.</span></span> <span data-ttu-id="a27f0-117">在下一個步驟中，您可以執行服務。</span><span class="sxs-lookup"><span data-stu-id="a27f0-117">In the next step, you run the service.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a27f0-118">如何：裝載及執行基本服務</span><span class="sxs-lookup"><span data-stu-id="a27f0-118">How to: Host and Run a Basic Service</span></span>](../../../docs/framework/wcf/how-to-host-and-run-a-basic-wcf-service.md)

<span data-ttu-id="a27f0-119">如需針對資訊進行疑難排解，請參閱[針對使用者入門教學課程進行疑難排解](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="a27f0-119">For troubleshooting information, see [Troubleshooting the Getting Started Tutorial](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a27f0-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a27f0-120">See also</span></span>

- [<span data-ttu-id="a27f0-121">快速入門</span><span class="sxs-lookup"><span data-stu-id="a27f0-121">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [<span data-ttu-id="a27f0-122">自我裝載</span><span class="sxs-lookup"><span data-stu-id="a27f0-122">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)