---
title: 訊息佇列上的訊息安全性
ms.date: 03/30/2017
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
ms.openlocfilehash: 9e9067c38d86bb74c569b6d648d84c7c9ff6fac6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989804"
---
# <a name="message-security-over-message-queuing"></a><span data-ttu-id="6237c-102">訊息佇列上的訊息安全性</span><span class="sxs-lookup"><span data-stu-id="6237c-102">Message Security over Message Queuing</span></span>
<span data-ttu-id="6237c-103">這個範例示範如何實作應用程式，該應用程式會針對用戶端使用具有 X.509v3 憑證驗證的 WS-Security，並透過 MSMQ 使用伺服器的 X.509v3 憑證來要求伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="6237c-103">This sample demonstrates how to implement an application that uses WS-Security with X.509v3 certificate authentication for the client and requires server authentication using the server's X.509v3 certificate over MSMQ.</span></span> <span data-ttu-id="6237c-104">有時候，為了確保 MSMQ 存放區中的訊息持續加密，並且讓應用程式可以執行其本身的訊息驗證，使用訊息安全性所產生的效果更為理想。</span><span class="sxs-lookup"><span data-stu-id="6237c-104">Message security is sometimes more desirable to ensure that the messages in the MSMQ store stay encrypted and the application can perform its own authentication of the message.</span></span>

 <span data-ttu-id="6237c-105">此樣本根據[交易 MSMQ 繫結](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)範例。</span><span class="sxs-lookup"><span data-stu-id="6237c-105">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="6237c-106">訊息會經過加密和簽署。</span><span class="sxs-lookup"><span data-stu-id="6237c-106">The messages are encrypted and signed.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6237c-107">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="6237c-107">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="6237c-108">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="6237c-108">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="6237c-109">如果服務優先執行，它就會檢查以確定佇列存在。</span><span class="sxs-lookup"><span data-stu-id="6237c-109">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="6237c-110">如果佇列不存在，服務將建立一個佇列。</span><span class="sxs-lookup"><span data-stu-id="6237c-110">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="6237c-111">您可以先執行服務來建立佇列，也可以透過 MSMQ 佇列管理員建立佇列。</span><span class="sxs-lookup"><span data-stu-id="6237c-111">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="6237c-112">請依照下列步驟，在 Windows 2008 中建立佇列。</span><span class="sxs-lookup"><span data-stu-id="6237c-112">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="6237c-113">開啟 Visual Studio 2012 中的 伺服器管理員。</span><span class="sxs-lookup"><span data-stu-id="6237c-113">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="6237c-114">依序展開**功能** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6237c-114">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="6237c-115">以滑鼠右鍵按一下**私用訊息佇列**，然後選取**新增**，**私用佇列**。</span><span class="sxs-lookup"><span data-stu-id="6237c-115">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="6237c-116">請檢查**Transactional**  方塊中。</span><span class="sxs-lookup"><span data-stu-id="6237c-116">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="6237c-117">輸入`ServiceModelSamplesTransacted`做為新佇列的名稱。</span><span class="sxs-lookup"><span data-stu-id="6237c-117">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="6237c-118">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="6237c-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="6237c-119">若要在同一部電腦上執行範例</span><span class="sxs-lookup"><span data-stu-id="6237c-119">To run the sample on the same computer</span></span>

1. <span data-ttu-id="6237c-120">確認路徑中包含 Makecert.exe 和 FindPrivateKey.exe 所在的資料夾。</span><span class="sxs-lookup"><span data-stu-id="6237c-120">Ensure that the path includes the folder that contains Makecert.exe and FindPrivateKey.exe.</span></span>

2. <span data-ttu-id="6237c-121">從範例安裝資料夾執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="6237c-121">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="6237c-122">這會安裝執行範例所需的所有憑證。</span><span class="sxs-lookup"><span data-stu-id="6237c-122">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="6237c-123">當您完成範例時，請務必執行 Cleanup.bat 以移除憑證。</span><span class="sxs-lookup"><span data-stu-id="6237c-123">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="6237c-124">其他安全性範例使用相同的憑證。</span><span class="sxs-lookup"><span data-stu-id="6237c-124">Other security samples use the same certificates.</span></span>  
  
