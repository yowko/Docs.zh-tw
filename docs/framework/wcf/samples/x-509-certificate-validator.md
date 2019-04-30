---
title: X.509 憑證驗證程式
ms.date: 03/30/2017
ms.assetid: 3b042379-02c4-4395-b927-e57c842fd3e0
ms.openlocfilehash: 88364aabf5df3a4f41d83613c0c4328b2d5979a0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949912"
---
# <a name="x509-certificate-validator"></a><span data-ttu-id="25c66-102">X.509 憑證驗證程式</span><span class="sxs-lookup"><span data-stu-id="25c66-102">X.509 Certificate Validator</span></span>
<span data-ttu-id="25c66-103">這個範例會示範如何實作自訂 X.509 憑證驗證程式。</span><span class="sxs-lookup"><span data-stu-id="25c66-103">This sample demonstrates how to implement a custom X.509 Certificate Validator.</span></span> <span data-ttu-id="25c66-104">當內建的 X.509 憑證驗證程式模式都不符合應用程式需求時，這個驗證程式就很有用。</span><span class="sxs-lookup"><span data-stu-id="25c66-104">This is useful in cases where none of the built-in X.509 Certificate Validation modes is appropriate for the requirements of the application.</span></span> <span data-ttu-id="25c66-105">這個範例示範的服務具有可接受自動發行之憑證的自訂驗證程式。</span><span class="sxs-lookup"><span data-stu-id="25c66-105">This sample shows a service that has a custom validator that accepts self-issued certificates.</span></span> <span data-ttu-id="25c66-106">用戶端會使用這類憑證來向服務驗證。</span><span class="sxs-lookup"><span data-stu-id="25c66-106">The client uses such a certificate to authenticate to the service.</span></span>

 <span data-ttu-id="25c66-107">注意:任何人都可以建構自動發行的憑證的服務所使用的自訂驗證程式是安全性低於 ChainTrust X509CertificateValidationMode 提供之預設行為。</span><span class="sxs-lookup"><span data-stu-id="25c66-107">Note: As anyone can construct a self-issued certificate the custom validator used by the service is less secure than the default behavior provided by the ChainTrust X509CertificateValidationMode.</span></span> <span data-ttu-id="25c66-108">在實際執行程式碼 (Production Code) 中使用這項驗證邏輯之前，應該要謹慎考量這些安全性含義。</span><span class="sxs-lookup"><span data-stu-id="25c66-108">The security implications of this should be carefully considered before using this validation logic in production code.</span></span>

 <span data-ttu-id="25c66-109">這個範例所示範的作業摘要如下：</span><span class="sxs-lookup"><span data-stu-id="25c66-109">In summary this sample demonstrates how:</span></span>

- <span data-ttu-id="25c66-110">用戶端可以使用 X.509 憑證進行驗證。</span><span class="sxs-lookup"><span data-stu-id="25c66-110">The client can be authenticated using an X.509 certificate.</span></span>

- <span data-ttu-id="25c66-111">伺服器會向自訂 X509CertificateValidator 驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="25c66-111">The server validates the client credentials against a custom X509CertificateValidator.</span></span>

- <span data-ttu-id="25c66-112">伺服器是使用該伺服器的 X.509 憑證來驗證的。</span><span class="sxs-lookup"><span data-stu-id="25c66-112">The server is authenticated using the server's X.509 certificate.</span></span>

 <span data-ttu-id="25c66-113">服務會公開 (Expose) 單一的端點來與已使用組態檔 App.config 定義之服務進行通訊。端點是由位址、繫結及合約所組成。</span><span class="sxs-lookup"><span data-stu-id="25c66-113">The service exposes a single endpoint for communicating with the service, defined using the configuration file App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="25c66-114">繫結設定的標準`wsHttpBinding`經由預設使用`WSSecurity`和用戶端憑證驗證。</span><span class="sxs-lookup"><span data-stu-id="25c66-114">The binding is configured with a standard `wsHttpBinding` that defaults to using `WSSecurity` and client certificate authentication.</span></span> <span data-ttu-id="25c66-115">服務行為會指定 [自訂] 模式，以驗證用戶端 X.509 憑證以及該驗證程式類別的類型。</span><span class="sxs-lookup"><span data-stu-id="25c66-115">The service behavior specifies the Custom mode for validating client X.509 certificates along with the type of the validator class.</span></span> <span data-ttu-id="25c66-116">行為也會使用 serviceCertificate 項目來指定伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="25c66-116">The behavior also specifies the server certificate using the serviceCertificate element.</span></span> <span data-ttu-id="25c66-117">伺服器憑證必須包含相同的值，如`SubjectName`作為`findValue`中[ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)。</span><span class="sxs-lookup"><span data-stu-id="25c66-117">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

