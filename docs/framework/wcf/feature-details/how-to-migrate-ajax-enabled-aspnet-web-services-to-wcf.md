---
title: 作法：將啟用 AJAX 的 ASP.NET Web 服務移轉至 WCF
ms.date: 03/30/2017
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
ms.openlocfilehash: f492efe9e364195dce6b73a14e9ca5fa34a6df25
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972295"
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a>作法：將啟用 AJAX 的 ASP.NET Web 服務移轉至 WCF
本主題概述將基本 ASP.NET AJAX 服務遷移至對等啟用 AJAX 的 Windows Communication Foundation （WCF）服務的程式。 它會示範如何建立具有功能的對等 WCF 版本的 ASP.NET AJAX 服務。 然後，這兩個服務可以並存使用，或使用 WCF 服務來取代 ASP.NET AJAX 服務。

 將現有的 ASP.NET AJAX 服務遷移至 WCF AJAX 服務可提供下列優點：

- 您可以使用最少的額外組態，將您的 AJAX 服務公開為 SOAP 服務。

- 您可以從 WCF 功能獲益，例如追蹤等等。

 下列程式假設您使用 Visual Studio 2012。

 在程序之後的範例中，會提供來自本主題中所述程序的程式碼。

 如需透過啟用 AJAX 的端點來公開 WCF 服務的詳細資訊，請參閱[如何：使用 [設定] 來新增 ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)端點主題。

### <a name="to-create-and-test-the-aspnet-web-service-application"></a>若要建立並測試 ASP.NET Web 服務應用程式

1. 開啟 Visual Studio 2012。

2. 從 [**檔案**] 功能表中，依序選取 [**新增**]、[**專案**]、[ **Web**]，然後選取 [ **ASP.NET Web 服務應用程式**]。

3. 將專案`ASPHello`命名為，然後按一下 **[確定]** 。

4. 在 Service1.asmx.cs 檔案中，取消包含 `System.Web.Script.Services.ScriptService]` 的字行註解以便為此服務啟用 AJAX。

5. 從 [**建立**] 功能表中，選取 [**建立方案**]。

6. 從 [偵錯] 功能表，選取 [啟動但不偵錯]。

7. 在產生的網頁中，選取 `HelloWorld` 作業。

