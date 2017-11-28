---
title: "如何：非同步呼叫 Web 服務 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6410ef93a706c047047aa24b3d47f8915e928015
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a><span data-ttu-id="93439-102">如何：非同步呼叫 Web 服務 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93439-102">How to: Call a Web Service Asynchronously (Visual Basic)</span></span>
<span data-ttu-id="93439-103">這個範例會將處理常式連接到 Web 服務的非同步處理常式事件，讓它能擷取非同步方法呼叫的結果。</span><span class="sxs-lookup"><span data-stu-id="93439-103">This example attaches a handler to a Web service's asynchronous handler event, so that it can retrieve the result of an asynchronous method call.</span></span> <span data-ttu-id="93439-104">此範例使用 DemoTemperatureService Web 服務，網址為 http://www.xmethods.net。</span><span class="sxs-lookup"><span data-stu-id="93439-104">This example used the DemoTemperatureService Web service at http://www.xmethods.net.</span></span>  
  
 <span data-ttu-id="93439-105">當您在 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] 整合式開發環境 (IDE) 中的專案參考 Web 服務時，它會加到 `My.WebServices` 物件，且 IDE 會產生用戶端 Proxy 類別來存取指定的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="93439-105">When you reference a Web service in your project in the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Integrated Development Environment (IDE), it is added to the `My.WebServices` object, and the IDE generates a client proxy class to access a specified Web service</span></span>  
  
 <span data-ttu-id="93439-106">Proxy 類別允許您同步呼叫 Web 服務方法，您的應用程式會在該處等候函式完成。</span><span class="sxs-lookup"><span data-stu-id="93439-106">The proxy class allows you to call the Web service methods synchronously, where your application waits for the function to complete.</span></span> <span data-ttu-id="93439-107">此外，Proxy 會建立額外的成員，協助非同步地呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="93439-107">In addition, the proxy creates additional members to help call the method asynchronously.</span></span> <span data-ttu-id="93439-108">針對每個 Web 服務函式 *NameOfWebServiceFunction*，Proxy 會建立一個 *NameOfWebServiceFunction*`Async` 副程式、一個 *NameOfWebServiceFunction*`Completed` 事件，以及一個 *NameOfWebServiceFunction*`CompletedEventArgs` 類別。</span><span class="sxs-lookup"><span data-stu-id="93439-108">For each Web service function, *NameOfWebServiceFunction*, the proxy creates a *NameOfWebServiceFunction*`Async` subroutine, a *NameOfWebServiceFunction*`Completed` event, and a *NameOfWebServiceFunction*`CompletedEventArgs` class.</span></span> <span data-ttu-id="93439-109">此範例示範如何使用非同步成員來存取 DemoTemperatureService Web 服務的 `getTemp` 函式。</span><span class="sxs-lookup"><span data-stu-id="93439-109">This example demonstrates how to use the asynchronous members to access the `getTemp` function of the DemoTemperatureService Web service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93439-110">這個程式碼在 Web 應用程式中無效，因為 ASP.NET 不支援 `My.WebServices` 物件。</span><span class="sxs-lookup"><span data-stu-id="93439-110">This code does not work in Web applications, because ASP.NET does not support the `My.WebServices` object.</span></span>  
  
### <a name="to-call-a-web-service-asynchronously"></a><span data-ttu-id="93439-111">非同步地呼叫 Web 服務</span><span class="sxs-lookup"><span data-stu-id="93439-111">To call a Web service asynchronously</span></span>  
  
1.  <span data-ttu-id="93439-112">參考 DemoTemperatureService Web 服務，網址為 http://www.xmethods.net。</span><span class="sxs-lookup"><span data-stu-id="93439-112">Reference the DemoTemperatureService Web service at http://www.xmethods.net.</span></span> <span data-ttu-id="93439-113">位址是</span><span class="sxs-lookup"><span data-stu-id="93439-113">The address is</span></span>  
  
    ```  
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl  
    ```  
  
2.  <span data-ttu-id="93439-114">新增 `getTempCompleted` 事件的事件處理常式：</span><span class="sxs-lookup"><span data-stu-id="93439-114">Add an event handler for the `getTempCompleted` event:</span></span>  
  
    ```  
    Private Sub getTempCompletedHandler(ByVal sender As Object,   
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)  
  
        MsgBox("Temperature: " & e.Result)  
    End Sub  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="93439-115">您不能使用 `Handles` 陳述式來產生事件處理常式與 `My.WebServices` 物件事件的關聯。</span><span class="sxs-lookup"><span data-stu-id="93439-115">You cannot use the `Handles` statement to associate an event handler with the `My.WebServices` object's events.</span></span>  
  
3.  <span data-ttu-id="93439-116">新增欄位以追蹤事件處理常式是否已加到 `getTempCompleted` 事件：</span><span class="sxs-lookup"><span data-stu-id="93439-116">Add a field to track if the event handler has been added to the `getTempCompleted` event:</span></span>  
  
    ```  
    Private handlerAttached As Boolean = False  
    ```  
  
4.  <span data-ttu-id="93439-117">新增方法以視需要將事件處理常式加到 `getTempCompleted` 事件，以及呼叫 `getTempAsynch` 方法：</span><span class="sxs-lookup"><span data-stu-id="93439-117">Add a method to add the event handler to the `getTempCompleted` event, if necessary, and to call the `getTempAsynch` method:</span></span>  
  
    ```  
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
  
     <span data-ttu-id="93439-118">若要非同步地呼叫 `getTemp` Web 方法，請呼叫 `CallGetTempAsync` 方法。</span><span class="sxs-lookup"><span data-stu-id="93439-118">To call the `getTemp` Web method asynchronously, call the `CallGetTempAsync` method.</span></span> <span data-ttu-id="93439-119">當 Web 方法完成時，它的傳回值會傳到 `getTempCompletedHandler` 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="93439-119">When the Web method finishes, its return value is passed to the `getTempCompletedHandler` event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93439-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93439-120">See Also</span></span>  
 [<span data-ttu-id="93439-121">存取應用程式 Web 服務</span><span class="sxs-lookup"><span data-stu-id="93439-121">Accessing Application Web Services</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)  
 [<span data-ttu-id="93439-122">My.WebServices 物件</span><span class="sxs-lookup"><span data-stu-id="93439-122">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)
