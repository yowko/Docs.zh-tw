---
title: "自訂權杖"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7fd8b38-c370-454f-ba3e-19759019f03d
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9509cb2c6478cf82cebd696ab92cd69a7e5b4097
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="custom-token"></a><span data-ttu-id="84d4f-102">自訂權杖</span><span class="sxs-lookup"><span data-stu-id="84d4f-102">Custom Token</span></span>
<span data-ttu-id="84d4f-103">這個範例示範如何將自訂權杖實作新增至 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 應用程式中。</span><span class="sxs-lookup"><span data-stu-id="84d4f-103">This sample demonstrates how to add a custom token implementation into a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application.</span></span> <span data-ttu-id="84d4f-104">範例會使用 `CreditCardToken`，將用戶端的信用卡資訊安全地傳遞至服務。</span><span class="sxs-lookup"><span data-stu-id="84d4f-104">The example uses a `CreditCardToken` to securely pass information about client credit cards to the service.</span></span> <span data-ttu-id="84d4f-105">權杖會在 WS-Security 訊息標頭中傳遞，並且是使用對稱安全性繫結項目，與訊息本文及其他訊息標頭一起經過簽署和加密。</span><span class="sxs-lookup"><span data-stu-id="84d4f-105">The token is passed in the WS-Security message header and is signed and encrypted using the symmetric security binding element along with message body and other message headers.</span></span> <span data-ttu-id="84d4f-106">當內建權杖的安全性不足時，這會十分有幫助。</span><span class="sxs-lookup"><span data-stu-id="84d4f-106">This is useful in cases where the built-in tokens are not sufficient.</span></span> <span data-ttu-id="84d4f-107">這個範例將示範如何提供自訂安全性權杖給服務，而不使用其中一個內建權杖。</span><span class="sxs-lookup"><span data-stu-id="84d4f-107">This sample demonstrates how to provide a custom security token to a service instead of using one of the built-in tokens.</span></span> <span data-ttu-id="84d4f-108">服務會實作定義要求-回覆通訊模式的合約。</span><span class="sxs-lookup"><span data-stu-id="84d4f-108">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84d4f-109">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="84d4f-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="84d4f-110">簡而言之，這個範例示範下面的情形：</span><span class="sxs-lookup"><span data-stu-id="84d4f-110">To summarize, this sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="84d4f-111">用戶端如何傳遞自訂安全性權杖給服務。</span><span class="sxs-lookup"><span data-stu-id="84d4f-111">How a client can pass a custom security token to a service.</span></span>  
  
-   <span data-ttu-id="84d4f-112">服務如何取用並驗證自訂安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="84d4f-112">How the service can consume and validate a custom security token.</span></span>  
  
-   <span data-ttu-id="84d4f-113">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務程式碼如何取得所收到關於安全性權杖 (包含自訂安全性權杖) 的資訊。</span><span class="sxs-lookup"><span data-stu-id="84d4f-113">How the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service code can obtain the information about received security tokens including the custom security token.</span></span>  
  
-   <span data-ttu-id="84d4f-114">如何使用伺服器的 X.509 憑證保護用於訊息加密和簽章的對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="84d4f-114">How the server's X.509 certificate is used to protect the symmetric key used for message encryption and signature.</span></span>  
  
## <a name="client-authentication-using-a-custom-security-token"></a><span data-ttu-id="84d4f-115">使用自訂安全性權杖的用戶端驗證</span><span class="sxs-lookup"><span data-stu-id="84d4f-115">Client Authentication Using a Custom Security Token</span></span>  
 <span data-ttu-id="84d4f-116">服務會使用 `BindingHelper` 和 `EchoServiceHost` 類別，公開透過程式設計所建立的單一端點。</span><span class="sxs-lookup"><span data-stu-id="84d4f-116">The service exposes a single endpoint that is programmatically created using `BindingHelper` and `EchoServiceHost` classes.</span></span> <span data-ttu-id="84d4f-117">端點是由位址、繫結及合約所組成。</span><span class="sxs-lookup"><span data-stu-id="84d4f-117">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="84d4f-118">繫結是透過使用 `SymmetricSecurityBindingElement` 和 `HttpTransportBindingElement` 的自訂繫結所設定。</span><span class="sxs-lookup"><span data-stu-id="84d4f-118">The binding is configured with a custom binding using `SymmetricSecurityBindingElement` and `HttpTransportBindingElement`.</span></span> <span data-ttu-id="84d4f-119">這個範例會設定 `SymmetricSecurityBindingElement`，使其在傳輸期間使用服務的 X.509 憑證來保護對稱金鑰，以及在 WS-Security 訊息標頭中傳遞自訂 `CreditCardToken` 做為簽署和加密的安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="84d4f-119">This sample sets the `SymmetricSecurityBindingElement` to use a service's X.509 certificate to protect the symmetric key during transmission and to pass a custom `CreditCardToken` in a WS-Security message header as a signed and encrypted security token.</span></span> <span data-ttu-id="84d4f-120">此行為會指定要用於用戶端驗證的服務認證，以及服務 X.509 憑證的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="84d4f-120">The behavior specifies the service credentials that are to be used for client authentication and also information about the service X.509 certificate.</span></span>  
  
