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
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a>教程：實現 Windows 通信基礎服務協定

本教程介紹創建基本 Windows 通信基礎 （WCF） 應用程式所需的五項任務中的第二個。 有關教程的概述，請參閱[教程：開始使用 Windows 通信基礎應用程式](getting-started-tutorial.md)。

創建 WCF 應用程式的下一步是添加代碼以實現您在上一步中創建的 WCF 服務介面。 在此步驟中，您將創建一個名為`CalculatorService`實現使用者定義的`ICalculator`介面的類。 以下代碼中的每個方法調用計算機操作，並將文本寫入主控台以進行測試。

在本教學課程中，您會了解如何：
> [!div class="checklist"]
>
> - 添加代碼以實現 WCF 服務協定。
> - 建置方案。

## <a name="add-code-to-implement-the-wcf-service-contract"></a>添加代碼以實現 WCF 服務協定

在**入門計畫中**，打開**Service1.cs**或**Service1.vb**檔，並將其代碼替換為以下代碼：

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

## <a name="edit-appconfig"></a>編輯應用程式.配置

在**入門Lib**中編輯**App.config，** 以反映對代碼所做的更改。

- 對於視覺化 C# 專案：
  - 將行 14 更改為`<service name="GettingStartedLib.CalculatorService">`
  - 將行 17 更改為`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - 將行 22 更改為`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`

- 如果是 Visual Basic 專案：
  - 將行 14 更改為`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`
  - 將行 17 更改為`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - 將行 22 更改為`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`

## <a name="compile-the-code"></a>編譯程式碼

生成解決方案以驗證沒有任何編譯錯誤。 如果您使用的是視覺化工作室，請在 **"生成"** 功能表上選擇 **"生成解決方案**"（或按**Ctrl**+**Shift**+**B**）。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已了解如何：
> [!div class="checklist"]
>
> - 添加代碼以實現 WCF 服務協定。
> - 建置方案。

請先到下一教程，瞭解如何運行 WCF 服務。

> [!div class="nextstepaction"]
> [教程：託管並運行基本的 WCF 服務](how-to-host-and-run-a-basic-wcf-service.md)