```xml
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- use host/baseAddresses to configure base address -->
        <!-- provided by host -->
        <host>
          <baseAddresses>
            <add baseAddress =
                "http://localhost:8001/servicemodelsamples/service" />
          </baseAddresses>
        </host>
        <!-- use base address specified above, provide one endpoint -->
        <endpoint address="certificate"
               binding="wsHttpBinding"
               bindingConfiguration="Binding"
               contract="Microsoft.ServiceModel.Samples.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <!-- X509 certificate binding -->
        <binding name="Binding">
          <security mode="Message">
            <message clientCredentialType="Certificate" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceDebug includeExceptionDetailInFaults ="true"/>
          <serviceCredentials>
            <!-- The serviceCredentials behavior allows one -->
            <!-- to specify authentication constraints on -->
            <!-- client certificates. -->
            <clientCertificate>
              <!-- Setting the certificateValidationMode to -->
              <!-- Custom means that if the custom -->
              <!-- X509CertificateValidator does NOT throw -->
              <!-- an exception, then the provided certificate -->
              <!-- will be trusted without performing any -->
              <!-- validation beyond that performed by the custom -->
              <!-- validator. The security implications of this -->
              <!-- setting should be carefully considered before -->
              <!-- using Custom in production code. -->
              <authentication
                 certificateValidationMode="Custom"
                 customCertificateValidatorType =
"Microsoft.ServiceModel.Samples.CustomX509CertificateValidator, service" />
            </clientCertificate>
            <!-- The serviceCredentials behavior allows one to -->
            <!-- define a service certificate. -->
            <!-- A service certificate is used by a client to -->
            <!-- authenticate the service and provide message -->
            <!-- protection. This configuration references the -->
            <!-- "localhost" certificate installed during the setup -->
            <!-- instructions. -->
            <serviceCertificate findValue="localhost"
                 storeLocation="LocalMachine"
                 storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
      </system.serviceModel>
```

 <span data-ttu-id="25c66-118">用戶端的端點組態是由組態名稱、服務端點的絕對位址、繫結和合約所組成。</span><span class="sxs-lookup"><span data-stu-id="25c66-118">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="25c66-119">用戶端繫結已設定了適當的模式與訊息 `clientCredentialType`。</span><span class="sxs-lookup"><span data-stu-id="25c66-119">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>

```xml
<system.serviceModel>
    <client>
      <!-- X509 certificate based endpoint -->
      <endpoint name="Certificate"
        address=
        "http://localhost:8001/servicemodelsamples/service/certificate"
                binding="wsHttpBinding"
                bindingConfiguration="Binding"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>
    <bindings>
        <wsHttpBinding>
            <!-- X509 certificate binding -->
            <binding name="Binding">
                <security mode="Message">
                    <message clientCredentialType="Certificate" />
               </security>
            </binding>
       </wsHttpBinding>
    </bindings>
    <behaviors>
      <endpointBehaviors>
        <behavior name="ClientCertificateBehavior">
          <clientCredentials>
            <serviceCertificate>
              <!-- Setting the certificateValidationMode to -->
              <!-- PeerOrChainTrust means that if the certificate -->
              <!-- is in the user's Trusted People store, then it -->
              <!-- is trusted without performing a validation of -->
              <!-- the certificate's issuer chain. -->
              <!-- This setting is used here for convenience so -->
              <!-- that the sample can be run without having to -->
              <!-- have certificates issued by a certification -->
              <!-- authority (CA). This setting is less secure -->
              <!-- than the default, ChainTrust. The security -->
              <!-- implications of this setting should be -->
              <!-- carefully considered before using -->
              <!-- PeerOrChainTrust in production code.-->
              <authentication
                  certificateValidationMode="PeerOrChainTrust" />
            </serviceCertificate>
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>
  </system.serviceModel>
```

 <span data-ttu-id="25c66-120">用戶端實作會設定要使用的用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="25c66-120">The client implementation sets the client certificate to use.</span></span>

