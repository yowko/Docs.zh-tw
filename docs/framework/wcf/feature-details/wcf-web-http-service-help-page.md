---
title: WCF Web HTTP 服務說明網頁
ms.date: 03/30/2017
ms.assetid: 63c7c695-44b6-4f31-bb9c-00f2763f525e
ms.openlocfilehash: d0fe4f99fea4d414c95244e535cd75891f921790
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47195988"
---
# <a name="wcf-web-http-service-help-page"></a><span data-ttu-id="15bd9-102">WCF Web HTTP 服務說明網頁</span><span class="sxs-lookup"><span data-stu-id="15bd9-102">WCF Web HTTP Service Help Page</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="15bd9-103">會為 WCF WEB HTTP 服務提供自動說明頁面。</span><span class="sxs-lookup"><span data-stu-id="15bd9-103"> provides an automatic help page for WCF WEB HTTP services.</span></span> <span data-ttu-id="15bd9-104">此說明頁面會列出每項作業、要求與回應格式和結構描述的說明。</span><span class="sxs-lookup"><span data-stu-id="15bd9-104">This help page lists a description of each operation, request and response formats, and schemas.</span></span> <span data-ttu-id="15bd9-105">此功能預設為關閉。</span><span class="sxs-lookup"><span data-stu-id="15bd9-105">This functionality is turned off by default.</span></span> <span data-ttu-id="15bd9-106">當使用者瀏覽至 WCF WEB HTTP 服務並附加在 「 / 說明 」 的 URL，例如後面 http://localhost:8000/Customers/Help ，一樣會顯示下列說明頁面。</span><span class="sxs-lookup"><span data-stu-id="15bd9-106">When a user browses to a WCF WEB HTTP service and appends "/Help" on to the end of the URL, for example http://localhost:8000/Customers/Help, a help page like the following is displayed.</span></span>  
  
 <span data-ttu-id="15bd9-107">![WCF REST 說明頁面](../../../../docs/framework/wcf/feature-details/media/wcfresthelppagemain.gif "WCFRESTHELPPAGEMAIN")</span><span class="sxs-lookup"><span data-stu-id="15bd9-107">![WCF REST Help Page](../../../../docs/framework/wcf/feature-details/media/wcfresthelppagemain.gif "WCFRESTHELPPAGEMAIN")</span></span>  
  
 <span data-ttu-id="15bd9-108">使用者可以按一下說明頁面中列出的任何方法，該作業的詳細資訊頁面便會顯示，提供有關該方法的詳細資訊，包括訊息格式和回應範例。</span><span class="sxs-lookup"><span data-stu-id="15bd9-108">The user can then click any method listed in the help page and detailed page for that operation is displayed showing more information about the method, including message formats and example responses.</span></span> <span data-ttu-id="15bd9-109">下圖是方法之說明頁面的範例。</span><span class="sxs-lookup"><span data-stu-id="15bd9-109">The following image is an example of a help page for a method.</span></span>  
  
 <span data-ttu-id="15bd9-110">![WCF REST 說明頁面詳細資料](../../../../docs/framework/wcf/feature-details/media/wcfresthelppagedetail2.gif "WCFRESTHELPPAGEDETAIL2")</span><span class="sxs-lookup"><span data-stu-id="15bd9-110">![WCF REST Help Page Details](../../../../docs/framework/wcf/feature-details/media/wcfresthelppagedetail2.gif "WCFRESTHELPPAGEDETAIL2")</span></span>  
  
## <a name="using-the-wcf-web-http-help-page"></a><span data-ttu-id="15bd9-111">使用 WCF Web HTTP 說明頁面</span><span class="sxs-lookup"><span data-stu-id="15bd9-111">Using the WCF Web HTTP Help Page</span></span>  
 <span data-ttu-id="15bd9-112">WCF WEB HTTP 說明頁面會顯示每項作業的簡短描述，您可以使用 <xref:System.ComponentModel.DescriptionAttribute> 來指定任何一項。</span><span class="sxs-lookup"><span data-stu-id="15bd9-112">The WCF WEB HTTP Help page displays a short description for each operation provided that you specify one using the <xref:System.ComponentModel.DescriptionAttribute>.</span></span> <span data-ttu-id="15bd9-113">此屬性會使用包含作業所套用之簡短描述的字串。</span><span class="sxs-lookup"><span data-stu-id="15bd9-113">This attribute takes a string that contains a short description of the operation it is applied to.</span></span> <span data-ttu-id="15bd9-114">例如，下列程式碼示範如何使用 <xref:System.ComponentModel.DescriptionAttribute>來提供簡短描述。</span><span class="sxs-lookup"><span data-stu-id="15bd9-114">For example, the following code shows how to use the <xref:System.ComponentModel.DescriptionAttribute> to provide a short description.</span></span>  
  