```  
public static class BindingHelper  
{  
    public static Binding CreateCreditCardBinding()  
    {  
        HttpTransportBindingElement httpTransport = new HttpTransportBindingElement();  
  
        // The message security binding element will be configured to require a credit card.  
        // The token that is encrypted with the service's certificate.   
        SymmetricSecurityBindingElement messageSecurity = new SymmetricSecurityBindingElement();  
        messageSecurity.EndpointSupportingTokenParameters.SignedEncrypted.Add(new CreditCardTokenParameters());  
        X509SecurityTokenParameters x509ProtectionParameters = new X509SecurityTokenParameters();  
        x509ProtectionParameters.InclusionMode = SecurityTokenInclusionMode.Never;  
        messageSecurity.ProtectionTokenParameters = x509ProtectionParameters;  
        return new CustomBinding(messageSecurity, httpTransport);  
    }  
}  
```  
  
 <span data-ttu-id="84d4f-121">為了取用訊息中的信用卡權杖，範例會使用自訂服務認證來提供這項功能。</span><span class="sxs-lookup"><span data-stu-id="84d4f-121">To consume a credit card token in the message, the sample uses custom service credentials to provide this functionality.</span></span> <span data-ttu-id="84d4f-122">服務認證類別位於 `CreditCardServiceCredentials` 類別中，而且會在 `EchoServiceHost.InitializeRuntime` 方法中新增至服務主機的行為集合。</span><span class="sxs-lookup"><span data-stu-id="84d4f-122">The service credentials class is located in the `CreditCardServiceCredentials` class and is added to the behaviors collections of the service host in the `EchoServiceHost.InitializeRuntime` method.</span></span>  
  
```  
class EchoServiceHost : ServiceHost  
{  
    string creditCardFile;  
  
    public EchoServiceHost(parameters Uri[] addresses)  
        : base(typeof(EchoService), addresses)  
    {  
        creditCardFile = ConfigurationManager.AppSettings["creditCardFile"];  
        if (string.IsNullOrEmpty(creditCardFile))  
        {  
            throw new ConfigurationErrorsException("creditCardFile not specified in service config");  
        }  
  
        creditCardFile = String.Format("{0}\\{1}", System.Web.Hosting.HostingEnvironment.ApplicationPhysicalPath, creditCardFile);  
  
    }  
  
    override protected void InitializeRuntime()  
    {  
        // Create a credit card service credentials and add it to the behaviors.  
        CreditCardServiceCredentials serviceCredentials = new CreditCardServiceCredentials(this.creditCardFile);  
        serviceCredentials.ServiceCertificate.SetCertificate("CN=localhost", StoreLocation.LocalMachine, StoreName.My);  
        this.Description.Behaviors.Remove((typeof(ServiceCredentials)));  
        this.Description.Behaviors.Add(serviceCredentials);  
  
        // Register a credit card binding for the endpoint.  
        Binding creditCardBinding = BindingHelper.CreateCreditCardBinding();  
        this.AddServiceEndpoint(typeof(IEchoService), creditCardBinding, string.Empty);  
  
        base.InitializeRuntime();  
    }  
}  
```  
  
 <span data-ttu-id="84d4f-123">用戶端端點與服務端點的設定方式相似。</span><span class="sxs-lookup"><span data-stu-id="84d4f-123">The client endpoint is configured in a similar manner as the service endpoint.</span></span> <span data-ttu-id="84d4f-124">用戶端會使用相同的 `BindingHelper` 類別來建立繫結。</span><span class="sxs-lookup"><span data-stu-id="84d4f-124">The client uses the same `BindingHelper` class to create a binding.</span></span> <span data-ttu-id="84d4f-125">其餘的設定工作則在 `Client` 類別中進行。</span><span class="sxs-lookup"><span data-stu-id="84d4f-125">The rest of the setup is located in the `Client` class.</span></span> <span data-ttu-id="84d4f-126">用戶端還會將含有適當資料的 `CreditCardToken` 執行個體新增至用戶端端點行為集合，以設定要包含在 `CreditCardClientCredentials` 中的資訊，以及要包含在安裝程式碼中的服務 X.509 憑證資訊。</span><span class="sxs-lookup"><span data-stu-id="84d4f-126">The client also sets information to be contained in the `CreditCardToken` and information about the service X.509 certificate in the setup code by adding a `CreditCardClientCredentials` instance with the proper data to the client endpoint behaviors collection.</span></span> <span data-ttu-id="84d4f-127">範例會使用其主體名稱設為 `CN=localhost` 的 X.509 憑證做為服務憑證。</span><span class="sxs-lookup"><span data-stu-id="84d4f-127">The sample uses X.509 certificate with subject name set to `CN=localhost` as the service certificate.</span></span>  
  
```  
Binding creditCardBinding = BindingHelper.CreateCreditCardBinding();  
EndpointAddress serviceAddress = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
  
// Create a client with given client endpoint configuration  
channelFactory =   
new ChannelFactory<IEchoService>(creditCardBinding, serviceAddress);  
  
// configure the credit card credentials on the channel factory   
CreditCardClientCredentials credentials =   
      new CreditCardClientCredentials(  
      new CreditCardInfo(creditCardNumber, issuer, expirationTime));  
// configure the service certificate on the credentials  
credentials.ServiceCertificate.SetDefaultCertificate(  
      "CN=localhost", StoreLocation.LocalMachine, StoreName.My);  
  
// replace ClientCredentials with CreditCardClientCredentials  
channelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));  
channelFactory.Endpoint.Behaviors.Add(credentials);  
  
client = channelFactory.CreateChannel();  
  
Console.WriteLine("Echo service returned: {0}", client.Echo());  
  
((IChannel)client).Close();  
channelFactory.Close();  
```  
  
## <a name="custom-security-token-implementation"></a><span data-ttu-id="84d4f-128">自訂安全性權杖實作</span><span class="sxs-lookup"><span data-stu-id="84d4f-128">Custom Security Token Implementation</span></span>  
 <span data-ttu-id="84d4f-129">若要在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中啟用自訂安全性權杖，請建立自訂安全性權杖的物件表示。</span><span class="sxs-lookup"><span data-stu-id="84d4f-129">To enable a custom security token in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], create an object representation of the custom security token.</span></span> <span data-ttu-id="84d4f-130">範例會在 `CreditCardToken` 類別中產生這個表示。</span><span class="sxs-lookup"><span data-stu-id="84d4f-130">The sample has this representation in the `CreditCardToken` class.</span></span> <span data-ttu-id="84d4f-131">此物件表示負責保存所有相關的安全性權杖資訊，並提供安全性權杖所含安全性金鑰的清單。</span><span class="sxs-lookup"><span data-stu-id="84d4f-131">The object representation is responsible for holding all relevant security token information and to provide a list of security keys contained in the security token.</span></span> <span data-ttu-id="84d4f-132">在本例中，信用卡安全性權杖未包含任何安全性金鑰。</span><span class="sxs-lookup"><span data-stu-id="84d4f-132">In this case, the credit card security token does not contain any security key.</span></span>  
  
 <span data-ttu-id="84d4f-133">下一節會說明應該如何做，才能讓自訂權杖在網路上傳輸並且供 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 端點取用。</span><span class="sxs-lookup"><span data-stu-id="84d4f-133">The next section describes what must be done to enable a custom token to be transmitted over the wire and consumed by a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint.</span></span>  
  