8. 按一下 [ `HelloWorld`測試] 頁面上的 [叫用 **] 按鈕。** 您應該會收到下列 XML 回應。

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <string xmlns="http://tempuri.org/">Hello World</string>
    ```

9. 這個回應會確認您現在有正在運作的 ASP.NET AJAX 服務，而且特別的是，服務現在已在回應 HTTP POST 要求並傳回 XML 的 Service1.asmx/HelloWorld 公開端點。

     現在您已準備好將此服務轉換成使用 WCF AJAX 服務。

### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a>建立相等的 WCF AJAX 服務應用程式

1. 以滑鼠右鍵按一下**ASPHello**專案，然後依序選取 [**加入**]、[**新增專案**] 和 [**啟用 AJAX 的 WCF 服務**]。

2. 為服務`WCFHello`命名，然後按一下 [**新增**]。

3. 開啟 WCFHello.svc.cs 檔案。

4. 從 Service1.asmx.cs 複製下列作業的執行`HelloWorld` 。

    ```csharp
    public string HelloWorld()
    {
         return "Hello World";
    }
    ```

5. 在 WCFHello.svc.cs 檔案中貼上`HelloWorld`要複製的作業執行，以取代下列程式碼。

    ```csharp
    public void DoWork()
    {
          // Add your operation implementation here
          return;
    }
    ```

6. 將的`Namespace` <xref:System.ServiceModel.ServiceContractAttribute>屬性指定為。 `WCFHello`

    ```csharp
    [ServiceContract(Namespace="WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]
    public class WCFHello
    { … }
    ```

7. <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>將加入<xref:System.ServiceModel.Web.WebInvokeAttribute>至作業，並將屬性設定為 return <xref:System.ServiceModel.Web.WebMessageFormat.Xml>。 `HelloWorld` 請注意，如果沒有設定，預設傳回型別為 <xref:System.ServiceModel.Web.WebMessageFormat.Json>。

    ```csharp
    [OperationContract]
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

8. 從 [**建立**] 功能表中，選取 [**建立方案**]。

9. 開啟 Wcfhello.svc .svc 檔案，然後從 [**調試**] 功能表選取 [**啟動但不進行調試**]。

10. 服務現在會公開的端點`WCFHello.svc/HelloWorld`，它會回應 HTTP POST 要求。 HTTP POST 要求無法從瀏覽器來測試，但是端點會傳回下列 XML。

    ```xml
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>
    ```

11. 和端點現在的`WCFHello.svc/HelloWorld`功能相同。`Service1.aspx/HelloWorld`

## <a name="example"></a>範例
 下列範例中會提供來自本主題中所述程序的程式碼。

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

 <xref:System.Xml.XmlDocument> 不支援 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 型別，因為它無法由 <xref:System.Xml.Serialization.XmlSerializer> 來序列化。 您可以使用 <xref:System.Xml.Linq.XDocument> 型別，或是改為序列化 <xref:System.Xml.XmlDocument.DocumentElement%2A>。

 如果要將 .ASMX Web 服務升級並同時遷移至 WCF 服務，請避免將兩種類型對應到用戶端上的相同名稱。 如果在 <xref:System.Web.Services.WebMethodAttribute> 和 <xref:System.ServiceModel.ServiceContractAttribute> 中使用相同的型別，會造成序列化程式中的例外狀況：

- 如果第一次加入 WCF 服務，在 .asmx Web 服務上叫用方法會<xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29>造成中的例外狀況，因為在 proxy 中順序的 WCF 樣式定義會優先使用。

- 如果第一次新增 .asmx Web 服務，在 WCF 服務上叫用方法<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>會造成中的例外狀況，因為在 proxy 中順序的 Web 服務樣式定義會優先使用。

 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 和 ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> 之間在行為上有許多不同之處。 例如，<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 會將字典表示為索引鍵/值配對的陣列，而 ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> 會將字典表示為實際的 JSON 物件。 因此下面是在 ASP.NET AJAX 中表示的字典。

```csharp
Dictionary<string, int> d = new Dictionary<string, int>();
d.Add("one", 1);
d.Add("two", 2);
```

 這個字典在 JSON 物件中的表示如下列清單所示：

- [{"Key":"one","Value":1},{"Key":"two","Value":2}]，透過 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>

- {"one"：1，"two"： 2} 由 ASP.NET AJAX<xref:System.Web.Script.Serialization.JavaScriptSerializer>

 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 的功能較為強大，因為它可以處理其中金鑰類型不是字串的字典，但是 <xref:System.Web.Script.Serialization.JavaScriptSerializer> 卻無法這麼做。 然而後者較容易用來處理 JSON。

 下表將摘要說明序列化程式之間的許多差異。

|差異分類|DataContractJsonSerializer|ASP.NET AJAX JavaScriptSerializer|
|-----------------------------|--------------------------------|---------------------------------------|
|將空的緩衝區 (新的 byte[0]) 還原序列化成 <xref:System.Object> (或 <xref:System.Uri> 或一些其他的類別)。|SerializationException|null|
|<xref:System.DBNull.Value> 的序列化|{}（或 {"__type"： "#System"}）|Null|
|[Serializable] 型別的私用成員序列化|已序列化|未序列化|
|<xref:System.Runtime.Serialization.ISerializable> 型別的公用屬性序列化。|未序列化|已序列化|
|JSON 的 "Extensions"|遵守 JSON 規格，需要在物件成員名稱上加上引號 ({"a":"hello"})。|支援不加引號的物件成員名稱 ({a:"hello"})。|
|<xref:System.DateTime> 以 Coordinated Universal Time (UTC) 時間計算|不支援格式 "\\/Date （123456789U）\\ {4} \\ + &#124; \\ \\ \\/" 或 "/Date\\（\d + （U （-[\d]））？）\\\\/)".|支援格式 "\\/Date （123456789U）\\/" 和 "\\/Date\\（\d + （U&#124;（\\ {4} + \\-[\d]））？\\）\\ /）"\\做為 DateTime 值。|
|字典表示法|KeyValuePair\<K，V > 的陣列會處理不是字串的索引鍵類型。|做為實際的 JSON 物件 - 但只能處理屬於字串的金鑰型別。|
|逸出字元|一律使用逸出正斜線 (/)；絕不允許使用未逸出的無效 JSON 字元，例如 "\n"。|使用逸出斜線 (/) 做為 DateTime 值。|

## <a name="see-also"></a>另請參閱

- [如何：使用設定來新增 ASP.NET AJAX 端點](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
