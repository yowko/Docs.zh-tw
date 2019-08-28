---
title: 使用複雜型別的 AJAX 服務範例
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: dce3e89449a036de7c4936963cfa0b36f3f08451
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045824"
---
# <a name="ajax-service-using-complex-types-sample"></a><span data-ttu-id="1396a-102">使用複雜型別的 AJAX 服務範例</span><span class="sxs-lookup"><span data-stu-id="1396a-102">AJAX Service Using Complex Types Sample</span></span>

<span data-ttu-id="1396a-103">這個範例會示範如何使用 Windows Communication Foundation (WCF) 來建立 ASP.NET 的非同步 JavaScript 和 XML (AJAX) 服務, 以建立複雜型別的實例, 並在服務和用戶端之間將它們當做 JavaScript 物件標記法 (JSON) 傳送。</span><span class="sxs-lookup"><span data-stu-id="1396a-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that creates instances of complex types and sends them between service and client as JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="1396a-104">您可以從 Web 瀏覽器用戶端使用 JavaScript 程式碼存取 AJAX 服務。</span><span class="sxs-lookup"><span data-stu-id="1396a-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="1396a-105">這個範例是以[基本 AJAX 服務](../../../../docs/framework/wcf/samples/basic-ajax-service.md)範例為基礎。</span><span class="sxs-lookup"><span data-stu-id="1396a-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>

<span data-ttu-id="1396a-106">WCF 中的 AJAX 支援已優化, 可透過<xref:System.Web.UI.ScriptManager>控制項與 ASP.NET ajax 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="1396a-106">AJAX support in WCF is optimized for use with ASP.NET AJAX through the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="1396a-107">如需搭配使用 WCF 與 ASP.NET AJAX 的範例, 請參閱[AJAX 範例](ajax.md)。</span><span class="sxs-lookup"><span data-stu-id="1396a-107">For an example of using WCF with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>

> [!NOTE]
> <span data-ttu-id="1396a-108">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="1396a-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="1396a-109">下列範例中的服務是不含 AJAX 特定程式碼的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="1396a-109">The service in the following sample is a WCF service with no AJAX-specific code.</span></span> <span data-ttu-id="1396a-110">因為沒有套用 <xref:System.ServiceModel.Web.WebGetAttribute> 屬性，所以會使用預設的 HTTP 動詞命令 ("POST")。</span><span class="sxs-lookup"><span data-stu-id="1396a-110">Because the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="1396a-111">服務有一項 `DoMath` 作業，它會傳回名為 `MathResult` 的複雜型別。</span><span class="sxs-lookup"><span data-stu-id="1396a-111">The service has one operation, `DoMath`, which returns a complex type named `MathResult`.</span></span> <span data-ttu-id="1396a-112">複雜型別是標準資料合約型別，其中也未包含 AJAX 特定程式碼。</span><span class="sxs-lookup"><span data-stu-id="1396a-112">The complex type is a standard data contract type, which also contains no AJAX-specific code.</span></span>

```csharp
[DataContract]
public class MathResult
{
    [DataMember]
    public double sum;
    [DataMember]
    public double difference;
    [DataMember]
    public double product;
    [DataMember]
    public double quotient;
}
```

<span data-ttu-id="1396a-113">您可以在服務上使用 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> 來建立 AJAX 端點，如基本 AJAX 服務範例所示。</span><span class="sxs-lookup"><span data-stu-id="1396a-113">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>

<span data-ttu-id="1396a-114">用戶端網頁 Complextypeclientpage.aspx 會包含 ASP.NET 和 JavaScript 程式碼, 可在使用者按一下頁面上的 [**執行計算**] 按鈕時叫用服務。</span><span class="sxs-lookup"><span data-stu-id="1396a-114">The client Web page ComplexTypeClientPage.aspx contains ASP.NET and JavaScript code to invoke the service when the user clicks the **Perform calculation** button on the page.</span></span> <span data-ttu-id="1396a-115">用來叫用服務的程式碼會使用 HTTP POST 來建立 JSON 主體並傳送它, 類似于[使用 HTTP post 範例的 AJAX 服務](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)。</span><span class="sxs-lookup"><span data-stu-id="1396a-115">The code to invoke the service constructs a JSON body and sends it using HTTP POST, similar to the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>

<span data-ttu-id="1396a-116">在服務呼叫成功後，您就可以存取在結果 JavaScript 物件上的個別資料成員 (`sum`、`difference`、`product` 和 `quotient`)。</span><span class="sxs-lookup"><span data-stu-id="1396a-116">After the service call succeeds, you can access the individual data members (`sum`, `difference`, `product` and `quotient`) on the resulting JavaScript object.</span></span>

```javascript
function onSuccess(mathResult){
     document.getElementById("sum").value = mathResult.sum;
     document.getElementById("difference").value = mathResult.difference;
     document.getElementById("product").value = mathResult.product;
     document.getElementById("quotient").value = mathResult.quotient;
}
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1396a-117">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="1396a-117">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="1396a-118">請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="1396a-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="1396a-119">如[建立 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中所述, 建立方案 ComplexTypeAjaxService。</span><span class="sxs-lookup"><span data-stu-id="1396a-119">Build the solution ComplexTypeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="1396a-120">流覽至`http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx` (請勿在瀏覽器中從專案目錄開啟 complextypeclientpage.aspx 會)。</span><span class="sxs-lookup"><span data-stu-id="1396a-120">Navigate to `http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx` (do not open ComplexTypeClientPage.aspx in the browser from the project directory).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1396a-121">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="1396a-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="1396a-122">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="1396a-122">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="1396a-123">如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。</span><span class="sxs-lookup"><span data-stu-id="1396a-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1396a-124">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="1396a-124">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`

## <a name="see-also"></a><span data-ttu-id="1396a-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1396a-125">See also</span></span>

- [<span data-ttu-id="1396a-126">基本 AJAX 服務</span><span class="sxs-lookup"><span data-stu-id="1396a-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