```csharp
// Create a client with Certificate endpoint configuration
CalculatorClient client = new CalculatorClient("Certificate");
try
{
    client.ClientCredentials.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "test1");

    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

    // Call the Subtract service operation.
    value1 = 145.00D;
    value2 = 76.54D;
    result = client.Subtract(value1, value2);
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

    // Call the Multiply service operation.
    value1 = 9.00D;
    value2 = 81.25D;
    result = client.Multiply(value1, value2);
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

    // Call the Divide service operation.
    value1 = 22.00D;
    value2 = 7.00D;
    result = client.Divide(value1, value2);
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);
    client.Close();
}
catch (TimeoutException e)
{
    Console.WriteLine("Call timed out : {0}", e.Message);
    client.Abort();
}
catch (CommunicationException e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
    client.Abort();
}
catch (Exception e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
    client.Abort();
}
```

 <span data-ttu-id="25c66-121">這個範例會使用自訂 X509CertificateValidator 以驗證憑證。</span><span class="sxs-lookup"><span data-stu-id="25c66-121">This sample uses a custom X509CertificateValidator to validate certificates.</span></span> <span data-ttu-id="25c66-122">此範例會實作衍生自 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 的 CustomX509CertificateValidator。</span><span class="sxs-lookup"><span data-stu-id="25c66-122">The sample implements CustomX509CertificateValidator, derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="25c66-123">如需詳細資訊，請參閱有關 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 的文件。</span><span class="sxs-lookup"><span data-stu-id="25c66-123">See documentation about <xref:System.IdentityModel.Selectors.X509CertificateValidator> for more information.</span></span> <span data-ttu-id="25c66-124">這個特定自訂驗證程式範例會實作 Validate 方法，以接受任何自動發行的 X.509 憑證，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="25c66-124">This particular custom validator sample implements the Validate method to accept any X.509 certificate that is self-issued as shown in the following code.</span></span>

```csharp
public class CustomX509CertificateValidator : X509CertificateValidator
{
  public override void Validate ( X509Certificate2 certificate )
  {
   // Only accept self-issued certificates
   if (certificate.Subject != certificate.Issuer)
     throw new Exception("Certificate is not self-issued");
   }
}
```

 <span data-ttu-id="25c66-125">一旦驗證程式在服務程式碼中實作，服務主機就必須收到要使用的驗證程式執行個體的相關通知。</span><span class="sxs-lookup"><span data-stu-id="25c66-125">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="25c66-126">這個動作是使用下列程式碼完成。</span><span class="sxs-lookup"><span data-stu-id="25c66-126">This is done using the following code.</span></span>

```csharp
serviceHost.Credentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.Custom;
serviceHost.Credentials.ClientCertificate.Authentication.CustomCertificateValidator = new CustomX509CertificateValidator();
```

 <span data-ttu-id="25c66-127">或者，您可以在組態中執行如下所示的動作。</span><span class="sxs-lookup"><span data-stu-id="25c66-127">Or you can do the same thing in configuration as follows.</span></span>