```  
class CreditCardToken : SecurityToken  
{  
    CreditCardInfo cardInfo;  
    DateTime effectiveTime = DateTime.UtcNow;  
    string id;  
    ReadOnlyCollection<SecurityKey> securityKeys;  
  
    public CreditCardToken(CreditCardInfo cardInfo) : this(cardInfo, Guid.NewGuid().ToString()) { }  
  
    public CreditCardToken(CreditCardInfo cardInfo, string id)  
    {  
        if (cardInfo == null)  
            throw new ArgumentNullException("cardInfo");  
  
        if (id == null)  
            throw new ArgumentNullException("id");  
  
        this.cardInfo = cardInfo;  
        this.id = id;  
  
        // The credit card token is not capable of any cryptography.  
        this.securityKeys = new ReadOnlyCollection<SecurityKey>(new List<SecurityKey>());  
    }  
  
    public CreditCardInfo CardInfo { get { return this.cardInfo; } }  
  
    public override ReadOnlyCollection<SecurityKey> SecurityKeys { get { return this.securityKeys; } }  
  
    public override DateTime ValidFrom { get { return this.effectiveTime; } }  
    public override DateTime ValidTo { get { return this.cardInfo.ExpirationDate; } }  
    public override string Id { get { return this.id; } }  
}  
```  
  
## <a name="getting-the-custom-credit-card-token-to-and-from-the-message"></a><span data-ttu-id="84d4f-134">在訊息中存取自訂信用卡權杖</span><span class="sxs-lookup"><span data-stu-id="84d4f-134">Getting the Custom Credit Card Token to and from the Message</span></span>  
 <span data-ttu-id="84d4f-135">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的安全性權杖序列化程式會負責從訊息的 XML 中建立安全性權杖的物件表示，以及從安全性權杖的物件表示中建立 XML。</span><span class="sxs-lookup"><span data-stu-id="84d4f-135">Security token serializers in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are responsible for creating an object representation of security tokens from the XML in the message and creating a XML form of the security tokens.</span></span> <span data-ttu-id="84d4f-136">它們還負責像是讀取和寫入指向安全性權杖之金鑰識別項等其他的功能，但是本範例僅使用與安全性權杖相關的功能。</span><span class="sxs-lookup"><span data-stu-id="84d4f-136">They are also responsible for other functionality such as reading and writing key identifiers pointing to security tokens, but this example uses only security token-related functionality.</span></span> <span data-ttu-id="84d4f-137">若要啟用自訂權杖，就必須實作您自己的安全性權杖序列化程式。</span><span class="sxs-lookup"><span data-stu-id="84d4f-137">To enable a custom token you must implement your own security token serializer.</span></span> <span data-ttu-id="84d4f-138">本範例會使用 `CreditCardSecurityTokenSerializer` 類別來達到這個目的。</span><span class="sxs-lookup"><span data-stu-id="84d4f-138">This sample uses the `CreditCardSecurityTokenSerializer` class for this purpose.</span></span>  
  
 <span data-ttu-id="84d4f-139">在服務上，自訂序列化程式會讀取自訂權杖的 XML 表單，並由其中建立自訂權杖物件表示。</span><span class="sxs-lookup"><span data-stu-id="84d4f-139">On the service, the custom serializer reads the XML form of the custom token and creates the custom token object representation from it.</span></span>  
  
 <span data-ttu-id="84d4f-140">在用戶端上，`CreditCardSecurityTokenSerializer` 類別會將安全性權杖物件表示中包含的資訊寫入至 XML 寫入器。</span><span class="sxs-lookup"><span data-stu-id="84d4f-140">On the client, the `CreditCardSecurityTokenSerializer` class writes the information contained in the security token object representation into the XML writer.</span></span>  
  
