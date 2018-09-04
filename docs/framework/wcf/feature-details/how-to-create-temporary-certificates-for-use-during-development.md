---
title: HOW TO：建立開發時要使用的暫時憑證
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: d3b051c7ea152606721388ea35b6f508eada1c5d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524361"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a><span data-ttu-id="6e2aa-102">HOW TO：建立開發時要使用的暫時憑證</span><span class="sxs-lookup"><span data-stu-id="6e2aa-102">How to: Create Temporary Certificates for Use During Development</span></span>
<span data-ttu-id="6e2aa-103">開發安全的服務或使用 Windows Communication Foundation (WCF) 用戶端時，通常必須提供要用做為認證的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-103">When developing a secure service or client using Windows Communication Foundation (WCF), it is often necessary to supply an X.509 certificate to be used as a credential.</span></span> <span data-ttu-id="6e2aa-104">憑證通常是憑證鏈結的一部分，在電腦的 [受信任的根憑證授權單位] 存放區中有根授權。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-104">The certificate typically is part of a chain of certificates with a root authority found in the Trusted Root Certification Authorities store of the computer.</span></span> <span data-ttu-id="6e2aa-105">具有憑證鏈結可讓您設定一組憑證的範圍，其中根授權通常來自您的組織或企業單位。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-105">Having a certificate chain enables you to scope a set of certificates where typically the root authority is from your organization or business unit.</span></span> <span data-ttu-id="6e2aa-106">如果要在開發期間進行模擬，您可以建立兩種憑證以滿足安全性需求。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-106">To emulate this at development time, you can create two certificates to satisfy the security requirements.</span></span> <span data-ttu-id="6e2aa-107">第一種是放在 [受信任的根憑證授權單位] 存放區中的自我簽署憑證，而第二種憑證是從第一種建立的，並放在個人存放區或本機位置，或目前使用者位置的個人存放區。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-107">The first is a self-signed certificate that is placed in the Trusted Root Certification Authorities store, and the second certificate is created from the first and is placed in either the Personal store of the Local Machine location, or the Personal store of the Current User location.</span></span> <span data-ttu-id="6e2aa-108">本主題逐步解說建立使用這兩種憑證的步驟[憑證建立工具 (MakeCert.exe)](https://go.microsoft.com/fwlink/?LinkId=248185)，這由提供[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]SDK。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-108">This topic walks through the steps to create these two certificates using the [Certificate Creation Tool (MakeCert.exe)](https://go.microsoft.com/fwlink/?LinkId=248185), which is provided by the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SDK.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6e2aa-109">憑證建立工具所產生的憑證僅針對測試用途提供。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-109">The certificates the Certification Creation tool generates are provided for testing purposes only.</span></span> <span data-ttu-id="6e2aa-110">當部署服務或用戶端時，請確定使用由憑證授權單位所提供的適當憑證。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-110">When deploying a service or client, be sure to use an appropriate certificate provided by a certification authority.</span></span> <span data-ttu-id="6e2aa-111">這可能是來自您組織中的 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 憑證伺服器或協力廠商。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-111">This could either be from a [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] certificate server in your organization or a third party.</span></span>  
>   
>  <span data-ttu-id="6e2aa-112">根據預設， [Makecert.exe （憑證建立工具）](https://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)會建立的憑證的根授權稱為 「 根代理者 **。 」**</span><span class="sxs-lookup"><span data-stu-id="6e2aa-112">By default, the [Makecert.exe (Certificate Creation Tool)](https://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d) creates certificates whose root authority is called "Root Agency **."**</span></span> <span data-ttu-id="6e2aa-113">由於「根代理者」不是在 [受信任的根憑證授權單位] 存放區中，因此會讓這些憑證變得不安全。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-113">Because the "Root Agency" is not in the Trusted Root Certification Authorities store, this makes these certificates insecure.</span></span> <span data-ttu-id="6e2aa-114">建立位於 [受信任的根憑證授權單位] 存放區中的自我簽署憑證，可讓您建立一個更能夠模擬您開發環境的開發環境。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-114">Creating a self-signed certificate that is placed in the Trusted Root Certification Authorities store enables you to create a development environment that more closely simulates your deployment environment.</span></span>  
  
 <span data-ttu-id="6e2aa-115">如需有關建立及使用憑證的詳細資訊，請參閱 < [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-115">For more information about creating and using certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="6e2aa-116">如需使用憑證做為認證的詳細資訊，請參閱[Securing Services and Clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-116">For more information about using a certificate as a credential, see [Securing Services and Clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span></span> <span data-ttu-id="6e2aa-117">如需有關使用 Microsoft Authenticode 技術的教學課程，請參閱 < [Authenticode 概觀與教學課程](https://go.microsoft.com/fwlink/?LinkId=88919)。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-117">For a tutorial about using Microsoft Authenticode technology, see [Authenticode Overviews and Tutorials](https://go.microsoft.com/fwlink/?LinkId=88919).</span></span>  
  
### <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a><span data-ttu-id="6e2aa-118">建立自我簽署根授權憑證及匯出私密金鑰</span><span class="sxs-lookup"><span data-stu-id="6e2aa-118">To create a self-signed root authority certificate and export the private key</span></span>  
  
1.  <span data-ttu-id="6e2aa-119">請使用 MakeCert.exe 工具搭配下列參數：</span><span class="sxs-lookup"><span data-stu-id="6e2aa-119">Use the MakeCert.exe tool with the following switches:</span></span>  
  
    1.  <span data-ttu-id="6e2aa-120">`-n` `subjectName`。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-120">`-n` `subjectName`.</span></span> <span data-ttu-id="6e2aa-121">指定主體名稱。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-121">Specifies the subject name.</span></span> <span data-ttu-id="6e2aa-122">慣例是使用 "CN = " 做為主體名稱的前置詞，代表「一般名稱」。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-122">The convention is to prefix the subject name with "CN = " for "Common Name".</span></span>  
  
    2.  <span data-ttu-id="6e2aa-123">`-r`.</span><span class="sxs-lookup"><span data-stu-id="6e2aa-123">`-r`.</span></span> <span data-ttu-id="6e2aa-124">指定憑證為自我簽署的。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-124">Specifies that the certificate will be self-signed.</span></span>  
  
    3.  <span data-ttu-id="6e2aa-125">`-sv` `privateKeyFile`.</span><span class="sxs-lookup"><span data-stu-id="6e2aa-125">`-sv` `privateKeyFile`.</span></span> <span data-ttu-id="6e2aa-126">指定含有私密金鑰容器的檔案。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-126">Specifies the file that contains the private key container.</span></span>  
  
     <span data-ttu-id="6e2aa-127">例如，下列命令會建立主體名稱為 "CN=TempCA" 的自我簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-127">For example, the following command creates a self-signed certificate with a subject name of "CN=TempCA."</span></span>  
  
    ```  
    makecert -n "CN=TempCA" -r -sv TempCA.pvk TempCA.cer  
    ```  
  
     <span data-ttu-id="6e2aa-128">您會收到提供密碼以保護私密金鑰的提示。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-128">You will be prompted to provide a password to protect the private key.</span></span> <span data-ttu-id="6e2aa-129">當建立由這個根憑證簽署的憑證時，需要這個密碼。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-129">This password is required when creating a certificate signed by this root certificate.</span></span>  
  
### <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a><span data-ttu-id="6e2aa-130">建立由根授權憑證簽署的新憑證</span><span class="sxs-lookup"><span data-stu-id="6e2aa-130">To create a new certificate signed by a root authority certificate</span></span>  
  
1.  <span data-ttu-id="6e2aa-131">請使用 MakeCert.exe 工具搭配下列參數：</span><span class="sxs-lookup"><span data-stu-id="6e2aa-131">Use the MakeCert.exe tool with the following switches:</span></span>  
  
    1.  <span data-ttu-id="6e2aa-132">`-sk` `subjectKey`.</span><span class="sxs-lookup"><span data-stu-id="6e2aa-132">`-sk` `subjectKey`.</span></span> <span data-ttu-id="6e2aa-133">主體的金鑰容器的位置，其中包含私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-133">The location of the subject's key container that holds the private key.</span></span> <span data-ttu-id="6e2aa-134">如果金鑰容器不存在，便會建立一個。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-134">If a key container does not exist, one is created.</span></span> <span data-ttu-id="6e2aa-135">如果 -sk 和 -sv 選項均未使用，根據預設，便會建立稱為 JoeSoft 的金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-135">If neither of the -sk or -sv options is used, a key container called JoeSoft is created by default.</span></span>  
  
    2.  <span data-ttu-id="6e2aa-136">`-n` `subjectName`.</span><span class="sxs-lookup"><span data-stu-id="6e2aa-136">`-n` `subjectName`.</span></span> <span data-ttu-id="6e2aa-137">指定主體名稱。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-137">Specifies the subject name.</span></span> <span data-ttu-id="6e2aa-138">慣例是使用 "CN = " 做為主體名稱的前置詞，代表「一般名稱」。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-138">The convention is to prefix the subject name with "CN = " for "Common Name".</span></span>  
  
    3.  <span data-ttu-id="6e2aa-139">`-iv` `issuerKeyFile`.</span><span class="sxs-lookup"><span data-stu-id="6e2aa-139">`-iv` `issuerKeyFile`.</span></span> <span data-ttu-id="6e2aa-140">指定簽發者的私密金鑰檔。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-140">Specifies the issuer's private key file.</span></span>  
  
    4.  <span data-ttu-id="6e2aa-141">`-ic` `issuerCertFile`.</span><span class="sxs-lookup"><span data-stu-id="6e2aa-141">`-ic` `issuerCertFile`.</span></span> <span data-ttu-id="6e2aa-142">指定簽發者的憑證的位置。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-142">Specifies the location of the issuer's certificate.</span></span>  
  
     <span data-ttu-id="6e2aa-143">例如，下列命令會使用簽發者的私密金鑰，建立由主體名稱為 `TempCA` 的 `"CN=SignedByCA"` 根授權憑證簽署的憑證。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-143">For example, the following command creates a certificate signed by the `TempCA` root authority certificate with a subject name of `"CN=SignedByCA"` using the private key of the issuer.</span></span>  
  
    ```  
    makecert -sk SignedByCA -iv TempCA.pvk -n "CN=SignedByCA" -ic TempCA.cer SignedByCA.cer -sr currentuser -ss My  
    ```  
  
## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a><span data-ttu-id="6e2aa-144">在受信任的根憑證授權單位存放區中安裝憑證</span><span class="sxs-lookup"><span data-stu-id="6e2aa-144">Installing a Certificate in the Trusted Root Certification Authorities Store</span></span>  
 <span data-ttu-id="6e2aa-145">在建立自我簽署憑證之後，您就可以將它安裝在 [受信任的根憑證授權單位] 存放區中。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-145">Once a self-signed certificate is created, you can install it in the Trusted Root Certification Authorities store.</span></span> <span data-ttu-id="6e2aa-146">此時任何使用憑證簽署的憑證都受到電腦的信任。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-146">Any certificates that are signed with the certificate at this point are trusted by the computer.</span></span> <span data-ttu-id="6e2aa-147">因此，當您不再需要憑證時，請立刻從存放區中將其刪除。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-147">For this reason, delete the certificate from the store as soon as you no longer need it.</span></span> <span data-ttu-id="6e2aa-148">當您刪除這個根授權憑證時，使用該憑證簽署的所有其他憑證都會變成未經授權的。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-148">When you delete this root authority certificate, all other certificates that signed with it become unauthorized.</span></span> <span data-ttu-id="6e2aa-149">根授權憑證只是一種機制，可依需要設定一組憑證的範圍。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-149">Root authority certificates are simply a mechanism whereby a group of certificates can be scoped as necessary.</span></span> <span data-ttu-id="6e2aa-150">例如，在對等應用程式中，通常不需要根授權，因為您只是藉由個體提供的憑證而信任其身分識別。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-150">For example, in peer-to-peer applications, there is typically no need for a root authority because you simply trust the identity of an individual by its supplied certificate.</span></span>  
  
#### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a><span data-ttu-id="6e2aa-151">在受信任的根憑證授權單位中安裝自我簽署憑證</span><span class="sxs-lookup"><span data-stu-id="6e2aa-151">To install a self-signed certificate in the Trusted Root Certification Authorities</span></span>  
  
1.  <span data-ttu-id="6e2aa-152">請開啟憑證嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-152">Open the certificate snap-in.</span></span> <span data-ttu-id="6e2aa-153">如需詳細資訊，請參閱[如何：使用 MMC 嵌入式管理單元來檢視憑證](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-153">For more information, see [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2.  <span data-ttu-id="6e2aa-154">開啟資料夾以儲存憑證，可以是 [ **本機電腦** ] 或 [ **目前使用者**]。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-154">Open the folder to store the certificate, either the **Local Computer** or the **Current User**.</span></span>  
  
3.  <span data-ttu-id="6e2aa-155">開啟 [ **受信任的根憑證授權單位** ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-155">Open the **Trusted Root Certification Authorities** folder.</span></span>  
  
4.  <span data-ttu-id="6e2aa-156">用滑鼠右鍵依序按一下 [ **憑證** ] 資料夾、[ **所有工作**] 和 [ **匯入**]。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-156">Right-click the **Certificates** folder and click **All Tasks**, then click **Import**.</span></span>  
  
5.  <span data-ttu-id="6e2aa-157">請依照螢幕上的精靈指示，將 TempCa.cer 匯入存放區中。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-157">Follow the on-screen wizard instructions to import the TempCa.cer into the store.</span></span>  
  
## <a name="using-certificates-with-wcf"></a><span data-ttu-id="6e2aa-158">搭配 WCF 使用憑證</span><span class="sxs-lookup"><span data-stu-id="6e2aa-158">Using Certificates With WCF</span></span>  
 <span data-ttu-id="6e2aa-159">設定暫時憑證之後，您可以用它來開發可將憑證指定為用戶端認證類型的 WCF 方案。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-159">Once you have set up the temporary certificates, you can use them to develop WCF solutions that specify certificates as a client credential type.</span></span> <span data-ttu-id="6e2aa-160">例如，下列 XML 組態會指定訊息安全性，而且將憑證指定為用戶端認證類型。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-160">For example, the following XML configuration specifies message security and a certificate as the client credential type.</span></span>  
  
#### <a name="to-specify-a-certificate-as-the-client-credential-type"></a><span data-ttu-id="6e2aa-161">若要將憑證指定為用戶端認證類型</span><span class="sxs-lookup"><span data-stu-id="6e2aa-161">To specify a certificate as the client credential type</span></span>  
  
-   <span data-ttu-id="6e2aa-162">在服務的組態檔中，使用下列 XML 將安全性模式設定為訊息，而且將用戶端認證類型設定為憑證。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-162">In the configuration file for a service, use the following XML to set the security mode to message, and the client credential type to certificate.</span></span>  
  
    ```xml  
    <bindings>       
      <wsHttpBinding>  
        <binding name="CertificateForClient">  
          <security>  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    ```  
  
 <span data-ttu-id="6e2aa-163">在用戶端的組態檔，請使用下列 XML 來指定憑證位於使用者的存放區，並且可搜尋在 SubjectName 欄位中的值"CohoWinery"。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-163">In the configuration file for a client, use the following XML to specify that the certificate is found in the user’s store, and can be found by searching the SubjectName field for the value "CohoWinery."</span></span>  
  
```xml  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="CertForClient">  
      <clientCredentials>  
        <clientCertificate findValue="CohoWinery" x509FindType="FindBySubjectName" />  
       </clientCredentials>  
     </behavior>  
   </endpointBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="6e2aa-164">如需在 WCF 中使用憑證的詳細資訊，請參閱 [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-164">For more information about using certificates in WCF, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="6e2aa-165">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="6e2aa-165">.NET Framework Security</span></span>  
 <span data-ttu-id="6e2aa-166">請用滑鼠右鍵按一下憑證，然後按一下 [ **刪除** ]，以確定從 [ **受信任的根憑證授權單位** ] 和 [ **個人**] 資料夾中刪除暫時的根授權憑證。</span><span class="sxs-lookup"><span data-stu-id="6e2aa-166">Be sure to delete any temporary root authority certificates from the **Trusted Root Certification Authorities** and **Personal** folders by right-clicking the certificate, then clicking **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e2aa-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e2aa-167">See Also</span></span>  
 [<span data-ttu-id="6e2aa-168">使用憑證</span><span class="sxs-lookup"><span data-stu-id="6e2aa-168">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="6e2aa-169">如何：使用 MMC 嵌入式管理單元來檢視憑證</span><span class="sxs-lookup"><span data-stu-id="6e2aa-169">How to: View Certificates with the MMC Snap-in</span></span>](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [<span data-ttu-id="6e2aa-170">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="6e2aa-170">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