```  
[OperationContract]  
[WebGet(UriTemplate="/template1", BodyStyle = WebMessageBodyStyle.Bare)]  
[Description("Description for GET /template1")]  
SyndicationFeedFormatter GetTemplate1();  
```  
  
 <span data-ttu-id="15bd9-115">若要開啟 WCF WEB HTTP 說明頁面，您必須加入端點行為至服務的端點。</span><span class="sxs-lookup"><span data-stu-id="15bd9-115">To turn on the WCF WEB HTTP Help page, you must add an endpoint behavior to your service's endpoints.</span></span> <span data-ttu-id="15bd9-116">這個動作可在組態或程式碼中完成。</span><span class="sxs-lookup"><span data-stu-id="15bd9-116">This can be done in configuration or code.</span></span> <span data-ttu-id="15bd9-117">若要啟用組態中的 WCF WEB HTTP 說明頁面，請使用 `<webHttp>``enableHelp` 項目加入端點行為，將 `true` 設為，並加入端點然後將其設定為使用端點行為。</span><span class="sxs-lookup"><span data-stu-id="15bd9-117">To enable the WCF WEB HTTP Help age in configuration, add an endpoint behavior with a `<webHttp>` element, set `enableHelp` to `true`, and add an endpoint and configure it to use the endpoint behavior.</span></span> <span data-ttu-id="15bd9-118">下列組態程式碼示範如何執行這項工作。</span><span class="sxs-lookup"><span data-stu-id="15bd9-118">The following configuration code shows how to do this.</span></span>  
  
```xml  
<endpointBehaviors>  
   <behavior name="RESTEndpointBehavior">  
      <webHttp enableHelp="true"/>  
   </behavior>  
</endpointBehaviors>  
<!-- ... -->  
<services>  
   <service behaviorConfiguration="RESTWebServiceBehavior" name="RESTWebService">      <endpoint address="" kind="webHttpEndpoint" behaviorConfiguration="RESTEndpointBehavior" contract="IHello" />  
  
      <!-- ... -->  
   </service>  
</services>  
```  
  
 <span data-ttu-id="15bd9-119">若要在程式碼中啟用 WCF Web HTTP 說明頁面，請加入服務端點，並將 <xref:System.ServiceModel.Description.WebHttpBehavior> 加入至端點設定，再將 <xref:System.ServiceModel.Description.WebHttpBehavior.HelpEnabled%2A> 設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="15bd9-119">To enable the WCF Web HTTP Help page in code, add a service endpoint and add a <xref:System.ServiceModel.Description.WebHttpBehavior> to the endpoint setting <xref:System.ServiceModel.Description.WebHttpBehavior.HelpEnabled%2A> to `true`.</span></span> <span data-ttu-id="15bd9-120">下列程式碼示範如何執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="15bd9-120">The following code shows how to do this.</span></span>  
  
```  
using (WebServiceHost host = new WebServiceHost(typeof(Service), new Uri("http://localhost:8000/Customers")))  
{  
   host.AddServiceEndpoint(typeof(ICustomerCollection), new WebHttpBinding(), "");
   host.Description.Endpoints[0].Behaviors.Add(new WebHttpBehavior { EnableHelp = true });  
   // ...  
}  
```  
  
 <span data-ttu-id="15bd9-121">說明頁面是含有標記的 XHTML 架構，可識別頁面的不同部分。</span><span class="sxs-lookup"><span data-stu-id="15bd9-121">The help page is XHTML based with mark-up that identifies the different parts of the page.</span></span> <span data-ttu-id="15bd9-122">如此可讓用戶端以程式設計方式，使用 <xref:System.Xml.Linq.XElement> 或其他 XLinq API 存取頁面。</span><span class="sxs-lookup"><span data-stu-id="15bd9-122">This enables clients to programmatically access the page using <xref:System.Xml.Linq.XElement> or other XLinq APIs.</span></span>  
  
