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
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a>教學課程：實作 Windows Communication Foundation 服務合約

本教學課程說明建立基本的 Windows Communication Foundation (WCF) 應用程式所需的五個工作的第二個。 如需教學課程的概觀，請參閱[教學課程：開始使用 Windows Communication Foundation 應用程式](getting-started-tutorial.md)。

建立 WCF 應用程式的下一個步驟是新增程式碼來實作您在上一個步驟中建立的 WCF 服務介面。 在此步驟中，您會建立名為類別`CalculatorService`它會實作使用者定義`ICalculator`介面。 下列程式碼中的每個方法呼叫計算機作業，並將文字寫入至主控台，以進行測試。 

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> - 將實作 WCF 服務合約的程式碼。
> - 建置方案。

## <a name="add-code-to-implement-the-wcf-service-contract"></a>加入程式碼來實作 WCF 服務合約

在  **GettingStartedLib**，開啟**Service1.cs**或是**Service1.vb**檔案，並以下列程式碼取代其程式碼：

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

編輯**App.config**中**GettingStartedLib**以反映所做的變更您對程式碼。
   - 視覺效果C#專案：
       - 變更至第 14 行 `<service name="GettingStartedLib.CalculatorService">`
       - 變更第 17 行至 `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
       - 變更到第 22 行 `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`

   - 如果是 Visual Basic 專案：
       - 變更至第 14 行 `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`
       - 變更第 17 行至 `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
       - 變更到第 22 行 `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`


## <a name="compile-the-code"></a>編譯程式碼

建置方案，以確認沒有任何編譯錯誤。 如果您使用 Visual Studio 中，在**建置**功能表中，選取**建置方案**(或按下**Ctrl**+**Shift** + **B**)。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> - 將實作 WCF 服務合約的程式碼。
> - 建置方案。

請前進到下一個教學課程，以了解如何執行 WCF 服務。

> [!div class="nextstepaction"]
> [教學課程：裝載和執行基本的 WCF 服務](how-to-host-and-run-a-basic-wcf-service.md)
