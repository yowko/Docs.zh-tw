---
title: "使用複雜型別的 AJAX 服務範例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2c340d947082fa3141b417c1a7dfbce3b7ddf86f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ajax-service-using-complex-types-sample"></a><span data-ttu-id="d4333-102">使用複雜型別的 AJAX 服務範例</span><span class="sxs-lookup"><span data-stu-id="d4333-102">AJAX Service Using Complex Types Sample</span></span>
<span data-ttu-id="d4333-103">這個範例會示範如何使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 來建立 ASP.NET Asynchronous JavaScript 與 XML (AJAX) 服務，此服務會建立複雜型別的執行個體，並在服務和用戶端之間以 Javascript 物件標記法 (JSON) 進行傳送。</span><span class="sxs-lookup"><span data-stu-id="d4333-103">This sample demonstrates how to use [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that creates instances of complex types and sends them between service and client as JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="d4333-104">您可以從 Web 瀏覽器用戶端使用 JavaScript 程式碼存取 AJAX 服務。</span><span class="sxs-lookup"><span data-stu-id="d4333-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="d4333-105">這個範例是根據[基本 AJAX 服務](../../../../docs/framework/wcf/samples/basic-ajax-service.md)範例。</span><span class="sxs-lookup"><span data-stu-id="d4333-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="d4333-106">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的 AJAX 支援已針對透過 <xref:System.Web.UI.ScriptManager> 控制項來搭配 ASP.NET AJAX 使用完成最佳化。</span><span class="sxs-lookup"><span data-stu-id="d4333-106">AJAX support in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is optimized for use with ASP.NET AJAX through the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="d4333-107">如需使用[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]與 ASP.NET AJAX，請參閱[AJAX 範例](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e)。</span><span class="sxs-lookup"><span data-stu-id="d4333-107">For an example of using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with ASP.NET AJAX, see the [AJAX Samples](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4333-108">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="d4333-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d4333-109">下列範例中的服務是沒有使用 AJAX 特定程式碼的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="d4333-109">The service in the following sample is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service with no AJAX-specific code.</span></span> <span data-ttu-id="d4333-110">因為沒有套用 <xref:System.ServiceModel.Web.WebGetAttribute> 屬性，所以會使用預設的 HTTP 動詞命令 ("POST")。</span><span class="sxs-lookup"><span data-stu-id="d4333-110">Because the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="d4333-111">服務有一項 `DoMath` 作業，它會傳回名為 `MathResult` 的複雜型別。</span><span class="sxs-lookup"><span data-stu-id="d4333-111">The service has one operation, `DoMath`, which returns a complex type named `MathResult`.</span></span> <span data-ttu-id="d4333-112">複雜型別是標準資料合約型別，其中也未包含 AJAX 特定程式碼。</span><span class="sxs-lookup"><span data-stu-id="d4333-112">The complex type is a standard data contract type, which also contains no AJAX-specific code.</span></span>  
  
```  
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
  
 <span data-ttu-id="d4333-113">您可以在服務上使用 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> 來建立 AJAX 端點，如基本 AJAX 服務範例所示。</span><span class="sxs-lookup"><span data-stu-id="d4333-113">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>  
  
 <span data-ttu-id="d4333-114">用戶端網頁 complextypeclientpage.aspx 會包含 ASP.NET 和 JavaScript 程式碼叫用此服務，當使用者按一下**執行計算**頁面上的按鈕。</span><span class="sxs-lookup"><span data-stu-id="d4333-114">The client Web page ComplexTypeClientPage.aspx contains ASP.NET and JavaScript code to invoke the service when the user clicks the **Perform calculation** button on the page.</span></span> <span data-ttu-id="d4333-115">叫用此服務的程式碼會建構 JSON 本文，然後使用類似的 HTTP POST 加以傳送[AJAX 服務使用 HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)範例。</span><span class="sxs-lookup"><span data-stu-id="d4333-115">The code to invoke the service constructs a JSON body and sends it using HTTP POST, similar to the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>  
  
 <span data-ttu-id="d4333-116">在服務呼叫成功後，您就可以存取在結果 JavaScript 物件上的個別資料成員 (`sum`、`difference`、`product` 和 `quotient`)。</span><span class="sxs-lookup"><span data-stu-id="d4333-116">After the service call succeeds, you can access the individual data members (`sum`, `difference`, `product` and `quotient`) on the resulting JavaScript object.</span></span>  
  
```  
function onSuccess(mathResult){  
     document.getElementById("sum").value = mathResult.sum;  
     document.getElementById("difference").value = mathResult.difference;  
     document.getElementById("product").value = mathResult.product;  
     document.getElementById("quotient").value = mathResult.quotient;  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d4333-117">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="d4333-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d4333-118">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="d4333-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="d4333-119">中所述，建置此方案 ComplexTypeAjaxService.sln[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="d4333-119">Build the solution ComplexTypeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="d4333-120">瀏覽到 http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx (不要使用瀏覽器從專案目錄開啟 ComplexTypeClientPage.aspx)。</span><span class="sxs-lookup"><span data-stu-id="d4333-120">Navigate to http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx (do not open ComplexTypeClientPage.aspx in the browser from the project directory).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d4333-121">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="d4333-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d4333-122">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="d4333-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d4333-123">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="d4333-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d4333-124">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="d4333-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## <a name="see-also"></a><span data-ttu-id="d4333-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4333-125">See Also</span></span>  
 [<span data-ttu-id="d4333-126">基本 AJAX 服務</span><span class="sxs-lookup"><span data-stu-id="d4333-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