```xml
<behaviors>
    <serviceBehaviors>
     <behavior name="CalculatorServiceBehavior">
       ...
   <serviceCredentials>
    <!--The serviceCredentials behavior allows one to specify -->
    <!--authentication constraints on client certificates.-->
    <clientCertificate>
    <!-- Setting the certificateValidationMode to Custom means -->
    <!--that if the custom X509CertificateValidator does NOT -->
    <!--throw an exception, then the provided certificate will -->
    <!--be trusted without performing any validation beyond that -->
    <!--performed by the custom validator. The security -->
    <!--implications of this setting should be carefully -->
    <!--considered before using Custom in production code. -->
    <authentication certificateValidationMode="Custom"
       customCertificateValidatorType =
"Microsoft.ServiceModel.Samples. CustomX509CertificateValidator, service" />
   </clientCertificate>
   ...
  </behavior>
 </serviceBehaviors>
</behaviors>
```

 <span data-ttu-id="25c66-128">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="25c66-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="25c66-129">用戶端應該會成功呼叫所有方法。</span><span class="sxs-lookup"><span data-stu-id="25c66-129">The client should successfully call all the methods.</span></span> <span data-ttu-id="25c66-130">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="25c66-130">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="25c66-131">設定批次檔</span><span class="sxs-lookup"><span data-stu-id="25c66-131">Setup Batch File</span></span>
 <span data-ttu-id="25c66-132">本範例中所包含的 Setup.bat 批次檔可讓您使用相關的憑證設定伺服器，以執行需要伺服器憑證安全性的自我裝載應用程式。</span><span class="sxs-lookup"><span data-stu-id="25c66-132">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="25c66-133">這個批次檔必須經過修改才能跨電腦運作，或在非裝載的情況下運作。</span><span class="sxs-lookup"><span data-stu-id="25c66-133">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="25c66-134">下面提供批次檔的各區段簡要概觀，讓批次檔得以修改為在適當的組態下執行：</span><span class="sxs-lookup"><span data-stu-id="25c66-134">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="25c66-135">建立伺服器憑證：</span><span class="sxs-lookup"><span data-stu-id="25c66-135">Creating the server certificate:</span></span>

     <span data-ttu-id="25c66-136">下列 Setup.bat 批次檔中的程式行會建立要使用的伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="25c66-136">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="25c66-137">%SERVER_NAME% 變數會指定伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="25c66-137">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="25c66-138">您可以變更這個變數來指定自己的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="25c66-138">Change this variable to specify your own server name.</span></span> <span data-ttu-id="25c66-139">預設值為 localhost。</span><span class="sxs-lookup"><span data-stu-id="25c66-139">The default value is localhost.</span></span>

    ```bash
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="25c66-140">將伺服器憑證安裝至用戶端的受信任憑證存放區中：</span><span class="sxs-lookup"><span data-stu-id="25c66-140">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="25c66-141">Setup.bat 批次檔中的下列程式行會將伺服器憑證複製到用戶端受信任人的存放區。</span><span class="sxs-lookup"><span data-stu-id="25c66-141">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="25c66-142">這是必要步驟，因為用戶端系統並未隱含信任 Makecert.exe 產生的憑證。</span><span class="sxs-lookup"><span data-stu-id="25c66-142">This step is required since certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="25c66-143">如果您已經有一個以用戶端信任的根憑證 (例如 Microsoft 所發行的憑證) 為基礎的憑證，就不需要這個將伺服器憑證填入用戶端憑證存放區的步驟。</span><span class="sxs-lookup"><span data-stu-id="25c66-143">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```bash
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="25c66-144">建立用戶端憑證：</span><span class="sxs-lookup"><span data-stu-id="25c66-144">Creating the client certificate:</span></span>

     <span data-ttu-id="25c66-145">下列 Setup.bat 批次檔中的程式行會建立要使用的用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="25c66-145">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="25c66-146">%USER_NAME% 變數會指定用戶端名稱。</span><span class="sxs-lookup"><span data-stu-id="25c66-146">The %USER_NAME% variable specifies the client name.</span></span> <span data-ttu-id="25c66-147">這個值會設定為 "test1"，因為這是用戶端程式碼會尋找的名稱。</span><span class="sxs-lookup"><span data-stu-id="25c66-147">This value is set to "test1" because this is the name the client code looks for.</span></span> <span data-ttu-id="25c66-148">如果變更了 %USER_NAME% 的值，您就必須在 Client.cs 原始程式檔中變更對應的值，並重新建置該用戶端。</span><span class="sxs-lookup"><span data-stu-id="25c66-148">If you change the value of %USER_NAME% you must change the corresponding value in the Client.cs source file and rebuild the client.</span></span>

     <span data-ttu-id="25c66-149">憑證會儲存在 CurrentUser 存放區位置下的 My (Personal) 存放區中。</span><span class="sxs-lookup"><span data-stu-id="25c66-149">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>

    ```bash
    echo ************
    echo Client cert setup starting
    echo %USER_NAME%
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%USER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="25c66-150">將用戶端憑證安裝至伺服器的受信任憑證存放區中：</span><span class="sxs-lookup"><span data-stu-id="25c66-150">Installing the client certificate into server's trusted certificate store:</span></span>

     <span data-ttu-id="25c66-151">Setup.bat 批次檔中的下列程式行會將用戶端憑證複製到受信任人的存放區。</span><span class="sxs-lookup"><span data-stu-id="25c66-151">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="25c66-152">這是必要步驟，因為伺服器系統並未隱含信任 Makecert.exe 產生的憑證。</span><span class="sxs-lookup"><span data-stu-id="25c66-152">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="25c66-153">如果您已經有一個以信任的根憑證 (例如 Microsoft 所發行的憑證) 為基礎的憑證，就不需要這個將用戶端憑證填入伺服器憑證存放區的步驟。</span><span class="sxs-lookup"><span data-stu-id="25c66-153">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>

    ```bash
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="25c66-154">若要設定和建置範例</span><span class="sxs-lookup"><span data-stu-id="25c66-154">To set up and build the sample</span></span>

