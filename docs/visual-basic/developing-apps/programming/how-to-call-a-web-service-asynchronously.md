---
title: HOW TO：非同步呼叫 Web 服務 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
ms.openlocfilehash: 01d2fad6be94f23457ba37cbb15521765e0bea17
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376197"
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a>作法：非同步呼叫 Web 服務 (Visual Basic)

這個範例會將處理常式連接到 Web 服務的非同步處理常式事件，讓它能擷取非同步方法呼叫的結果。 此範例使用 DemoTemperatureService Web 服務，網址為 `http://www.xmethods.net`。

當您在 Visual Studio 整合式開發環境 (IDE) 中的專案參考 Web 服務時，會將它新增至 `My.WebServices` 物件，且 IDE 會產生用戶端 Proxy 類別來存取指定的 Web 服務

Proxy 類別允許您同步呼叫 Web 服務方法，您的應用程式會在該處等候函式完成。 此外，Proxy 會建立額外的成員，協助非同步地呼叫方法。 針對每個 Web 服務函式 *NameOfWebServiceFunction*，Proxy 會建立一個 *NameOfWebServiceFunction*`Async` 副程式、一個 *NameOfWebServiceFunction*`Completed` 事件，以及一個 *NameOfWebServiceFunction*`CompletedEventArgs` 類別。 此範例示範如何使用非同步成員來存取 DemoTemperatureService Web 服務的 `getTemp` 函式。

> [!NOTE]
> 這個程式碼在 Web 應用程式中無效，因為 ASP.NET 不支援 `My.WebServices` 物件。

### <a name="to-call-a-web-service-asynchronously"></a>非同步地呼叫 Web 服務

1. 參考 DemoTemperatureService Web 服務，網址為 `http://www.xmethods.net`。 位址是

    ```
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl
    ```

2. 新增 `getTempCompleted` 事件的事件處理常式：

    ```vb
    Private Sub getTempCompletedHandler(ByVal sender As Object,
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)

        MsgBox("Temperature: " & e.Result)
    End Sub
    ```

    > [!NOTE]
    > 您不能使用 `Handles` 陳述式來產生事件處理常式與 `My.WebServices` 物件事件的關聯。

3. 新增欄位以追蹤事件處理常式是否已加到 `getTempCompleted` 事件：

    ```vb
    Private handlerAttached As Boolean = False
    ```

4. 新增方法以視需要將事件處理常式加到 `getTempCompleted` 事件，以及呼叫 `getTempAsync` 方法：

    ```vb
    Sub CallGetTempAsync(ByVal zipCode As Integer)
        If Not handlerAttached Then
            AddHandler My.WebServices.
                TemperatureService.getTempCompleted,
                AddressOf Me.TS_getTempCompleted
            handlerAttached = True
        End If
        My.WebServices.TemperatureService.getTempAsync(zipCode)
    End Sub
    ```

    若要非同步地呼叫 `getTemp` Web 方法，請呼叫 `CallGetTempAsync` 方法。 當 Web 方法完成時，它的傳回值會傳到 `getTempCompletedHandler` 事件處理常式。

## <a name="see-also"></a>另請參閱

- [存取應用程式 Web 服務](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
- [My.WebServices 物件](../../../visual-basic/language-reference/objects/my-webservices-object.md)
