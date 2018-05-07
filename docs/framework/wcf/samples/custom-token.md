---
title: 自訂權杖
ms.date: 03/30/2017
ms.assetid: e7fd8b38-c370-454f-ba3e-19759019f03d
ms.openlocfilehash: 5850f97d6d3a66aacf82ab1cb2338240a75a00fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="custom-token"></a>自訂權杖
這個範例示範如何新增自訂權杖實作 Windows Communication Foundation (WCF) 應用程式。 範例會使用 `CreditCardToken`，將用戶端的信用卡資訊安全地傳遞至服務。 權杖會在 WS-Security 訊息標頭中傳遞，並且是使用對稱安全性繫結項目，與訊息本文及其他訊息標頭一起經過簽署和加密。 當內建權杖的安全性不足時，這會十分有幫助。 這個範例將示範如何提供自訂安全性權杖給服務，而不使用其中一個內建權杖。 服務會實作定義要求-回覆通訊模式的合約。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 簡而言之，這個範例示範下面的情形：  
  
-   用戶端如何傳遞自訂安全性權杖給服務。  
  
-   服務如何取用並驗證自訂安全性權杖。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務程式碼如何取得所收到關於安全性權杖 (包含自訂安全性權杖) 的資訊。  
  
-   如何使用伺服器的 X.509 憑證保護用於訊息加密和簽章的對稱金鑰。  
  
## <a name="client-authentication-using-a-custom-security-token"></a>使用自訂安全性權杖的用戶端驗證  
 服務會使用 `BindingHelper` 和 `EchoServiceHost` 類別，公開透過程式設計所建立的單一端點。 端點是由位址、繫結及合約所組成。 繫結是透過使用 `SymmetricSecurityBindingElement` 和 `HttpTransportBindingElement` 的自訂繫結所設定。 這個範例會設定 `SymmetricSecurityBindingElement`，使其在傳輸期間使用服務的 X.509 憑證來保護對稱金鑰，以及在 WS-Security 訊息標頭中傳遞自訂 `CreditCardToken` 做為簽署和加密的安全性權杖。 此行為會指定要用於用戶端驗證的服務認證，以及服務 X.509 憑證的相關資訊。  
  
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
  
 為了取用訊息中的信用卡權杖，範例會使用自訂服務認證來提供這項功能。 服務認證類別位於 `CreditCardServiceCredentials` 類別中，而且會在 `EchoServiceHost.InitializeRuntime` 方法中新增至服務主機的行為集合。  
  
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
  
 用戶端端點與服務端點的設定方式相似。 用戶端會使用相同的 `BindingHelper` 類別來建立繫結。 其餘的設定工作則在 `Client` 類別中進行。 用戶端還會將含有適當資料的 `CreditCardToken` 執行個體新增至用戶端端點行為集合，以設定要包含在 `CreditCardClientCredentials` 中的資訊，以及要包含在安裝程式碼中的服務 X.509 憑證資訊。 範例會使用其主體名稱設為 `CN=localhost` 的 X.509 憑證做為服務憑證。  
  
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
  
## <a name="custom-security-token-implementation"></a>自訂安全性權杖實作  
 若要在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中啟用自訂安全性權杖，請建立自訂安全性權杖的物件表示。 範例會在 `CreditCardToken` 類別中產生這個表示。 此物件表示負責保存所有相關的安全性權杖資訊，並提供安全性權杖所含安全性金鑰的清單。 在本例中，信用卡安全性權杖未包含任何安全性金鑰。  
  
 下一節會說明應該如何做，才能讓自訂權杖在網路上傳輸並且供 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 端點取用。  
  
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
  
