---
title: HOW TO：將啟用 AJAX 的 ASP.NET Web 服務移轉至 WCF
ms.date: 03/30/2017
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
ms.openlocfilehash: 6114fa90b10a5d0cacb60a7ad40f63fae776e174
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683518"
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a><span data-ttu-id="7cdc2-102">HOW TO：將啟用 AJAX 的 ASP.NET Web 服務移轉至 WCF</span><span class="sxs-lookup"><span data-stu-id="7cdc2-102">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>
<span data-ttu-id="7cdc2-103">本主題概述將基本的 ASP.NET AJAX 服務移轉至對等的 AJAX 啟用 Windows Communication Foundation (WCF) 服務的程序。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-103">This topic outlines procedures to migrate a basic ASP.NET AJAX service to an equivalent AJAX-enabled Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="7cdc2-104">它示範如何建立同等功效的 WCF 版本的 ASP.NET AJAX 服務。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-104">It shows how to create a functionally equivalent WCF version of an ASP.NET AJAX service.</span></span> <span data-ttu-id="7cdc2-105">這兩項服務可以接著使用並排顯示，或 WCF 服務可以用來取代 ASP.NET AJAX 服務。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-105">The two services can then be used side by side, or the WCF service can be used to replace the ASP.NET AJAX service.</span></span>

 <span data-ttu-id="7cdc2-106">移轉現有的 ASP.NET AJAX 的 WCF AJAX 服務的服務提供下列優點：</span><span class="sxs-lookup"><span data-stu-id="7cdc2-106">Migrating an existing ASP.NET AJAX service to a WCF AJAX service gives you the following benefits:</span></span>

- <span data-ttu-id="7cdc2-107">您可以使用最少的額外組態，將您的 AJAX 服務公開為 SOAP 服務。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-107">You can expose your AJAX service as a SOAP service with minimal extra configuration.</span></span>

- <span data-ttu-id="7cdc2-108">您可以受益於 WCF 功能，例如追蹤等等。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-108">You can benefit from WCF features such as tracing, and so on.</span></span>

 <span data-ttu-id="7cdc2-109">下列程序假設您使用 Visual Studio 2012。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-109">The following procedures assume that you are using Visual Studio 2012.</span></span>

 <span data-ttu-id="7cdc2-110">在程序之後的範例中，會提供來自本主題中所述程序的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-110">The code that results from the procedures outlined in this topic is provided in the example following the procedures.</span></span>

 <span data-ttu-id="7cdc2-111">如需有關如何公開透過啟用 AJAX 的端點的 WCF 服務的詳細資訊，請參閱[How to:使用組態新增 ASP.NET AJAX 端點](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)主題。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-111">For more information about exposing a WCF service through an AJAX-enabled endpoint, see the [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) topic.</span></span>

### <a name="to-create-and-test-the-aspnet-web-service-application"></a><span data-ttu-id="7cdc2-112">若要建立並測試 ASP.NET Web 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="7cdc2-112">To create and test the ASP.NET Web service application</span></span>

1. <span data-ttu-id="7cdc2-113">開啟 Visual Studio 2012。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-113">Open Visual Studio 2012.</span></span>

2. <span data-ttu-id="7cdc2-114">從**檔案**功能表上，選取**新增**，然後**專案**，然後**Web**，然後選取  **ASP.NET Web 服務應用程式**.</span><span class="sxs-lookup"><span data-stu-id="7cdc2-114">From the **File** menu, select **New**, then **Project**, then **Web**, and then select **ASP.NET Web Service Application**.</span></span>

3. <span data-ttu-id="7cdc2-115">將專案命名為`ASPHello`，按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-115">Name the project `ASPHello` and click **OK**.</span></span>

4. <span data-ttu-id="7cdc2-116">在 Service1.asmx.cs 檔案中，取消包含 `System.Web.Script.Services.ScriptService]` 的字行註解以便為此服務啟用 AJAX。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-116">Uncomment the line in the Service1.asmx.cs file that contains `System.Web.Script.Services.ScriptService]` to enable AJAX for this service.</span></span>

5. <span data-ttu-id="7cdc2-117">從**建置**功能表上，選取**建置方案**。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-117">From the **Build** menu, select **Build Solution**.</span></span>

6. <span data-ttu-id="7cdc2-118">從 [偵錯] 功能表，選取 [啟動但不偵錯]。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-118">From the **Debug** menu, select **Start Without Debugging**.</span></span>