```  
public class CreditCardSecurityTokenSerializer : WSSecurityTokenSerializer  
{  
    public CreditCardSecurityTokenSerializer(SecurityTokenVersion version) : base() { }  
  
    protected override bool CanReadTokenCore(XmlReader reader)  
    {  
        XmlDictionaryReader localReader = XmlDictionaryReader.CreateDictionaryReader(reader);  
  
        if (reader == null) throw new ArgumentNullException("reader");  
  
        if (reader.IsStartElement(Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace))  
            return true;  
  
        return base.CanReadTokenCore(reader);  
    }  
  
    protected override SecurityToken ReadTokenCore(XmlReader reader, SecurityTokenResolver tokenResolver)  
    {  
        if (reader == null) throw new ArgumentNullException("reader");  
  
        if (reader.IsStartElement(Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace))  
        {  
            string id = reader.GetAttribute(Constants.Id, Constants.WsUtilityNamespace);  
  
            reader.ReadStartElement();  
  
            // Read the credit card number.  
            string creditCardNumber = reader.ReadElementString(Constants.CreditCardNumberElementName, Constants.CreditCardTokenNamespace);  
  
            // Read the expiration date.  
            string expirationTimeString = reader.ReadElementString(Constants.CreditCardExpirationElementName, Constants.CreditCardTokenNamespace);  
            DateTime expirationTime = XmlConvert.ToDateTime(expirationTimeString, XmlDateTimeSerializationMode.Utc);  
  
            // Read the issuer of the credit card.  
            string creditCardIssuer = reader.ReadElementString(Constants.CreditCardIssuerElementName, Constants.CreditCardTokenNamespace);  
            reader.ReadEndElement();  
  
            CreditCardInfo cardInfo = new CreditCardInfo(creditCardNumber, creditCardIssuer, expirationTime);  
  
            return new CreditCardToken(cardInfo, id);  
        }  
        else  
        {  
            return WSSecurityTokenSerializer.DefaultInstance.ReadToken(reader, tokenResolver);  
        }  
    }  
  
    protected override bool CanWriteTokenCore(SecurityToken token)  
    {  
        if (token is CreditCardToken)  
            return true;  
  
        else  
            return base.CanWriteTokenCore(token);  
    }  
  
    protected override void WriteTokenCore(XmlWriter writer, SecurityToken token)  
    {  
        if (writer == null) { throw new ArgumentNullException("writer"); }  
        if (token == null) { throw new ArgumentNullException("token"); }  
  
        CreditCardToken c = token as CreditCardToken;  
        if (c != null)  
        {  
            writer.WriteStartElement(Constants.CreditCardTokenPrefix, Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace);  
            writer.WriteAttributeString(Constants.WsUtilityPrefix, Constants.Id, Constants.WsUtilityNamespace, token.Id);  
            writer.WriteElementString(Constants.CreditCardNumberElementName, Constants.CreditCardTokenNamespace, c.CardInfo.CardNumber);  
            writer.WriteElementString(Constants.CreditCardExpirationElementName, Constants.CreditCardTokenNamespace, XmlConvert.ToString(c.CardInfo.ExpirationDate, XmlDateTimeSerializationMode.Utc));  
            writer.WriteElementString(Constants.CreditCardIssuerElementName, Constants.CreditCardTokenNamespace, c.CardInfo.CardIssuer);  
            writer.WriteEndElement();  
            writer.Flush();  
        }  
        else  
        {  
            base.WriteTokenCore(writer, token);  
        }  
    }  
}  
```  
  
## <a name="how-token-provider-and-token-authenticator-classes-are-created"></a><span data-ttu-id="84d4f-141">建立權杖提供者和權杖驗證器類別的方式</span><span class="sxs-lookup"><span data-stu-id="84d4f-141">How Token Provider and Token Authenticator Classes are Created</span></span>  
 <span data-ttu-id="84d4f-142">用戶端和服務認證負責提供安全性權杖管理員執行個體。</span><span class="sxs-lookup"><span data-stu-id="84d4f-142">Client and service credentials are responsible for providing the security token manager instance.</span></span> <span data-ttu-id="84d4f-143">安全性權杖管理員執行個體可以用來取得權杖提供者、權杖驗證器和權杖序列化程式。</span><span class="sxs-lookup"><span data-stu-id="84d4f-143">The security token manager instance is used to get token providers, token authenticators and token serializers.</span></span>  
  
 <span data-ttu-id="84d4f-144">權杖提供者會根據用戶端或服務認證中包含的資訊，以建立權杖的物件表示，</span><span class="sxs-lookup"><span data-stu-id="84d4f-144">The token provider creates an object representation of the token based on the information contained in the client or service credentials.</span></span> <span data-ttu-id="84d4f-145">然後使用權杖序列化程式 (如上一節所討論的) 將權杖物件表示寫入訊息中。</span><span class="sxs-lookup"><span data-stu-id="84d4f-145">The token object representation is then written to the message using the token serializer (discussed in the previous section).</span></span>  
  
 <span data-ttu-id="84d4f-146">權杖驗證器會驗證抵達訊息的權杖。</span><span class="sxs-lookup"><span data-stu-id="84d4f-146">The token authenticator validates tokens that arrive in the message.</span></span> <span data-ttu-id="84d4f-147">傳入的權杖物件表示是權杖序列化程式所建立的。</span><span class="sxs-lookup"><span data-stu-id="84d4f-147">The incoming token object representation is created by the token serializer.</span></span> <span data-ttu-id="84d4f-148">這個物件表示會接著傳遞給權杖驗證器以供驗證。</span><span class="sxs-lookup"><span data-stu-id="84d4f-148">This object representation is then passed to the token authenticator for validation.</span></span> <span data-ttu-id="84d4f-149">當權杖成功通過驗證後，權杖驗證器便會傳回代表權杖內所含資訊的 `IAuthorizationPolicy` 物件集合。</span><span class="sxs-lookup"><span data-stu-id="84d4f-149">After the token is successfully validated, the token authenticator returns a collection of `IAuthorizationPolicy` objects that represent the information contained in the token.</span></span> <span data-ttu-id="84d4f-150">這項資訊稍後會在處理訊息時用來進行授權決策，以及提供應用程式的宣告。</span><span class="sxs-lookup"><span data-stu-id="84d4f-150">This information is used later during the message processing to perform authorization decisions and to provide claims for the application.</span></span> <span data-ttu-id="84d4f-151">在此範例中，信用卡權杖驗證器會使用 `CreditCardTokenAuthorizationPolicy` 來達成這個目的。</span><span class="sxs-lookup"><span data-stu-id="84d4f-151">In this example, the credit card token authenticator uses `CreditCardTokenAuthorizationPolicy` for this purpose.</span></span>  
  
 <span data-ttu-id="84d4f-152">權杖序列化程式會負責在網路傳輸上存取權杖的物件表示。</span><span class="sxs-lookup"><span data-stu-id="84d4f-152">The token serializer is responsible for getting the object representation of the token to and from the wire.</span></span> <span data-ttu-id="84d4f-153">上一節已討論過這一點。</span><span class="sxs-lookup"><span data-stu-id="84d4f-153">This is discussed in the previous section.</span></span>  
  
 <span data-ttu-id="84d4f-154">在此範例中，因為只是要以用戶端到服務的方向來傳輸信用卡權杖，所以在用戶端只使用了權杖提供者，而在服務上只使用權杖驗證器。</span><span class="sxs-lookup"><span data-stu-id="84d4f-154">In this sample, we use a token provider only on the client and a token authenticator only on the service, because we want to transmit a credit card token only in the client-to-service direction.</span></span>  
  
 <span data-ttu-id="84d4f-155">用戶端的這項功能是在 `CreditCardClientCrendentials`, `CreditCardClientCredentialsSecurityTokenManager` 和 `CreditCardTokenProvider` 類別中。</span><span class="sxs-lookup"><span data-stu-id="84d4f-155">The functionality on the client is located in the `CreditCardClientCrendentials`, `CreditCardClientCredentialsSecurityTokenManager` and `CreditCardTokenProvider` classes.</span></span>  
  
 <span data-ttu-id="84d4f-156">服務上的功能則是在 `CreditCardServiceCredentials`、`CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` 和 `CreditCardTokenAuthorizationPolicy` 類別中。</span><span class="sxs-lookup"><span data-stu-id="84d4f-156">On the service, the functionality resides in the `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` and `CreditCardTokenAuthorizationPolicy` classes.</span></span>  
  
