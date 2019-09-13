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
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a>教學課程：執行 Windows Communication Foundation 服務合約

本教學課程說明建立基本 Windows Communication Foundation （WCF）應用程式所需的五個工作中的第二個。 如需教學課程的總覽，請[參閱教學課程：Windows Communication Foundation 應用程式](getting-started-tutorial.md)入門。

建立 WCF 應用程式的下一個步驟是加入程式碼，以執行您在上一個步驟中建立的 WCF 服務介面。 在此步驟中，您會建立名`CalculatorService`為的類別，以執行`ICalculator`使用者定義的介面。 下列程式碼中的每個方法都會呼叫計算機作業，並將文字寫入主控台以進行測試。 

在本教學課程中，您將了解如何：
> [!div class="checklist"]
>
> - 加入程式碼來執行 WCF 服務合約。
> - 建置方案。

## <a name="add-code-to-implement-the-wcf-service-contract"></a>加入程式碼來執行 WCF 服務合約

在**GettingStartedLib**中，開啟**Service1.cs**或**Service1**檔案，並將其程式碼取代為下列程式碼：

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

## <a name="edit-appconfig"></a>編輯 App.config

編輯**GettingStartedLib**中的 app.config，以反映您對**程式**代碼所做的變更。

- 針對 Visual C#專案：
  - 將第14行變更為`<service name="GettingStartedLib.CalculatorService">`
  - 將第17行變更為`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - 將第22行變更為`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`

- 如果是 Visual Basic 專案：
  - 將第14行變更為`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`
  - 將第17行變更為`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - 將第22行變更為`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`

## <a name="compile-the-code"></a>編譯程式碼

建立解決方案，以確認沒有任何編譯錯誤。 如果您使用 Visual Studio，請在 [**建立**] 功能表上選取 [**建立方案**] （或按**Ctrl** + **Shift** + **B**）。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您將了解如何：
> [!div class="checklist"]
>
> - 加入程式碼來執行 WCF 服務合約。
> - 建置方案。

請前進到下一個教學課程，以瞭解如何執行 WCF 服務。

> [!div class="nextstepaction"]
> [教學課程：裝載和執行基本 WCF 服務](how-to-host-and-run-a-basic-wcf-service.md)