## <a name="getting-the-custom-credit-card-token-to-and-from-the-message"></a>在訊息中存取自訂信用卡權杖  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的安全性權杖序列化程式會負責從訊息的 XML 中建立安全性權杖的物件表示，以及從安全性權杖的物件表示中建立 XML。 它們還負責像是讀取和寫入指向安全性權杖之金鑰識別項等其他的功能，但是本範例僅使用與安全性權杖相關的功能。 若要啟用自訂權杖，就必須實作您自己的安全性權杖序列化程式。 本範例會使用 `CreditCardSecurityTokenSerializer` 類別來達到這個目的。  
  
 在服務上，自訂序列化程式會讀取自訂權杖的 XML 表單，並由其中建立自訂權杖物件表示。  
  
 在用戶端上，`CreditCardSecurityTokenSerializer` 類別會將安全性權杖物件表示中包含的資訊寫入至 XML 寫入器。  
  
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
  
## <a name="how-token-provider-and-token-authenticator-classes-are-created"></a>建立權杖提供者和權杖驗證器類別的方式  
 用戶端和服務認證負責提供安全性權杖管理員執行個體。 安全性權杖管理員執行個體可以用來取得權杖提供者、權杖驗證器和權杖序列化程式。  
  
 權杖提供者會根據用戶端或服務認證中包含的資訊，以建立權杖的物件表示， 然後使用權杖序列化程式 (如上一節所討論的) 將權杖物件表示寫入訊息中。  
  
 權杖驗證器會驗證抵達訊息的權杖。 傳入的權杖物件表示是權杖序列化程式所建立的。 這個物件表示會接著傳遞給權杖驗證器以供驗證。 當權杖成功通過驗證後，權杖驗證器便會傳回代表權杖內所含資訊的 `IAuthorizationPolicy` 物件集合。 這項資訊稍後會在處理訊息時用來進行授權決策，以及提供應用程式的宣告。 在此範例中，信用卡權杖驗證器會使用 `CreditCardTokenAuthorizationPolicy` 來達成這個目的。  
  
 權杖序列化程式會負責在網路傳輸上存取權杖的物件表示。 上一節已討論過這一點。  
  
 在此範例中，因為只是要以用戶端到服務的方向來傳輸信用卡權杖，所以在用戶端只使用了權杖提供者，而在服務上只使用權杖驗證器。  
  
 用戶端的這項功能是在 `CreditCardClientCrendentials`, `CreditCardClientCredentialsSecurityTokenManager` 和 `CreditCardTokenProvider` 類別中。  
  
 服務上的功能則是在 `CreditCardServiceCredentials`、`CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` 和 `CreditCardTokenAuthorizationPolicy` 類別中。  
  
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
  
## <a name="displaying-the-callers-information"></a>顯示呼叫端的資訊  
 若要顯示呼叫者的資訊，請使用 `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets`，如下列範例程式碼所示。 `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` 包含與目前呼叫者關聯的授權宣告。 `CreditCardToken` 集合中的 `AuthorizationPolicies` 類別會提供這些宣告。  
  
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
  
 當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。 在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。  
  
## <a name="setup-batch-file"></a>設定批次檔  
 本範例中所包含的 Setup.bat 批次檔可讓您使用相關的憑證設定伺服器，以執行需要伺服器憑證安全性的 IIS 裝載應用程式。 這個批次檔必須經過修改才能跨電腦運作，或在非裝載的情況下運作。  
  
 下面提供批次檔的各區段簡要概觀，讓將批次檔得以修改為在適當的組態下執行。  
  