```  
    public class CreditCardClientCredentials : ClientCredentials  
    {  
        CreditCardInfo creditCardInfo;  
  
        public CreditCardClientCredentials(CreditCardInfo creditCardInfo)  
            : base()  
        {  
            if (creditCardInfo == null)  
                throw new ArgumentNullException("creditCardInfo");  
  
            this.creditCardInfo = creditCardInfo;  
        }  
  
        public CreditCardInfo CreditCardInfo  
        {  
            get { return this.creditCardInfo; }  
        }  
  
        protected override ClientCredentials CloneCore()  
        {  
            return new CreditCardClientCredentials(this.creditCardInfo);  
        }  
  
        public override SecurityTokenManager CreateSecurityTokenManager()  
        {  
            return new CreditCardClientCredentialsSecurityTokenManager(this);  
        }  
    }  
  
public class CreditCardClientCredentialsSecurityTokenManager : ClientCredentialsSecurityTokenManager  
    {  
        CreditCardClientCredentials creditCardClientCredentials;  
  
        public CreditCardClientCredentialsSecurityTokenManager(CreditCardClientCredentials creditCardClientCredentials)  
            : base (creditCardClientCredentials)  
        {  
            this.creditCardClientCredentials = creditCardClientCredentials;  
        }  
  
        public override SecurityTokenProvider CreateSecurityTokenProvider(SecurityTokenRequirement tokenRequirement)  
        {  
            // handle this token for Custom  
            if (tokenRequirement.TokenType == Constants.CreditCardTokenType)  
                return new CreditCardTokenProvider(this.creditCardClientCredentials.CreditCardInfo);  
            // return server cert  
            else if (tokenRequirement is InitiatorServiceModelSecurityTokenRequirement)  
            {  
                if (tokenRequirement.TokenType == SecurityTokenTypes.X509Certificate)  
                {  
                    return new X509SecurityTokenProvider(creditCardClientCredentials.ServiceCertificate.DefaultCertificate);  
                }  
            }  
  
            return base.CreateSecurityTokenProvider(tokenRequirement);  
        }  
  
        public override SecurityTokenSerializer CreateSecurityTokenSerializer(SecurityTokenVersion version)  
        {  
  
            return new CreditCardSecurityTokenSerializer(version);  
        }  
  
    }  
  
    class CreditCardTokenProvider : SecurityTokenProvider  
    {  
        CreditCardInfo creditCardInfo;  
  
        public CreditCardTokenProvider(CreditCardInfo creditCardInfo) : base()  
        {  
            if (creditCardInfo == null)  
            {  
                throw new ArgumentNullException("creditCardInfo");  
            }  
            this.creditCardInfo = creditCardInfo;  
        }  
  
        protected override SecurityToken GetTokenCore(TimeSpan timeout)  
        {  
            SecurityToken result = new CreditCardToken(this.creditCardInfo);  
            return result;  
        }  
    }  
  
public class CreditCardServiceCredentials : ServiceCredentials  
    {  
        string creditCardFile;  
  
        public CreditCardServiceCredentials(string creditCardFile)  
            : base()  
        {   
            if (creditCardFile == null)  
                throw new ArgumentNullException("creditCardFile");  
  
            this.creditCardFile = creditCardFile;  
        }  
  
        public string CreditCardDataFile  
        {  
            get { return this.creditCardFile; }  
        }  
  
        protected override ServiceCredentials CloneCore()  
        {  
            return new CreditCardServiceCredentials(this.creditCardFile);  
        }  
  
        public override SecurityTokenManager CreateSecurityTokenManager()  
        {  
            return new CreditCardServiceCredentialsSecurityTokenManager(this);  
        }  
    }  
  
public class CreditCardServiceCredentialsSecurityTokenManager : ServiceCredentialsSecurityTokenManager  
{  
        CreditCardServiceCredentials creditCardServiceCredentials;  
  
        public CreditCardServiceCredentialsSecurityTokenManager(CreditCardServiceCredentials creditCardServiceCredentials)  
            : base(creditCardServiceCredentials)  
        {  
            this.creditCardServiceCredentials = creditCardServiceCredentials;  
        }  
  
        public override SecurityTokenAuthenticator CreateSecurityTokenAuthenticator(SecurityTokenRequirement tokenRequirement, out SecurityTokenResolver outOfBandTokenResolver)  
        {  
            if (tokenRequirement.TokenType == Constants.CreditCardTokenType)  
            {  
                outOfBandTokenResolver = null;  
                return new CreditCardTokenAuthenticator(creditCardServiceCredentials.CreditCardDataFile);  
            }  
  
            return base.CreateSecurityTokenAuthenticator(tokenRequirement, out outOfBandTokenResolver);  
        }  
  
        public override SecurityTokenSerializer CreateSecurityTokenSerializer(SecurityTokenVersion version)  
        {  
            return new CreditCardSecurityTokenSerializer(version);  
        }  
    }  
  
    class CreditCardTokenAuthenticator : SecurityTokenAuthenticator  
    {  
        string creditCardsFile;  
        public CreditCardTokenAuthenticator(string creditCardsFile)  
        {  
            this.creditCardsFile = creditCardsFile;  
        }  
  
        protected override bool CanValidateTokenCore(SecurityToken token)  
        {  
            return (token is CreditCardToken);  
        }  
  
        protected override ReadOnlyCollection<IAuthorizationPolicy> ValidateTokenCore(SecurityToken token)  
        {  
            CreditCardToken creditCardToken = token as CreditCardToken;  
  
            if (creditCardToken.CardInfo.ExpirationDate < DateTime.UtcNow)  
                throw new SecurityTokenValidationException("The credit card has expired");  
            if (!IsCardNumberAndExpirationValid(creditCardToken.CardInfo))  
                throw new SecurityTokenValidationException("Unknown or invalid credit card");  
  
            // the credit card token has only 1 claim - the card number. The issuer for the claim is the  
            // credit card issuer  
  
            DefaultClaimSet cardIssuerClaimSet = new DefaultClaimSet(new Claim(ClaimTypes.Name, creditCardToken.CardInfo.CardIssuer, Rights.PossessProperty));  
            DefaultClaimSet cardClaimSet = new DefaultClaimSet(cardIssuerClaimSet, new Claim(Constants.CreditCardNumberClaim, creditCardToken.CardInfo.CardNumber, Rights.PossessProperty));  
            List<IAuthorizationPolicy> policies = new List<IAuthorizationPolicy>(1);  
            policies.Add(new CreditCardTokenAuthorizationPolicy(cardClaimSet));  
            return policies.AsReadOnly();  
        }  
  
        /// <summary>  
        /// Helper method to check if a given credit card entry is present in the User DB  
        /// </summary>  
        private bool IsCardNumberAndExpirationValid(CreditCardInfo cardInfo)  
        {  
            try  
            {  
                using (StreamReader myStreamReader = new StreamReader(this.creditCardsFile))  
                {  
                    string line = "";  
                    while ((line = myStreamReader.ReadLine()) != null)  
                    {  
                        string[] splitEntry = line.Split('#');  
                        if (splitEntry[0] == cardInfo.CardNumber)  
                        {  
                            string expirationDateString = splitEntry[1].Trim();  
                            DateTime expirationDateOnFile = DateTime.Parse(expirationDateString, System.Globalization.DateTimeFormatInfo.InvariantInfo, System.Globalization.DateTimeStyles.AdjustToUniversal);  
                            if (cardInfo.ExpirationDate == expirationDateOnFile)  
                            {  
                                string issuer = splitEntry[2];  
                                return issuer.Equals(cardInfo.CardIssuer, StringComparison.InvariantCultureIgnoreCase);  
                            }  
                            else  
                            {  
                                return false;  
                            }  
                        }  
                    }  
                    return false;  
                }  
            }  
            catch (Exception e)  
            {  
                throw new Exception("BookStoreService: Error while retrieving credit card information from User DB " + e.ToString());  
            }  
        }  
    }  
  
    public class CreditCardTokenAuthorizationPolicy : IAuthorizationPolicy  
    {  
        string id;  
        ClaimSet issuer;  
        IEnumerable<ClaimSet> issuedClaimSets;  
  
        public CreditCardTokenAuthorizationPolicy(ClaimSet issuedClaims)  
        {  
            if (issuedClaims == null)  
                throw new ArgumentNullException("issuedClaims");  
            this.issuer = issuedClaims.Issuer;  
            this.issuedClaimSets = new ClaimSet[] { issuedClaims };  
            this.id = Guid.NewGuid().ToString();  
        }  
  
        public ClaimSet Issuer { get { return this.issuer; } }  
  
        public string Id { get { return this.id; } }  
  
        public bool Evaluate(EvaluationContext context, ref object state)  
        {  
            foreach (ClaimSet issuance in this.issuedClaimSets)  
            {  
                context.AddClaimSet(this, issuance);  
            }  
  
            return true;  
        }  
    }  
```  
  