7. <span data-ttu-id="7cdc2-119">在產生的網頁中，選取 `HelloWorld` 作業。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-119">On the Web page generated, select the `HelloWorld` operation.</span></span>

8. <span data-ttu-id="7cdc2-120">按一下  **Invoke**按鈕`HelloWorld`測試頁。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-120">Click the **Invoke** button on the `HelloWorld` test page.</span></span> <span data-ttu-id="7cdc2-121">您應該會收到下列 XML 回應。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-121">You should receive the following XML response.</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <string xmlns="http://tempuri.org/">Hello World</string>
    ```

9. <span data-ttu-id="7cdc2-122">這個回應會確認您現在有正在運作的 ASP.NET AJAX 服務，而且特別的是，服務現在已在回應 HTTP POST 要求並傳回 XML 的 Service1.asmx/HelloWorld 公開端點。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-122">This response confirms that you now have a functioning ASP.NET AJAX service and, in particular, that the service has now exposed an endpoint at Service1.asmx/HelloWorld that responds to HTTP POST requests and returns XML.</span></span>

     <span data-ttu-id="7cdc2-123">現在您已準備好轉換這個服務，若要使用的 WCF AJAX 服務。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-123">Now you are ready to convert this service to use a WCF AJAX service.</span></span>

### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a><span data-ttu-id="7cdc2-124">建立相等的 WCF AJAX 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="7cdc2-124">To create an equivalent WCF AJAX service application</span></span>

1. <span data-ttu-id="7cdc2-125">以滑鼠右鍵按一下**ASPHello**專案，然後選取**新增**，然後**新項目**，然後**啟用 AJAX 的 WCF 服務**。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-125">Right-click the **ASPHello** project and select **Add**, then **New Item**, and then **AJAX-enabled WCF Service**.</span></span>

2. <span data-ttu-id="7cdc2-126">將服務命名`WCFHello`，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-126">Name the service `WCFHello` and click **Add**.</span></span>

3. <span data-ttu-id="7cdc2-127">開啟 WCFHello.svc.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-127">Open the WCFHello.svc.cs file.</span></span>

4. <span data-ttu-id="7cdc2-128">從 Service1.asmx.cs 複製的下列實作`HelloWorld`作業。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-128">From Service1.asmx.cs, copy the following implementation of the `HelloWorld` operation.</span></span>

    ```
    public string HelloWorld()
    {
         return "Hello World";
    }
    ```

5. <span data-ttu-id="7cdc2-129">貼上複製實作`HelloWorld`至 WCFHello.svc.cs 檔案，取代下列程式碼的作業。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-129">Paste to copied implementation of the `HelloWorld` operation into the WCFHello.svc.cs file in place of the following code.</span></span>

    ```
    public void DoWork()
    {
          // Add your operation implementation here
          return;
    }
    ```

6. <span data-ttu-id="7cdc2-130">指定`Namespace`屬性<xref:System.ServiceModel.ServiceContractAttribute>做為`WCFHello`。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-130">Specify the `Namespace` attribute for <xref:System.ServiceModel.ServiceContractAttribute> as `WCFHello`.</span></span>

    ```
    [ServiceContract(Namespace="WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]
    public class WCFHello
    { … }
    ```

7. <span data-ttu-id="7cdc2-131">新增<xref:System.ServiceModel.Web.WebInvokeAttribute>要`HelloWorld`作業，並設定<xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>屬性，以傳回<xref:System.ServiceModel.Web.WebMessageFormat.Xml>。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-131">Add the <xref:System.ServiceModel.Web.WebInvokeAttribute> to the `HelloWorld` operation and set the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> property to return <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span></span> <span data-ttu-id="7cdc2-132">請注意，如果沒有設定，預設傳回型別為 <xref:System.ServiceModel.Web.WebMessageFormat.Json>。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-132">Note that, if not set, the default return type is <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span>

    ```
    [OperationContract]
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

8. <span data-ttu-id="7cdc2-133">從**建置**功能表上，選取**建置方案**。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-133">From the **Build** menu, select **Build Solution**.</span></span>

9. <span data-ttu-id="7cdc2-134">開啟 WCFHello.svc 檔案進出**偵錯**功能表上，選取**啟動但不偵錯**。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-134">Open the WCFHello.svc file and from the **Debug** menu, select **Start Without Debugging**.</span></span>

10. <span data-ttu-id="7cdc2-135">服務現在會公開在端點`WCFHello.svc/HelloWorld`，其會回應 HTTP POST 要求。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-135">The service now exposes an endpoint at `WCFHello.svc/HelloWorld`, which responds to HTTP POST requests.</span></span> <span data-ttu-id="7cdc2-136">HTTP POST 要求無法從瀏覽器來測試，但是端點會傳回下列 XML。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-136">HTTP POST requests cannot be tested from the browser, but the endpoint returns XML following XML.</span></span>

    ```xml
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>
    ```

11. <span data-ttu-id="7cdc2-137">`WCFHello.svc/HelloWorld`而`Service1.aspx/HelloWorld`端點現在的功能相同。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-137">The `WCFHello.svc/HelloWorld` and the `Service1.aspx/HelloWorld` endpoints are now functionally equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="7cdc2-138">範例</span><span class="sxs-lookup"><span data-stu-id="7cdc2-138">Example</span></span>
 <span data-ttu-id="7cdc2-139">下列範例中會提供來自本主題中所述程序的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-139">The code that results from the procedures outlined in this topic is provided in the following example.</span></span>

```csharp
//This is the ASP.NET code in the Service1.asmx.cs file.

using System;
using System.Collections;
using System.ComponentModel;
using System.Data;
using System.Linq;
using System.Web;
using System.Web.Services;
using System.Web.Services.Protocols;
using System.Xml.Linq;
using System.Web.Script.Services;

namespace ASPHello
{
    /// <summary>
    /// Summary description for Service1.
    /// </summary>
    [WebService(Namespace = "http://tempuri.org/")]
    [WebServiceBinding(ConformsTo = WsiProfiles.BasicProfile1_1)]
    [ToolboxItem(false)]
    // To allow this Web Service to be called from script, using ASP.NET AJAX, uncomment the following line.
    [System.Web.Script.Services.ScriptService]
    public class Service1 : System.Web.Services.WebService
    {

        [WebMethod]
        public string HelloWorld()
        {
            return "Hello World";
        }
    }
}

//This is the WCF code in the WCFHello.svc.cs file.
using System;
using System.Linq;
using System.Runtime.Serialization;
using System.ServiceModel;
using System.ServiceModel.Activation;
using System.ServiceModel.Web;

namespace ASPHello
{
    [ServiceContract(Namespace = "WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
    public class WCFHello
    {
        // Add [WebInvoke] attribute to use HTTP GET.
        [OperationContract]
        [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
        public string HelloWorld()
        {
            return "Hello World";
        }

        // Add more operations here and mark them with [OperationContract].
    }
}
```

 <span data-ttu-id="7cdc2-140"><xref:System.Xml.XmlDocument> 不支援 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 型別，因為它無法由 <xref:System.Xml.Serialization.XmlSerializer> 來序列化。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-140">The <xref:System.Xml.XmlDocument> type is not supported by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because it is not serializable by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="7cdc2-141">您可以使用 <xref:System.Xml.Linq.XDocument> 型別，或是改為序列化 <xref:System.Xml.XmlDocument.DocumentElement%2A>。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-141">You can use either an <xref:System.Xml.Linq.XDocument> type, or serialize the <xref:System.Xml.XmlDocument.DocumentElement%2A> instead.</span></span>

 <span data-ttu-id="7cdc2-142">如果 ASMX Web 服務正在升級和移轉至 WCF 服務的並排顯示，以避免兩個型別對應至用戶端上相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-142">If ASMX Web services are being upgraded and migrated side-by-side to WCF services, avoid mapping two types to the same name on the client.</span></span> <span data-ttu-id="7cdc2-143">如果在 <xref:System.Web.Services.WebMethodAttribute> 和 <xref:System.ServiceModel.ServiceContractAttribute> 中使用相同的型別，會造成序列化程式中的例外狀況：</span><span class="sxs-lookup"><span data-stu-id="7cdc2-143">This causes an exception in serializers if the same type is used in a <xref:System.Web.Services.WebMethodAttribute> and a <xref:System.ServiceModel.ServiceContractAttribute>:</span></span>

- <span data-ttu-id="7cdc2-144">第一次加入 WCF 服務時，叫用 ASMX Web 服務上的方法會導致例外狀況中的<xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29>因為 WCF 樣式定義，在 proxy 中順序的優先順序。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-144">If WCF service is added first, invoking the method on ASMX Web Service causes exception in <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> because the WCF style definition of the order in the proxy takes precedence.</span></span>

- <span data-ttu-id="7cdc2-145">如果先新增 ASMX Web 服務，則叫用 WCF 服務上的方法會導致例外狀況中的<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>因為在 proxy 中順序的 Web 服務樣式定義會取得優先權。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-145">If ASMX Web Service is added first, invoking method on WCF service causes exception in <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because the Web Service style definition of the order in the proxy takes precedence.</span></span>

 <span data-ttu-id="7cdc2-146"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 和 ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> 之間在行為上有許多不同之處。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-146">There are significant differences in behavior between the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> and the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>.</span></span> <span data-ttu-id="7cdc2-147">例如，<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 會將字典表示為索引鍵/值配對的陣列，而 ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> 會將字典表示為實際的 JSON 物件。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-147">For example, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> represents a dictionary as an array of key/value pairs, whereas the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> represents a dictionary as actual JSON objects.</span></span> <span data-ttu-id="7cdc2-148">因此下面是在 ASP.NET AJAX 中表示的字典。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-148">So the following is the dictionary represented in ASP.NET AJAX.</span></span>

```
Dictionary<string, int> d = new Dictionary<string, int>();
d.Add("one", 1);
d.Add("two", 2);
```

 <span data-ttu-id="7cdc2-149">這個字典在 JSON 物件中的表示如下列清單所示：</span><span class="sxs-lookup"><span data-stu-id="7cdc2-149">This dictionary is represented in JSON objects as shown in the following list:</span></span>

- <span data-ttu-id="7cdc2-150">[{"Key":"one","Value":1},{"Key":"two","Value":2}]，透過 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span><span class="sxs-lookup"><span data-stu-id="7cdc2-150">[{"Key":"one","Value":1},{"Key":"two","Value":2}] by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span></span>

- <span data-ttu-id="7cdc2-151">{"one": 1，"two": 2} 的 ASP.NET ajax <xref:System.Web.Script.Serialization.JavaScriptSerializer></span><span class="sxs-lookup"><span data-stu-id="7cdc2-151">{"one":1,"two":2} by the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer></span></span>

 <span data-ttu-id="7cdc2-152"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 的功能較為強大，因為它可以處理其中金鑰類型不是字串的字典，但是 <xref:System.Web.Script.Serialization.JavaScriptSerializer> 卻無法這麼做。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-152">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is more powerful in the sense that it can handle dictionaries where the key type is not string, while the <xref:System.Web.Script.Serialization.JavaScriptSerializer> cannot.</span></span> <span data-ttu-id="7cdc2-153">然而後者較容易用來處理 JSON。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-153">But the latter is more JSON-friendly.</span></span>

 <span data-ttu-id="7cdc2-154">下表將摘要說明序列化程式之間的許多差異。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-154">The significant differences between these serializers are summarized in the following table.</span></span>

|<span data-ttu-id="7cdc2-155">差異分類</span><span class="sxs-lookup"><span data-stu-id="7cdc2-155">Category of Differences</span></span>|<span data-ttu-id="7cdc2-156">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="7cdc2-156">DataContractJsonSerializer</span></span>|<span data-ttu-id="7cdc2-157">ASP.NET AJAX JavaScriptSerializer</span><span class="sxs-lookup"><span data-stu-id="7cdc2-157">ASP.NET AJAX JavaScriptSerializer</span></span>|
|-----------------------------|--------------------------------|---------------------------------------|
|<span data-ttu-id="7cdc2-158">將空的緩衝區 (新的 byte[0]) 還原序列化成 <xref:System.Object> (或 <xref:System.Uri> 或一些其他的類別)。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-158">Deserializing the empty buffer (new byte[0]) into <xref:System.Object> (or <xref:System.Uri>, or some other classes).</span></span>|<span data-ttu-id="7cdc2-159">SerializationException</span><span class="sxs-lookup"><span data-stu-id="7cdc2-159">SerializationException</span></span>|<span data-ttu-id="7cdc2-160">null</span><span class="sxs-lookup"><span data-stu-id="7cdc2-160">null</span></span>|
|<span data-ttu-id="7cdc2-161"><xref:System.DBNull.Value> 的序列化</span><span class="sxs-lookup"><span data-stu-id="7cdc2-161">Serialization of <xref:System.DBNull.Value></span></span>|<span data-ttu-id="7cdc2-162">{} (或 {"__type":"#System"})</span><span class="sxs-lookup"><span data-stu-id="7cdc2-162">{} (or {"__type":"#System"})</span></span>|<span data-ttu-id="7cdc2-163">Null</span><span class="sxs-lookup"><span data-stu-id="7cdc2-163">Null</span></span>|
|<span data-ttu-id="7cdc2-164">[Serializable] 型別的私用成員序列化</span><span class="sxs-lookup"><span data-stu-id="7cdc2-164">Serialization of the private members of [Serializable] types.</span></span>|<span data-ttu-id="7cdc2-165">已序列化</span><span class="sxs-lookup"><span data-stu-id="7cdc2-165">serialized</span></span>|<span data-ttu-id="7cdc2-166">未序列化</span><span class="sxs-lookup"><span data-stu-id="7cdc2-166">not serialized</span></span>|
|<span data-ttu-id="7cdc2-167"><xref:System.Runtime.Serialization.ISerializable> 型別的公用屬性序列化。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-167">Serialization of the public properties of <xref:System.Runtime.Serialization.ISerializable> types.</span></span>|<span data-ttu-id="7cdc2-168">未序列化</span><span class="sxs-lookup"><span data-stu-id="7cdc2-168">not serialized</span></span>|<span data-ttu-id="7cdc2-169">已序列化</span><span class="sxs-lookup"><span data-stu-id="7cdc2-169">serialized</span></span>|
|<span data-ttu-id="7cdc2-170">JSON 的 "Extensions"</span><span class="sxs-lookup"><span data-stu-id="7cdc2-170">"Extensions" of JSON</span></span>|<span data-ttu-id="7cdc2-171">遵守 JSON 規格，需要在物件成員名稱上加上引號 ({"a":"hello"})。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-171">Adheres to the JSON specification, which requires quotes on object member names ({"a":"hello"}).</span></span>|<span data-ttu-id="7cdc2-172">支援不加引號的物件成員名稱 ({a:"hello"})。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-172">Supports the names of object members without quotes ({a:"hello"}).</span></span>|
|<span data-ttu-id="7cdc2-173"><xref:System.DateTime> 以 Coordinated Universal Time (UTC) 時間計算</span><span class="sxs-lookup"><span data-stu-id="7cdc2-173"><xref:System.DateTime> Coordinated Universal Time (UTC)</span></span>|<span data-ttu-id="7cdc2-174">不支援格式"\\/Date(123456789U)\\/ 」 或 「\\/日期\\(\d+ (U&#124;(\\+\\-[\d{4}]))？\\)\\\\/)".</span><span class="sxs-lookup"><span data-stu-id="7cdc2-174">Does not support format "\\/Date(123456789U)\\/" or "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)".</span></span>|<span data-ttu-id="7cdc2-175">支援格式"\\/Date(123456789U)\\/"和"\\/日期\\(\d+ (U&#124;(\\+\\-[\d{4}]))？\\)\\ \\/)"做為 DateTime 值。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-175">Supports format "\\/Date(123456789U)\\/" and "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)" as DateTime values.</span></span>|
|<span data-ttu-id="7cdc2-176">字典表示法</span><span class="sxs-lookup"><span data-stu-id="7cdc2-176">Representation of dictionaries</span></span>|<span data-ttu-id="7cdc2-177">陣列的 KeyValuePair\<K，V >，可處理索引鍵的類型不是字串。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-177">An array of KeyValuePair\<K,V>, handles key types that are not strings.</span></span>|<span data-ttu-id="7cdc2-178">做為實際的 JSON 物件 - 但只能處理屬於字串的金鑰型別。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-178">As actual JSON objects - but only handles key types that are strings.</span></span>|
|<span data-ttu-id="7cdc2-179">逸出字元</span><span class="sxs-lookup"><span data-stu-id="7cdc2-179">Escaped characters</span></span>|<span data-ttu-id="7cdc2-180">一律使用逸出正斜線 (/)；絕不允許使用未逸出的無效 JSON 字元，例如 "\n"。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-180">Always with an escape forward slash (/); never allows un-escaped invalid JSON characters, such as "\n".</span></span>|<span data-ttu-id="7cdc2-181">使用逸出斜線 (/) 做為 DateTime 值。</span><span class="sxs-lookup"><span data-stu-id="7cdc2-181">With an escape forward slash (/) for DateTime values.</span></span>|

## <a name="see-also"></a><span data-ttu-id="7cdc2-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7cdc2-182">See also</span></span>

- [<span data-ttu-id="7cdc2-183">如何：使用組態新增 ASP.NET AJAX 端點</span><span class="sxs-lookup"><span data-stu-id="7cdc2-183">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