## <a name="schemas-used-in-the-wcf-web-http-service-help-page"></a><span data-ttu-id="15bd9-123">WCF Web HTTP 服務說明頁面中使用的結構描述</span><span class="sxs-lookup"><span data-stu-id="15bd9-123">Schemas Used in the WCF Web HTTP Service Help Page</span></span>  
 <span data-ttu-id="15bd9-124">WCF Web HTTP 服務說明頁面會使用下列結構描述。</span><span class="sxs-lookup"><span data-stu-id="15bd9-124">The following schemas are used in the WCF Web HTTP service help page.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:tns="http://schemas.microsoft.com/2003/10/Serialization/" attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="http://schemas.microsoft.com/2003/10/Serialization/" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="anyType" nillable="true" type="xs:anyType" />  
  <xs:element name="anyURI" nillable="true" type="xs:anyURI" />  
  <xs:element name="base64Binary" nillable="true" type="xs:base64Binary" />  
  <xs:element name="boolean" nillable="true" type="xs:boolean" />  
  <xs:element name="byte" nillable="true" type="xs:byte" />  
  <xs:element name="dateTime" nillable="true" type="xs:dateTime" />  
  <xs:element name="decimal" nillable="true" type="xs:decimal" />  
  <xs:element name="double" nillable="true" type="xs:double" />  
  <xs:element name="float" nillable="true" type="xs:float" />  
  <xs:element name="int" nillable="true" type="xs:int" />  
  <xs:element name="long" nillable="true" type="xs:long" />  
  <xs:element name="QName" nillable="true" type="xs:QName" />  
  <xs:element name="short" nillable="true" type="xs:short" />  
  <xs:element name="string" nillable="true" type="xs:string" />  
  <xs:element name="unsignedByte" nillable="true" type="xs:unsignedByte" />  
  <xs:element name="unsignedInt" nillable="true" type="xs:unsignedInt" />  
  <xs:element name="unsignedLong" nillable="true" type="xs:unsignedLong" />  
  <xs:element name="unsignedShort" nillable="true" type="xs:unsignedShort" />  
  <xs:element name="char" nillable="true" type="tns:char" />  
  <xs:simpleType name="char">  
    <xs:restriction base="xs:int" />  
  </xs:simpleType>  
  <xs:element name="duration" nillable="true" type="tns:duration" />  
  <xs:simpleType name="duration">  
    <xs:restriction base="xs:duration">  
      <xs:pattern value="\-?P(\d*D)?(T(\d*H)?(\d*M)?(\d*(\.\d*)?S)?)?" />  
      <xs:minInclusive value="-P10675199DT2H48M5.4775808S" />  
      <xs:maxInclusive value="P10675199DT2H48M5.4775807S" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:element name="guid" nillable="true" type="tns:guid" />  
  <xs:simpleType name="guid">  
    <xs:restriction base="xs:string">  
      <xs:pattern value="[\da-fA-F]{8}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{12}" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:attribute name="FactoryType" type="xs:QName" />  
  <xs:attribute name="Id" type="xs:ID" />  
  <xs:attribute name="Ref" type="xs:IDREF" />  
</xs:schema>  
  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:tns="http://microsoft.com/wsdl/types/" elementFormDefault="qualified" targetNamespace="http://microsoft.com/wsdl/types/" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:simpleType name="guid">  
    <xs:restriction base="xs:string">  
      <xs:pattern value="[0-9a-fA-F]{8}-[0-9a-fA-F]{4}-[0-9a-fA-F]{4}-[0-9a-fA-F]{4}-[0-9a-fA-F]{12}" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="char">  
    <xs:restriction base="xs:unsignedShort" />  
  </xs:simpleType>  