-   建立伺服器憑證：  
  
     下列 `Setup.bat` 批次檔中的程式行會建立要使用的伺服器憑證。 `%SERVER_NAME%` 變數會指定伺服器名稱。 您可以變更這個變數來指定自己的伺服器名稱。 這個批次檔中的預設值為 localhost。 如果您變更 `%SERVER_NAME%` 變數，就必須在 Client.cs 和 Service.cs 檔案中遍尋 localhost，並以您在 Setup.bat 指令碼中使用的伺服器名稱來取代 localhost 的所有例項。  
  
     憑證會儲存在 `LocalMachine` 存放區位置下的 My (Personal) 存放區中。 憑證會儲存在 IIS 裝載服務的 LocalMachine 存放區中。 對於自我裝載的服務，您應該以 CurrentUser 取代字串 LocalMachine，將批次檔改為在 CurrentUser 存放區的位置上儲存用戶端憑證。  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   將伺服器憑證安裝至用戶端的受信任憑證存放區中：  
  
     Setup.bat 批次檔中的下列程式行會將伺服器憑證複製到用戶端受信任人的存放區。 這是必要步驟，因為用戶端系統並未隱含信任 Makecert.exe 產生的憑證。 如果您已經有一個以用戶端信任的根憑證 (例如 Microsoft 所發行的憑證) 為基礎的憑證，就不需要這個將伺服器憑證填入用戶端憑證存放區的步驟。  
  
    ```  
    echo ************  
    echo copying server cert to client's TrustedPeople store  
    echo ************  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   若要啟用從 IIS 裝載服務對憑證私密金鑰進行的存取，就必須將私密金鑰的適當權限授與用於執行 IIS 裝載處理序的使用者帳戶。 Setup.bat 指令碼中的最後幾個步驟將會完成這個部分。  
  
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
>  Setup.bat 批次檔是設計用來從 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元執行。 在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元中設定的 PATH 環境變數會指向包含 Setup.bat 指令碼所需之可執行檔的目錄。  
  
#### <a name="to-set-up-and-build-the-sample"></a>若要設定和建置範例  
  
1.  請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置此方案，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>若要在同一部電腦上執行範例  
  
1.  使用系統管理員權限來開啟 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元視窗，然後執行範例安裝資料夾中的 Setup.bat。 這會安裝執行範例所需的所有憑證。確認路徑中包含 Makecert.exe 所在的資料夾。  
  
> [!NOTE]
>  當您完成範例時，請務必執行 Cleanup.bat 以移除憑證。 其他安全性範例使用相同的憑證。  
  
1.  從 \client\bin 目錄啟動 Client.exe。 用戶端活動會顯示在用戶端主控台應用程式上。  
  
2.  如果用戶端和服務無法通訊，請參閱[疑難排解提示](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)。  
  
#### <a name="to-run-the-sample-across-computer"></a>若要跨電腦執行範例  
  
1.  在服務電腦上為服務二進位碼檔案建立一個目錄。  
  
2.  將服務程式檔複製到服務電腦上的服務目錄中。 別忘了複製 CreditCardFile.txt，否則信用卡驗證器將無法驗證用戶端傳來的信用卡資訊。 同時，將 Setup.bat 和 Cleanup.bat 檔案複製到服務電腦中。  
  
3.  您伺服器憑證的主體名稱必須包含電腦的完整網域名稱。 只要將 `%SERVER_NAME%` 變數變更為裝載服務之電腦的完整名稱，您就可以使用 Setup.bat 建立憑證。 請注意，您必須在使用系統管理員權限開啟的 Visual Studio 命令提示字元中，執行 Setup.bat 檔案。  
  
4.  將伺服器憑證複製到用戶端的 CurrentUser-TrustedPeople 存放區中。 只有在伺服器憑證不是由受信任的簽發者發行時才必須這麼做。  
  
5.  在 EchoServiceHost.cs 檔案中，將憑證主體名稱的值改為指定完整電腦名稱，而不指定 localhost。  
  
6.  將語言特定資料夾下 \client\bin\ 資料夾中的用戶端程式檔案複製到用戶端電腦。  
  
7.  在 Client.cs 檔案中，變更端點的位址值以符合服務的新位址。  
  
8.  在 Client.cs 檔案中，變更服務 X.509 憑證的主體名稱以符合遠端主機的完整電腦名稱，而不使用 localhost。  
  
9. 在用戶端電腦上，從命令提示字元視窗啟動 Client.exe。  
  
10. 如果用戶端和服務無法通訊，請參閱[疑難排解提示](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)。  
  
#### <a name="to-clean-up-after-the-sample"></a>若要在使用範例之後進行清除  
  
1.  當您完成執行範例後，請執行範例資料夾中的 Cleanup.bat。  
  
## <a name="see-also"></a>另請參閱
