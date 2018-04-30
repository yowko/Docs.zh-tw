---
title: HOW TO：將啟用 AJAX 的 ASP.NET Web 服務移轉至 WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2b728e6283a2f038b7e5ef4c535da41f4eb8ebef
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a>HOW TO：將啟用 AJAX 的 ASP.NET Web 服務移轉至 WCF
本主題將概述用來將基本 ASP.NET AJAX 服務移轉至相等之啟用 AJAX 的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務的程序。 其中將示範如何建立功能相等的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 版本的 ASP.NET AJAX 服務。 然後這兩項服務可以並存使用，或是 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務可以用於取代 ASP.NET AJAX 服務。  
  
 將現有的 ASP.NET AJAX 服務移轉至 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX 服務可為您提供下列優點：  
  
-   您可以使用最少的額外組態，將您的 AJAX 服務公開為 SOAP 服務。  
  
-   您可以從 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 功能獲益，例如追蹤等等。  
  
 下列程序假設使用的是 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]。  
  
 在程序之後的範例中，會提供來自本主題中所述程序的程式碼。  
  
 如需有關公開[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]服務透過啟用 AJAX 的端點，請參閱[How to： 使用組態新增 ASP.NET AJAX 端點](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)主題。  
  
### <a name="to-create-and-test-the-aspnet-web-service-application"></a>若要建立並測試 ASP.NET Web 服務應用程式  
  
1.  開啟 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]。  
  
2.  從**檔案**功能表上，選取**新增**，然後**專案**，然後**Web**，然後選取**ASP.NET Web 服務應用程式**.  
  
3.  將專案命名`ASPHello`按一下**確定**。  
  
4.  在 Service1.asmx.cs 檔案中，取消包含 `System.Web.Script.Services.ScriptService]` 的字行註解以便為此服務啟用 AJAX。  
  
5.  從**建置**功能表上，選取**建置方案**。  
  
6.  從**偵錯**功能表上，選取**啟動但不偵錯**。  
  
7.  在產生的網頁中，選取 `HelloWorld` 作業。  
  
8.  按一下**Invoke**按鈕`HelloWorld`測試頁。 您應該會收到下列 XML 回應。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <string xmlns="http://tempuri.org/">Hello World</string>  
    ```  
  
9. 這個回應會確認您現在有正在運作的 ASP.NET AJAX 服務，而且特別的是，服務現在已在回應 HTTP POST 要求並傳回 XML 的 Service1.asmx/HelloWorld 公開端點。  
  
     現在您已準備好要轉換這個服務，以使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX 服務了。  
  
### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a>建立相等的 WCF AJAX 服務應用程式  
  
1.  以滑鼠右鍵按一下**ASPHello**專案，然後選取**新增**，然後**新項目**，然後**啟用 AJAX 的 WCF 服務**。  
  
2.  為服務名稱`WCFHello`按一下**新增**。  
  
3.  開啟 WCFHello.svc.cs 檔案。  
  
4.  從 Service1.asmx.cs 複製的下列實作`HelloWorld`作業。  
  
    ```  
    public string HelloWorld()  
    {  
         return "Hello World";  
    }  
    ```  
  
5.  複製的實作貼上至`HelloWorld`WCFHello.svc.cs 檔案，以取代下列程式碼的作業。  
  
    ```  
    public void DoWork()  
    {  
          // Add your operation implementation here  
          return;  
    }  
    ```  
  
6.  指定`Namespace`屬性<xref:System.ServiceModel.ServiceContractAttribute>為`WCFHello`。  
  
    ```  
    [ServiceContract(Namespace="WCFHello")]  
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]  
    public class WCFHello  
    { … }  
    ```  
  
7.  新增<xref:System.ServiceModel.Web.WebInvokeAttribute>至`HelloWorld`作業，並設定<xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>屬性，以傳回<xref:System.ServiceModel.Web.WebMessageFormat.Xml>。 請注意，如果沒有設定，預設傳回型別為 <xref:System.ServiceModel.Web.WebMessageFormat.Json>。  
  
    ```  
    [OperationContract]  
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]  
    public string HelloWorld()  
    {  
        return "Hello World";  
    }  
    ```  
  
8.  從**建置**功能表上，選取**建置方案**。  
  
9. 開啟 WCFHello.svc 檔案和從**偵錯**功能表上，選取**啟動但不偵錯**。  
  
10. 服務現在會公開在端點`WCFHello.svc/HelloWorld`，回應 HTTP POST 要求。 HTTP POST 要求無法從瀏覽器來測試，但是端點會傳回下列 XML。  
  
    ```xml  
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>  
    ```  
  
11. `WCFHello.svc/HelloWorld`和`Service1.aspx/HelloWorld`端點現在的功能相同。  
  
## <a name="example"></a>範例  
 下列範例中會提供來自本主題中所述程序的程式碼。  
  
```  
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
  
 如果 ASMX Web 服務正並存升級及移轉至 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務，請避免將兩種型別對應至用戶端上相同的名稱。 如果在 <xref:System.Web.Services.WebMethodAttribute> 和 <xref:System.ServiceModel.ServiceContractAttribute> 中使用相同的型別，會造成序列化程式中的例外狀況：  
  