</xs:schema>  
  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:tns="http://schemas.datacontract.org/2004/07/System" elementFormDefault="qualified" targetNamespace="http://schemas.datacontract.org/2004/07/System" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:import namespace="http://schemas.microsoft.com/2003/10/Serialization/" />  
  <xs:complexType name="DateTimeOffset">  
    <xs:annotation>  
      <xs:appinfo>  
        <IsValueType xmlns="http://schemas.microsoft.com/2003/10/Serialization/">true</IsValueType>  
      </xs:appinfo>  
    </xs:annotation>  
    <xs:sequence>  
      <xs:element name="DateTime" type="xs:dateTime" />  
      <xs:element name="OffsetMinutes" type="xs:short" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="DateTimeOffset" nillable="true" type="tns:DateTimeOffset" />  
  <xs:complexType name="DBNull">  
    <xs:sequence />  
  </xs:complexType>  
  <xs:element name="DBNull" nillable="true" type="tns:DBNull" />  
</xs:schema>  
  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:tns="http://schemas.microsoft.com/2003/10/Serialization/Arrays" xmlns:ser="http://schemas.microsoft.com/2003/10/Serialization/" elementFormDefault="qualified" targetNamespace="http://schemas.microsoft.com/2003/10/Serialization/Arrays" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:import namespace="http://schemas.microsoft.com/2003/10/Serialization/" />  
  <xs:complexType name="ArrayOfboolean">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="boolean" type="xs:boolean" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOfboolean" nillable="true" type="tns:ArrayOfboolean" />  
  <xs:complexType name="ArrayOfchar">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="char" type="ser:char" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOfchar" nillable="true" type="tns:ArrayOfchar" />  
  <xs:complexType name="ArrayOfdateTime">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="dateTime" type="xs:dateTime" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOfdateTime" nillable="true" type="tns:ArrayOfdateTime" />  
  <xs:complexType name="ArrayOfdecimal">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="decimal" type="xs:decimal" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOfdecimal" nillable="true" type="tns:ArrayOfdecimal" />  
  <xs:complexType name="ArrayOfdouble">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="double" type="xs:double" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOfdouble" nillable="true" type="tns:ArrayOfdouble" />  
  <xs:complexType name="ArrayOffloat">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="float" type="xs:float" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOffloat" nillable="true" type="tns:ArrayOffloat" />  
  <xs:complexType name="ArrayOfguid">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="guid" type="ser:guid" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOfguid" nillable="true" type="tns:ArrayOfguid" />  
  <xs:complexType name="ArrayOfint">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="int" type="xs:int" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOfint" nillable="true" type="tns:ArrayOfint" />  
  <xs:complexType name="ArrayOflong">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="long" type="xs:long" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOflong" nillable="true" type="tns:ArrayOflong" />  
  <xs:complexType name="ArrayOfshort">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="short" type="xs:short" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOfshort" nillable="true" type="tns:ArrayOfshort" />  
  <xs:complexType name="ArrayOfstring">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="string" nillable="true" type="xs:string" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOfstring" nillable="true" type="tns:ArrayOfstring" />  
  <xs:complexType name="ArrayOfduration">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="duration" type="ser:duration" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOfduration" nillable="true" type="tns:ArrayOfduration" />  
  <xs:complexType name="ArrayOfunsignedInt">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="unsignedInt" type="xs:unsignedInt" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOfunsignedInt" nillable="true" type="tns:ArrayOfunsignedInt" />  
  <xs:complexType name="ArrayOfunsignedLong">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="unsignedLong" type="xs:unsignedLong" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOfunsignedLong" nillable="true" type="tns:ArrayOfunsignedLong" />  
  <xs:complexType name="ArrayOfunsignedShort">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="unsignedShort" type="xs:unsignedShort" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOfunsignedShort" nillable="true" type="tns:ArrayOfunsignedShort" />  
  <xs:complexType name="ArrayOfQName">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="QName" nillable="true" type="xs:QName" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOfQName" nillable="true" type="tns:ArrayOfQName" />  
</xs:schema>  
```  
  
 <span data-ttu-id="15bd9-125">如需有關資料合約序列化結構描述的詳細資訊，請參閱[Data Contract Schema Reference](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="15bd9-125">For more information about the data contract serialization schema, see [Data Contract Schema Reference](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).</span></span>