## <a name="displaying-the-callers-information"></a><span data-ttu-id="84d4f-157">顯示呼叫端的資訊</span><span class="sxs-lookup"><span data-stu-id="84d4f-157">Displaying the Callers' Information</span></span>  
 <span data-ttu-id="84d4f-158">若要顯示呼叫者的資訊，請使用 `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets`，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="84d4f-158">To display the caller's information, use the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` as shown in the following sample code.</span></span> <span data-ttu-id="84d4f-159">`ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` 包含與目前呼叫者關聯的授權宣告。</span><span class="sxs-lookup"><span data-stu-id="84d4f-159">The `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contains authorization claims associated with the current caller.</span></span> <span data-ttu-id="84d4f-160">`CreditCardToken` 集合中的 `AuthorizationPolicies` 類別會提供這些宣告。</span><span class="sxs-lookup"><span data-stu-id="84d4f-160">The claims are supplied by the `CreditCardToken` class in its `AuthorizationPolicies` collection.</span></span>  
  
```  
bool TryGetStringClaimValue(ClaimSet claimSet, string claimType, out string claimValue)  
{  
    claimValue = null;  
    IEnumerable<Claim> matchingClaims = claimSet.FindClaims(claimType,  
        Rights.PossessProperty);  
    if (matchingClaims == null)  
        return false;  
    IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();  
    enumerator.MoveNext();  
    claimValue = (enumerator.Current.Resource == null) ? null :   
        enumerator.Current.Resource.ToString();  
    return true;  
}  
  
string GetCallerCreditCardNumber()  
{  
     foreach (ClaimSet claimSet in   
         ServiceSecurityContext.Current.AuthorizationContext.ClaimSets)  
     {  
         string creditCardNumber = null;  
         if (TryGetStringClaimValue(claimSet,   
             Constants.CreditCardNumberClaim, out creditCardNumber))  
             {  
                 string issuer;  
                 if (!TryGetStringClaimValue(claimSet.Issuer,  
                        ClaimTypes.Name, out issuer))  
                 {  
                     issuer = "Unknown";  
                 }  
                 return String.Format(  
                   "Credit card '{0}' issued by '{1}'",   
                   creditCardNumber, issuer);  
        }  
    }  
    return "Credit card is not known";  
}  
```  
  
 <span data-ttu-id="84d4f-161">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="84d4f-161">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="84d4f-162">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="84d4f-162">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="84d4f-163">設定批次檔</span><span class="sxs-lookup"><span data-stu-id="84d4f-163">Setup Batch File</span></span>  
 <span data-ttu-id="84d4f-164">本範例中所包含的 Setup.bat 批次檔可讓您使用相關的憑證設定伺服器，以執行需要伺服器憑證安全性的 IIS 裝載應用程式。</span><span class="sxs-lookup"><span data-stu-id="84d4f-164">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run the IIS-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="84d4f-165">這個批次檔必須經過修改才能跨電腦運作，或在非裝載的情況下運作。</span><span class="sxs-lookup"><span data-stu-id="84d4f-165">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="84d4f-166">下面提供批次檔的各區段簡要概觀，讓將批次檔得以修改為在適當的組態下執行。</span><span class="sxs-lookup"><span data-stu-id="84d4f-166">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