3. <span data-ttu-id="6237c-125">從 \service\bin 啟動 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="6237c-125">Launch Service.exe from \service\bin.</span></span>  
  
4. <span data-ttu-id="6237c-126">從 \client\bin 啟動 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="6237c-126">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="6237c-127">用戶端活動會顯示在用戶端主控台應用程式上。</span><span class="sxs-lookup"><span data-stu-id="6237c-127">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="6237c-128">如果用戶端和服務能夠進行通訊，請參閱[的 WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="6237c-128">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="6237c-129">若要跨電腦執行範例</span><span class="sxs-lookup"><span data-stu-id="6237c-129">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="6237c-130">將 Setup.bat、Cleanup.bat 和 ImportClientCert.bat 檔案複製到服務電腦。</span><span class="sxs-lookup"><span data-stu-id="6237c-130">Copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
2. <span data-ttu-id="6237c-131">在用戶端電腦上為用戶端二進位碼檔案建立一個目錄。</span><span class="sxs-lookup"><span data-stu-id="6237c-131">Create a directory on the client computer for the client binaries.</span></span>  
  
3. <span data-ttu-id="6237c-132">將用戶端程式檔複製到用戶端電腦上的用戶端目錄。</span><span class="sxs-lookup"><span data-stu-id="6237c-132">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="6237c-133">同時，將 Setup.bat、Cleanup.bat 和 ImportServiceCert.bat 檔案複製到用戶端。</span><span class="sxs-lookup"><span data-stu-id="6237c-133">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
4. <span data-ttu-id="6237c-134">在伺服器上執行 `setup.bat service`。</span><span class="sxs-lookup"><span data-stu-id="6237c-134">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="6237c-135">執行`setup.bat`與`service`引數會建立具有電腦完整網域名稱的服務憑證，並將服務憑證匯出為名為 Service.cer 的檔案。</span><span class="sxs-lookup"><span data-stu-id="6237c-135">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
5. <span data-ttu-id="6237c-136">編輯服務的 service.exe.config 以反映新的憑證名稱 (在`findValue`屬性中[ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) 做為電腦的完整網域名稱相同。</span><span class="sxs-lookup"><span data-stu-id="6237c-136">Edit service's service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
6. <span data-ttu-id="6237c-137">從服務目錄中將 Service.cer 檔案複製至用戶端電腦上的用戶端目錄。</span><span class="sxs-lookup"><span data-stu-id="6237c-137">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
7. <span data-ttu-id="6237c-138">在用戶端上執行 `setup.bat client`。</span><span class="sxs-lookup"><span data-stu-id="6237c-138">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="6237c-139">使用 `setup.bat` 引數來執行 `client`，就會建立名稱為 client.com 的用戶端憑證，並且會將用戶端憑證匯出為名為 Client.cer 的檔案。</span><span class="sxs-lookup"><span data-stu-id="6237c-139">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
8. <span data-ttu-id="6237c-140">在用戶端電腦上的 Client.exe.config 檔案中，變更端點的位址值以符合服務的新位址。</span><span class="sxs-lookup"><span data-stu-id="6237c-140">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="6237c-141">若要這麼做，請使用伺服器的完整網域名稱取代 localhost。</span><span class="sxs-lookup"><span data-stu-id="6237c-141">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  <span data-ttu-id="6237c-142">您也必須變更服務的憑證名稱，讓它和服務電腦的完整網域名稱相同 (在 `findValue` 下 `defaultCertificate` 項目的 `serviceCertificate` 屬性中 `clientCredentials`)。</span><span class="sxs-lookup"><span data-stu-id="6237c-142">You must also change the certificate name of the service to be the same as the fully-qualified domain name of the service computer (in the `findValue` attribute in the `defaultCertificate` element of `serviceCertificate` under `clientCredentials`).</span></span>  
  
9. <span data-ttu-id="6237c-143">從用戶端目錄將 Client.cer 檔案複製到伺服器上的服務目錄中。</span><span class="sxs-lookup"><span data-stu-id="6237c-143">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
10. <span data-ttu-id="6237c-144">在用戶端上執行 `ImportServiceCert.bat`。</span><span class="sxs-lookup"><span data-stu-id="6237c-144">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="6237c-145">這樣會將服務憑證從 Service.cer 檔案匯入至 CurrentUser - TrustedPeople 存放區中。</span><span class="sxs-lookup"><span data-stu-id="6237c-145">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
11. <span data-ttu-id="6237c-146">在伺服器上執行 `ImportClientCert.bat`，這樣會從 Client.cer 檔案中將用戶端憑證匯入至 LocalMachine - TrustedPeople 存放區中。</span><span class="sxs-lookup"><span data-stu-id="6237c-146">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="6237c-147">在服務電腦上，從命令提示字元啟動 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="6237c-147">On the service computer, launch Service.exe from the command prompt.</span></span>  
  
13. <span data-ttu-id="6237c-148">在用戶端電腦上，從命令提示字元啟動 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="6237c-148">On the client computer, launch Client.exe from the command prompt.</span></span> <span data-ttu-id="6237c-149">如果用戶端和服務能夠進行通訊，請參閱[的 WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="6237c-149">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="6237c-150">若要在使用範例之後進行清除</span><span class="sxs-lookup"><span data-stu-id="6237c-150">To clean up after the sample</span></span>  
  
- <span data-ttu-id="6237c-151">當您完成執行範例後，請執行範例資料夾中的 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="6237c-151">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6237c-152">跨電腦執行此範例時，這個指令碼不會移除用戶端上的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="6237c-152">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="6237c-153">如果您已執行跨電腦使用憑證的 Windows Communication Foundation (WCF) 範例，請務必清除已安裝在 CurrentUser-TrustedPeople 存放區的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="6237c-153">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="6237c-154">若要這樣做，請使用下列命令：`certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` 例如： `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`。</span><span class="sxs-lookup"><span data-stu-id="6237c-154">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>

## <a name="requirements"></a><span data-ttu-id="6237c-155">需求</span><span class="sxs-lookup"><span data-stu-id="6237c-155">Requirements</span></span>
 <span data-ttu-id="6237c-156">這個範例需要安裝並執行 MSMQ。</span><span class="sxs-lookup"><span data-stu-id="6237c-156">This sample requires that MSMQ is installed and running.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="6237c-157">示範</span><span class="sxs-lookup"><span data-stu-id="6237c-157">Demonstrates</span></span>
 <span data-ttu-id="6237c-158">用戶端會使用服務的公開金鑰對訊息加密，再使用它自己的憑證來簽署訊息。</span><span class="sxs-lookup"><span data-stu-id="6237c-158">The client encrypts the message using the public key of the service and signs the message using its own certificate.</span></span> <span data-ttu-id="6237c-159">從佇列讀取訊息的服務會使用其受信任人存放區中的憑證來驗證用戶端憑證，</span><span class="sxs-lookup"><span data-stu-id="6237c-159">The service reading the message from the queue authenticates the client certificate with the certificate in its trusted people store.</span></span> <span data-ttu-id="6237c-160">然後解密訊息，並將它分派至服務作業。</span><span class="sxs-lookup"><span data-stu-id="6237c-160">It then decrypts the message and dispatches the message to the service operation.</span></span>

 <span data-ttu-id="6237c-161">Windows Communication Foundation (WCF) 訊息會當做 MSMQ 訊息本文中承載傳送，因為 MSMQ 存放區的主體會保持加密。</span><span class="sxs-lookup"><span data-stu-id="6237c-161">Because the Windows Communication Foundation (WCF) message is carried as a payload in the body of the MSMQ message, the body remains encrypted in the MSMQ store.</span></span> <span data-ttu-id="6237c-162">這可以保護訊息，避免不該發生的洩漏風險。</span><span class="sxs-lookup"><span data-stu-id="6237c-162">This secures the message from unwanted disclosure of the message.</span></span> <span data-ttu-id="6237c-163">請注意，MSMQ 本身並不知道它所攜帶的訊息是否有加密。</span><span class="sxs-lookup"><span data-stu-id="6237c-163">Note that MSMQ itself is not aware whether the message it is carrying is encrypted.</span></span>

 <span data-ttu-id="6237c-164">此範例示範如何將訊息層級上的相互驗證與 MSMQ 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="6237c-164">The sample demonstrates how mutual authentication at the message level can be used with MSMQ.</span></span> <span data-ttu-id="6237c-165">憑證是透過超出範圍之外的方式進行交換。</span><span class="sxs-lookup"><span data-stu-id="6237c-165">The certificates are exchanged out-of-band.</span></span> <span data-ttu-id="6237c-166">對佇列應用程式而言，一定都會採用這種方式，因為服務和用戶端並不需要同時啟動和執行。</span><span class="sxs-lookup"><span data-stu-id="6237c-166">This is always the case with queued application because the service and the client do not have to be up and running at the same time.</span></span>

## <a name="description"></a><span data-ttu-id="6237c-167">描述</span><span class="sxs-lookup"><span data-stu-id="6237c-167">Description</span></span>
 <span data-ttu-id="6237c-168">範例用戶端與服務程式碼完全一樣[交易 MSMQ 繫結](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)其中一項差異的範例。</span><span class="sxs-lookup"><span data-stu-id="6237c-168">The sample client and service code are the same as the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample with one difference.</span></span> <span data-ttu-id="6237c-169">作業合約附有保護層級的標註，這表示訊息必須經過簽署並加密。</span><span class="sxs-lookup"><span data-stu-id="6237c-169">The operation contract is annotated with protection level, which suggests that the message must be signed and encrypted.</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="6237c-170">為了確定是使用識別服務和用戶端所需的權杖來保護訊息安全，App.config 會包含認證資訊。</span><span class="sxs-lookup"><span data-stu-id="6237c-170">To ensure that the message is secured using the required token to identify the service and client, the App.config contains credential information.</span></span>

 <span data-ttu-id="6237c-171">用戶端組態會指定服務憑證來驗證服務。</span><span class="sxs-lookup"><span data-stu-id="6237c-171">The client configuration specifies the service certificate to authenticate the service.</span></span> <span data-ttu-id="6237c-172">它使用 LocalMachine 存放區做為可信賴之服務有效性的受信任存放區。</span><span class="sxs-lookup"><span data-stu-id="6237c-172">It uses its LocalMachine store as the trusted store to rely on the validity of the service.</span></span> <span data-ttu-id="6237c-173">它也會指定用戶端憑證，其中附有用戶端之服務驗證的訊息。</span><span class="sxs-lookup"><span data-stu-id="6237c-173">It also specifies the client certificate that is attached with the message for service authentication of the client.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>

  <system.serviceModel>

    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"
                binding="netMsmqBinding"
                bindingConfiguration="messageSecurityBinding"
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor"
                behaviorConfiguration="ClientCertificateBehavior" />
    </client>

    <bindings>
        <netMsmqBinding>
            <binding name="messageSecurityBinding">
                <security mode="Message">
                    <message clientCredentialType="Certificate"/>
                </security>
            </binding>
        </netMsmqBinding>
    </bindings>

    <behaviors>
      <endpointBehaviors>
        <behavior name="ClientCertificateBehavior">
          <!--
        The clientCredentials behavior allows one to define a certificate to present to a service.
        A certificate is used by a client to authenticate itself to the service and provide message integrity.
        This configuration references the "client.com" certificate installed during the setup instructions.
        -->
          <clientCredentials>
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />
            <serviceCertificate>
                <defaultCertificate findValue="localhost" storeLocation="CurrentUser" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it is trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </serviceCertificate>
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>

  </system.serviceModel>
</configuration>
```

 <span data-ttu-id="6237c-174">請注意，安全性模式是設定為 Message，而 ClientCredentialType 則設定為 Certificate。</span><span class="sxs-lookup"><span data-stu-id="6237c-174">Note that the security mode is set to Message and the ClientCredentialType is set to Certificate.</span></span>

 <span data-ttu-id="6237c-175">服務組態會包含服務行為，以指定用戶端驗證服務時所使用的服務認證。</span><span class="sxs-lookup"><span data-stu-id="6237c-175">The service configuration includes a service behavior that specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="6237c-176">伺服器憑證主體名稱中指定`findValue`屬性中[ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)。</span><span class="sxs-lookup"><span data-stu-id="6237c-176">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>

  <appSettings>
    <!-- Use appSetting to configure MSMQ queue name. -->
    <add key="queueName" value=".\private$\ServiceModelSamplesMessageSecurity" />
  </appSettings>

  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.OrderProcessorService"
          behaviorConfiguration="PurchaseOrderServiceBehavior">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
          </baseAddresses>
        </host>
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"
                  binding="netMsmqBinding"
                  bindingConfiguration="messageSecurityBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
        <!-- The mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex. -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>

    <bindings>
        <netMsmqBinding>
            <binding name="messageSecurityBinding">
                <security mode="Message">
                    <message clientCredentialType="Certificate" />
                </security>
            </binding>
        </netMsmqBinding>
    </bindings>

    <behaviors>
      <serviceBehaviors>
        <behavior name="PurchaseOrderServiceBehavior">
          <serviceMetadata httpGetEnabled="True"/>
          <!--
               The serviceCredentials behavior allows one to define a service certificate.
               A service certificate is used by the service to authenticate itself to its clients and to provide message protection.
               This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
            <clientCertificate>
                <certificate findValue="client.com" storeLocation="LocalMachine" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it is trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </clientCertificate>
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>

</configuration>
```

 <span data-ttu-id="6237c-177">這個範例示範如何使用組態控制驗證以及如何從安全性內容取得呼叫者身分識別，如下列範例程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="6237c-177">The sample demonstrates controlling authentication using configuration, and how to obtain the caller’s identity from the security context, as shown in the following sample code:</span></span>

```csharp
// Service class which implements the service contract.
// Added code to write output to the console window.
public class OrderProcessorService : IOrderProcessor
{
    private string GetCallerIdentity()
    {
        // The client certificate is not mapped to a Windows identity by default.
        // ServiceSecurityContext.PrimaryIdentity is populated based on the information
        // in the certificate that the client used to authenticate itself to the service.
        return ServiceSecurityContext.Current.PrimaryIdentity.Name;
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Console.WriteLine("Client's Identity {0} ", GetCallerIdentity());
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
    }
  //…
}
```

 <span data-ttu-id="6237c-178">執行時，服務程式碼會顯示用戶端識別。</span><span class="sxs-lookup"><span data-stu-id="6237c-178">When run, the service code displays the client identification.</span></span> <span data-ttu-id="6237c-179">下列是服務程式碼的範例輸出：</span><span class="sxs-lookup"><span data-stu-id="6237c-179">The following is a sample output from the service code:</span></span>

```
The service is ready.
Press <ENTER> to terminate service.

Client's Identity CN=client.com; ECA6629A3C695D01832D77EEE836E04891DE9D3C
Processing Purchase Order: 6536e097-da96-4773-9da3-77bab4345b5d
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

## <a name="comments"></a><span data-ttu-id="6237c-180">註解</span><span class="sxs-lookup"><span data-stu-id="6237c-180">Comments</span></span>

- <span data-ttu-id="6237c-181">建立用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="6237c-181">Creating the client certificate.</span></span>

     <span data-ttu-id="6237c-182">批次檔中的下列程式行會建立用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="6237c-182">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="6237c-183">在所建立之憑證主體的名稱中，會使用指定的用戶端名稱。</span><span class="sxs-lookup"><span data-stu-id="6237c-183">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="6237c-184">憑證會儲存在位於 `My` 存放區的 `CurrentUser` 存放區中。</span><span class="sxs-lookup"><span data-stu-id="6237c-184">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="6237c-185">將用戶端憑證安裝至伺服器的受信任憑證存放區中。</span><span class="sxs-lookup"><span data-stu-id="6237c-185">Installing the client certificate into server’s trusted certificate store.</span></span>

     <span data-ttu-id="6237c-186">批次檔中的下列程式行會將用戶端憑證複製到伺服器的 TrustedPeople 存放區，讓伺服器可以做出相關的信任或不信任決定。</span><span class="sxs-lookup"><span data-stu-id="6237c-186">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="6237c-187">安裝在 TrustedPeople 存放區受到 Windows Communication Foundation (WCF) 服務所信任的憑證，用戶端憑證驗證模式必須設定為`PeerOrChainTrust`或`PeerTrust`值。</span><span class="sxs-lookup"><span data-stu-id="6237c-187">For a certificate installed in the TrustedPeople store to be trusted by a Windows Communication Foundation (WCF) service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust` value.</span></span> <span data-ttu-id="6237c-188">請參閱先前的服務組態範例，以了解如何使用組態檔完成這個工作。</span><span class="sxs-lookup"><span data-stu-id="6237c-188">See the previous service configuration sample to learn how this can be done using a configuration file.</span></span>

    ```bat
    echo ************
    echo copying client cert to server's LocalMachine store
    echo ************
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

- <span data-ttu-id="6237c-189">建立伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="6237c-189">Creating the server certificate.</span></span>

     <span data-ttu-id="6237c-190">下列 Setup.bat 批次檔中的程式行會建立要使用的伺服器憑證：</span><span class="sxs-lookup"><span data-stu-id="6237c-190">The following lines from the Setup.bat batch file create the server certificate to be used:</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     <span data-ttu-id="6237c-191">%SERVER_NAME% 變數會指定伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="6237c-191">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="6237c-192">憑證是儲存在 LocalMachine 存放區中。</span><span class="sxs-lookup"><span data-stu-id="6237c-192">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="6237c-193">如果使用 service 引數執行安裝批次檔 (例如`setup.bat service`) %server_name%就會包含電腦完整網域名稱。否則，預設為 localhost</span><span class="sxs-lookup"><span data-stu-id="6237c-193">If the setup batch file is run with an argument of service (such as, `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.Otherwise it defaults to localhost</span></span>

- <span data-ttu-id="6237c-194">將伺服器憑證安裝到用戶端的受信任憑證存放區中。</span><span class="sxs-lookup"><span data-stu-id="6237c-194">Installing server certificate into the client’s trusted certificate store.</span></span>

     <span data-ttu-id="6237c-195">下列程式行會將伺服器憑證複製到用戶端受信任人的存放區中。</span><span class="sxs-lookup"><span data-stu-id="6237c-195">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="6237c-196">這是必要步驟，因為用戶端系統並未隱含信任 Makecert.exe 產生的憑證。</span><span class="sxs-lookup"><span data-stu-id="6237c-196">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="6237c-197">如果您已經有一個以用戶端信任的根憑證 (例如 Microsoft 所發行的憑證) 為基礎的憑證，就不需要這個將伺服器憑證填入用戶端憑證的步驟。</span><span class="sxs-lookup"><span data-stu-id="6237c-197">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    >  <span data-ttu-id="6237c-198">如果您使用的是非美式英文版的 Microsoft Windows，就必須編輯 Setup.bat 檔案，並以適用您所在地區的對等帳戶來取代 "NT AUTHORITY\NETWORK SERVICE" 帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="6237c-198">If you are using a non-U.S. English edition of Microsoft Windows you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="6237c-199">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="6237c-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="6237c-200">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="6237c-200">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6237c-201">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="6237c-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6237c-202">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="6237c-202">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
