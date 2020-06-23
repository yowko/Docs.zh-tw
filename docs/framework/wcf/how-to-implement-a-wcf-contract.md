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
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a>教學課程：執行 Windows Communication Foundation 服務合約

本教學課程說明建立基本 Windows Communication Foundation （WCF）應用程式所需的五個工作中的第二個。 如需教學課程的總覽，請參閱[教學課程：開始使用 Windows Communication Foundation 應用程式](getting-started-tutorial.md)。

建立 WCF 應用程式的下一個步驟是加入程式碼，以執行您在上一個步驟中建立的 WCF 服務介面。 在此步驟中，您會建立名為的類別，以執行 `CalculatorService` 使用者定義的 `ICalculator` 介面。 下列程式碼中的每個方法都會呼叫計算機作業，並將文字寫入主控台以進行測試。

在本教學課程中，您會了解如何：
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

編輯**GettingStartedLib**中的**App.config** ，以反映您對程式碼所做的變更。

- 針對 Visual c # 專案：
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

在本教學課程中，您已了解如何：
> [!div class="checklist"]
>
> - 加入程式碼來執行 WCF 服務合約。
> - 建置方案。

請前進到下一個教學課程，以瞭解如何執行 WCF 服務。

> [!div class="nextstepaction"]
> [教學課程：裝載和執行基本 WCF 服務](how-to-host-and-run-a-basic-wcf-service.md)