-   如果先新增 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務，則叫用 ASMX Web 服務上的方法會造成 <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> 中的例外狀況，因為在 Proxy 中順序的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 樣式定義會取得優先權。  
  
-   如果先新增 ASMX Web 服務，則叫用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務上的方法會造成 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 中的例外狀況，因為在 Proxy 中順序的 Web 服務樣式定義會取得優先權。  
  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 和 ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> 之間在行為上有許多不同之處。 例如，<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 會將字典表示為索引鍵/值配對的陣列，而 ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> 會將字典表示為實際的 JSON 物件。 因此下面是在 ASP.NET AJAX 中表示的字典。  
  
```  
Dictionary<string, int> d = new Dictionary<string, int>();  
d.Add("one", 1);  
d.Add("two", 2);  
```  
  
 這個字典在 JSON 物件中的表示如下列清單所示：  
  
-   [{"Key":"one","Value":1},{"Key":"two","Value":2}]，透過 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>  
  
-   {"one": 1，"two": 2} 的 ASP.NET ajax <xref:System.Web.Script.Serialization.JavaScriptSerializer>  
  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 的功能較為強大，因為它可以處理其中金鑰類型不是字串的字典，但是 <xref:System.Web.Script.Serialization.JavaScriptSerializer> 卻無法這麼做。 然而後者較容易用來處理 JSON。  
  
 下表將摘要說明序列化程式之間的許多差異。  
  
|差異分類|DataContractJsonSerializer|ASP.NET AJAX JavaScriptSerializer|  
|-----------------------------|--------------------------------|---------------------------------------|  
|將空的緩衝區 (新的 byte[0]) 還原序列化成 <xref:System.Object> (或 <xref:System.Uri> 或一些其他的類別)。|SerializationException|null|  
|<xref:System.DBNull.Value> 的序列化|{} (或 {"__type":"#System"})|Null|  
|[Serializable] 型別的私用成員序列化|已序列化|未序列化|  
|<xref:System.Runtime.Serialization.ISerializable> 型別的公用屬性序列化。|未序列化|已序列化|  
|JSON 的 "Extensions"|遵守 JSON 規格，需要在物件成員名稱上加上引號 ({"a":"hello"})。|支援不加引號的物件成員名稱 ({a:"hello"})。|  
|<xref:System.DateTime> 以 Coordinated Universal Time (UTC) 時間計算|不支援格式"\\/Date(123456789U)\\/"或"\\/Date\\(\d+ (U&#124;(\\+\\-[\d{4}]))？\\)\\\\/)".|支援格式"\\/Date(123456789U)\\/"和"\\/Date\\(\d+ (U&#124;(\\+\\-[\d{4}]))？\\)\\ \\/)"做為 DateTime 值。|  
|字典表示法|陣列的 KeyValuePair\<K，V >，可處理不是字串的索引鍵類型。|做為實際的 JSON 物件 - 但只能處理屬於字串的金鑰型別。|  
|逸出字元|一律使用逸出正斜線 (/)；絕不允許使用未逸出的無效 JSON 字元，例如 "\n"。|使用逸出斜線 (/) 做為 DateTime 值。|  
  
## <a name="see-also"></a>另請參閱  
 [如何：使用組態新增 ASP.NET AJAX 端點](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