1. <span data-ttu-id="25c66-155">若要建置方案時，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="25c66-155">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

2. <span data-ttu-id="25c66-156">若要在單一或跨電腦的組態中執行本範例，請使用下列指示。</span><span class="sxs-lookup"><span data-stu-id="25c66-156">To run the sample in a single- or cross-computerconfiguration, use the following instructions.</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="25c66-157">若要在同一部電腦上執行範例</span><span class="sxs-lookup"><span data-stu-id="25c66-157">To run the sample on the same computer</span></span>

1. <span data-ttu-id="25c66-158">從範例安裝資料夾內以系統管理員權限開啟 Visual Studio 2012 命令提示字元執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="25c66-158">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="25c66-159">這會安裝執行範例所需的所有憑證。</span><span class="sxs-lookup"><span data-stu-id="25c66-159">This installs all the certificates required for running the sample.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="25c66-160">Setup.bat 批次檔被設計來從 Visual Studio 2012 命令提示字元執行。</span><span class="sxs-lookup"><span data-stu-id="25c66-160">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="25c66-161">路徑環境變數設定在 Visual Studio 2012 命令提示字元會指向包含 Setup.bat 指令碼所需的可執行檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="25c66-161">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="25c66-162">從 service\bin 啟動 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="25c66-162">Launch Service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="25c66-163">從 \client\bin 啟動 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="25c66-163">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="25c66-164">用戶端活動會顯示在用戶端主控台應用程式上。</span><span class="sxs-lookup"><span data-stu-id="25c66-164">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="25c66-165">如果用戶端和服務能夠進行通訊，請參閱[的 WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="25c66-165">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="25c66-166">若要跨電腦執行範例</span><span class="sxs-lookup"><span data-stu-id="25c66-166">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="25c66-167">在服務電腦上建立目錄。</span><span class="sxs-lookup"><span data-stu-id="25c66-167">Create a directory on the service computer.</span></span>  
  
2. <span data-ttu-id="25c66-168">將 \service\bin 中的服務程式檔複製到服務電腦上的虛擬目錄中。</span><span class="sxs-lookup"><span data-stu-id="25c66-168">Copy the service program files from \service\bin to the virtual directory on the service computer.</span></span> <span data-ttu-id="25c66-169">同時將 Setup.bat、Cleanup.bat、GetComputerName.vbs 和 ImportClientCert.bat 檔複製到服務電腦上。</span><span class="sxs-lookup"><span data-stu-id="25c66-169">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="25c66-170">在用戶端電腦上為用戶端二進位碼檔案建立一個目錄。</span><span class="sxs-lookup"><span data-stu-id="25c66-170">Create a directory on the client computerfor the client binaries.</span></span>  
  
4. <span data-ttu-id="25c66-171">將用戶端程式檔複製到用戶端電腦上的用戶端目錄。</span><span class="sxs-lookup"><span data-stu-id="25c66-171">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="25c66-172">同時，將 Setup.bat、Cleanup.bat 和 ImportServiceCert.bat 檔案複製到用戶端。</span><span class="sxs-lookup"><span data-stu-id="25c66-172">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="25c66-173">在伺服器上，執行`setup.bat service`在開發人員命令提示字元適用於 Visual Studio 開啟系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="25c66-173">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="25c66-174">執行`setup.bat`與`service`引數會建立服務憑證的完整網域名稱的電腦匯出為名為 Service.cer 的檔案的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="25c66-174">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computerand exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="25c66-175">編輯 Service.exe.config 以反映新的憑證名稱 (在`findValue`屬性中[ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) 做為電腦的完整網域名稱相同。</span><span class="sxs-lookup"><span data-stu-id="25c66-175">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="25c66-176">也會變更中的電腦名稱\<服務 > /\<baseAddresses > 從本機主機服務電腦的完整名稱的項目。</span><span class="sxs-lookup"><span data-stu-id="25c66-176">Also change the computer name in the \<service>/\<baseAddresses> element from localhost to fully qualified name of your service computer.</span></span>  
  
7. <span data-ttu-id="25c66-177">從服務目錄中將 Service.cer 檔案複製至用戶端電腦上的用戶端目錄。</span><span class="sxs-lookup"><span data-stu-id="25c66-177">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="25c66-178">在用戶端，執行`setup.bat client`在開發人員命令提示字元適用於 Visual Studio 開啟系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="25c66-178">On the client, run `setup.bat client` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="25c66-179">使用 `setup.bat` 引數來執行 `client`，就會建立名稱為 client.com 的用戶端憑證，並且會將用戶端憑證匯出為名為 Client.cer 的檔案。</span><span class="sxs-lookup"><span data-stu-id="25c66-179">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="25c66-180">在用戶端電腦上的 Client.exe.config 檔案中，變更端點的位址值以符合服務的新位址。</span><span class="sxs-lookup"><span data-stu-id="25c66-180">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="25c66-181">若要這麼做，請使用伺服器的完整網域名稱取代 localhost。</span><span class="sxs-lookup"><span data-stu-id="25c66-181">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="25c66-182">從用戶端目錄將 Client.cer 檔案複製到伺服器上的服務目錄中。</span><span class="sxs-lookup"><span data-stu-id="25c66-182">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="25c66-183">在用戶端，以系統管理員權限開啟的 Visual studio 中開發人員命令提示字元執行 ImportServiceCert.bat。</span><span class="sxs-lookup"><span data-stu-id="25c66-183">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="25c66-184">這樣會將服務憑證從 Service.cer 檔案匯入至 CurrentUser - TrustedPeople 存放區中。</span><span class="sxs-lookup"><span data-stu-id="25c66-184">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="25c66-185">在伺服器上，以系統管理員權限開啟的 Visual studio 中開發人員命令提示字元執行 ImportClientCert.bat。</span><span class="sxs-lookup"><span data-stu-id="25c66-185">On the server, run ImportClientCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="25c66-186">這樣便會從 Client.cer 檔將用戶端憑證匯入至 LocalMachine - TrustedPeople 存放區中。</span><span class="sxs-lookup"><span data-stu-id="25c66-186">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="25c66-187">在伺服器電腦上，從命令提示字元視窗啟動 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="25c66-187">On the server computer, launch Service.exe from the command prompt window.</span></span>  
  
14. <span data-ttu-id="25c66-188">在用戶端電腦上，從命令提示字元視窗啟動 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="25c66-188">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="25c66-189">如果用戶端和服務能夠進行通訊，請參閱[的 WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="25c66-189">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="25c66-190">若要在使用範例之後進行清除</span><span class="sxs-lookup"><span data-stu-id="25c66-190">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="25c66-191">當您完成執行範例後，請執行範例資料夾中的 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="25c66-191">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="25c66-192">這樣會從憑證存放區中移除伺服器與用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="25c66-192">This removes the server and client certificates from the certificate store.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="25c66-193">跨電腦執行此範例時，這個指令碼不會移除用戶端上的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="25c66-193">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="25c66-194">如果您已執行跨電腦使用憑證的 Windows Communication Foundation (WCF) 範例，請務必清除已安裝在 CurrentUser-TrustedPeople 存放區的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="25c66-194">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="25c66-195">若要這樣做，請使用下列命令：`certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` 例如： `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`。</span><span class="sxs-lookup"><span data-stu-id="25c66-195">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