-   <span data-ttu-id="84d4f-167">建立伺服器憑證：</span><span class="sxs-lookup"><span data-stu-id="84d4f-167">Creating the server certificate:</span></span>  
  
     <span data-ttu-id="84d4f-168">下列 `Setup.bat` 批次檔中的程式行會建立要使用的伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="84d4f-168">The following lines from the `Setup.bat` batch file create the server certificate to be used.</span></span> <span data-ttu-id="84d4f-169">`%SERVER_NAME%` 變數會指定伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="84d4f-169">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="84d4f-170">您可以變更這個變數來指定自己的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="84d4f-170">Change this variable to specify your own server name.</span></span> <span data-ttu-id="84d4f-171">這個批次檔中的預設值為 localhost。</span><span class="sxs-lookup"><span data-stu-id="84d4f-171">The default in this batch file is localhost.</span></span> <span data-ttu-id="84d4f-172">如果您變更 `%SERVER_NAME%` 變數，就必須在 Client.cs 和 Service.cs 檔案中遍尋 localhost，並以您在 Setup.bat 指令碼中使用的伺服器名稱來取代 localhost 的所有例項。</span><span class="sxs-lookup"><span data-stu-id="84d4f-172">If you change the `%SERVER_NAME%` variable, you must go through the Client.cs and Service.cs files and replace all instances of localhost with the server name that you use in the Setup.bat script.</span></span>  
  
     <span data-ttu-id="84d4f-173">憑證會儲存在 `LocalMachine` 存放區位置下的 My (Personal) 存放區中。</span><span class="sxs-lookup"><span data-stu-id="84d4f-173">The certificate is stored in My (Personal) store under the `LocalMachine` store location.</span></span> <span data-ttu-id="84d4f-174">憑證會儲存在 IIS 裝載服務的 LocalMachine 存放區中。</span><span class="sxs-lookup"><span data-stu-id="84d4f-174">The certificate is stored in the LocalMachine store for the IIS-hosted services.</span></span> <span data-ttu-id="84d4f-175">對於自我裝載的服務，您應該以 CurrentUser 取代字串 LocalMachine，將批次檔改為在 CurrentUser 存放區的位置上儲存用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="84d4f-175">For self-hosted services, you should modify the batch file to store the client certificate in the CurrentUser store location by replacing the string LocalMachine with CurrentUser.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="84d4f-176">將伺服器憑證安裝至用戶端的受信任憑證存放區中：</span><span class="sxs-lookup"><span data-stu-id="84d4f-176">Installing the server certificate into client's trusted certificate store:</span></span>  
  
     <span data-ttu-id="84d4f-177">Setup.bat 批次檔中的下列程式行會將伺服器憑證複製到用戶端受信任人的存放區。</span><span class="sxs-lookup"><span data-stu-id="84d4f-177">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="84d4f-178">這是必要步驟，因為用戶端系統並未隱含信任 Makecert.exe 產生的憑證。</span><span class="sxs-lookup"><span data-stu-id="84d4f-178">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="84d4f-179">如果您已經有一個以用戶端信任的根憑證 (例如 Microsoft 所發行的憑證) 為基礎的憑證，就不需要這個將伺服器憑證填入用戶端憑證存放區的步驟。</span><span class="sxs-lookup"><span data-stu-id="84d4f-179">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    echo ************  
    echo copying server cert to client's TrustedPeople store  
    echo ************  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="84d4f-180">若要啟用從 IIS 裝載服務對憑證私密金鑰進行的存取，就必須將私密金鑰的適當權限授與用於執行 IIS 裝載處理序的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="84d4f-180">To enable access to the certificate private key from the IIS-hosted service, the user account under which the IIS-hosted process is running must be granted appropriate permissions for the private key.</span></span> <span data-ttu-id="84d4f-181">Setup.bat 指令碼中的最後幾個步驟將會完成這個部分。</span><span class="sxs-lookup"><span data-stu-id="84d4f-181">This is accomplished by last steps in the Setup.bat script.</span></span>  
  
    ```  
    echo ************  
    echo setting privileges on server certificates  
    echo ************  
    for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i  
    set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
    (ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
    iisreset  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="84d4f-182">Setup.bat 批次檔是設計用來從 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元執行。</span><span class="sxs-lookup"><span data-stu-id="84d4f-182">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="84d4f-183">在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元中設定的 PATH 環境變數會指向包含 Setup.bat 指令碼所需之可執行檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="84d4f-183">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="84d4f-184">若要設定和建置範例</span><span class="sxs-lookup"><span data-stu-id="84d4f-184">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="84d4f-185">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="84d4f-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="84d4f-186">若要建置此方案，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="84d4f-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="84d4f-187">若要在同一部電腦上執行範例</span><span class="sxs-lookup"><span data-stu-id="84d4f-187">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="84d4f-188">使用系統管理員權限來開啟 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元視窗，然後執行範例安裝資料夾中的 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="84d4f-188">Open a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="84d4f-189">這會安裝執行範例所需的所有憑證。確認路徑中包含 Makecert.exe 所在的資料夾。</span><span class="sxs-lookup"><span data-stu-id="84d4f-189">This installs all the certificates required for running the sample.Make sure that the path includes the folder where Makecert.exe is located.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84d4f-190">當您完成範例時，請務必執行 Cleanup.bat 以移除憑證。</span><span class="sxs-lookup"><span data-stu-id="84d4f-190">Be sure to remove the certificates by running Cleanup.bat when finished with the sample.</span></span> <span data-ttu-id="84d4f-191">其他安全性範例使用相同的憑證。</span><span class="sxs-lookup"><span data-stu-id="84d4f-191">Other security samples use the same certificates.</span></span>  
  
1.  <span data-ttu-id="84d4f-192">從 \client\bin 目錄啟動 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="84d4f-192">Launch Client.exe from client\bin directory.</span></span> <span data-ttu-id="84d4f-193">用戶端活動會顯示在用戶端主控台應用程式上。</span><span class="sxs-lookup"><span data-stu-id="84d4f-193">Client activity is displayed on the client console application.</span></span>  
  
2.  <span data-ttu-id="84d4f-194">如果用戶端和服務無法通訊，請參閱 [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b)。</span><span class="sxs-lookup"><span data-stu-id="84d4f-194">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computer"></a><span data-ttu-id="84d4f-195">若要跨電腦執行範例</span><span class="sxs-lookup"><span data-stu-id="84d4f-195">To run the sample across computer</span></span>  
  
1.  <span data-ttu-id="84d4f-196">在服務電腦上為服務二進位碼檔案建立一個目錄。</span><span class="sxs-lookup"><span data-stu-id="84d4f-196">Create a directory on the service computer for the service binaries.</span></span>  
  
2.  <span data-ttu-id="84d4f-197">將服務程式檔複製到服務電腦上的服務目錄中。</span><span class="sxs-lookup"><span data-stu-id="84d4f-197">Copy the service program files into the service directory on the service computer.</span></span> <span data-ttu-id="84d4f-198">別忘了複製 CreditCardFile.txt，否則信用卡驗證器將無法驗證用戶端傳來的信用卡資訊。</span><span class="sxs-lookup"><span data-stu-id="84d4f-198">Do not forget to copy CreditCardFile.txt; otherwise the credit card authenticator cannot validate credit card information sent from the client.</span></span> <span data-ttu-id="84d4f-199">同時，將 Setup.bat 和 Cleanup.bat 檔案複製到服務電腦中。</span><span class="sxs-lookup"><span data-stu-id="84d4f-199">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="84d4f-200">您伺服器憑證的主體名稱必須包含電腦的完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="84d4f-200">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="84d4f-201">只要將 `%SERVER_NAME%` 變數變更為裝載服務之電腦的完整名稱，您就可以使用 Setup.bat 建立憑證。</span><span class="sxs-lookup"><span data-stu-id="84d4f-201">You can create one using the Setup.bat if you change the `%SERVER_NAME%` variable to fully-qualified name of the computer where the service is hosted.</span></span> <span data-ttu-id="84d4f-202">請注意，您必須在使用系統管理員權限開啟的 Visual Studio 命令提示字元中，執行 Setup.bat 檔案。</span><span class="sxs-lookup"><span data-stu-id="84d4f-202">Note that the Setup.bat file must be run in a Visual Studio command prompt opened with administrator privileges.</span></span>  
  
4.  <span data-ttu-id="84d4f-203">將伺服器憑證複製到用戶端的 CurrentUser-TrustedPeople 存放區中。</span><span class="sxs-lookup"><span data-stu-id="84d4f-203">Copy the server certificate into the CurrentUser-TrustedPeople store on the client.</span></span> <span data-ttu-id="84d4f-204">只有在伺服器憑證不是由受信任的簽發者發行時才必須這麼做。</span><span class="sxs-lookup"><span data-stu-id="84d4f-204">You must do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5.  <span data-ttu-id="84d4f-205">在 EchoServiceHost.cs 檔案中，將憑證主體名稱的值改為指定完整電腦名稱，而不指定 localhost。</span><span class="sxs-lookup"><span data-stu-id="84d4f-205">In the EchoServiceHost.cs file, change the value of the certificate subject name to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="84d4f-206">將語言特定資料夾下 \client\bin\ 資料夾中的用戶端程式檔案複製到用戶端電腦。</span><span class="sxs-lookup"><span data-stu-id="84d4f-206">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
7.  <span data-ttu-id="84d4f-207">在 Client.cs 檔案中，變更端點的位址值以符合服務的新位址。</span><span class="sxs-lookup"><span data-stu-id="84d4f-207">In the Client.cs file, change the address value of the endpoint to match the new address of your service.</span></span>  
  
8.  <span data-ttu-id="84d4f-208">在 Client.cs 檔案中，變更服務 X.509 憑證的主體名稱以符合遠端主機的完整電腦名稱，而不使用 localhost。</span><span class="sxs-lookup"><span data-stu-id="84d4f-208">In the Client.cs file change the subject name of the service X.509 certificate to match the fully-qualified computer name of the remote host instead of localhost.</span></span>  
  
9. <span data-ttu-id="84d4f-209">在用戶端電腦上，從命令提示字元視窗啟動 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="84d4f-209">On the client computer, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="84d4f-210">如果用戶端和服務無法通訊，請參閱 [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b)。</span><span class="sxs-lookup"><span data-stu-id="84d4f-210">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="84d4f-211">若要在使用範例之後進行清除</span><span class="sxs-lookup"><span data-stu-id="84d4f-211">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="84d4f-212">當您完成執行範例後，請執行範例資料夾中的 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="84d4f-212">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84d4f-213">請參閱</span><span class="sxs-lookup"><span data-stu-id="84d4f-213">See Also</span></span>
