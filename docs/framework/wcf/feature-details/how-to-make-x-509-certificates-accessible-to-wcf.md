---
title: HOW TO：讓 WCF 能夠存取 X.509 憑證
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
ms.openlocfilehash: 7c90d5b0541edfc11145d9373c2554ee4595a7b1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741873"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="b4e78-102">HOW TO：讓 WCF 能夠存取 X.509 憑證</span><span class="sxs-lookup"><span data-stu-id="b4e78-102">How to: Make X.509 Certificates Accessible to WCF</span></span>
<span data-ttu-id="b4e78-103">若要存取以 Windows Communication Foundation (WCF) 的 X.509 憑證，請的憑證存放區名稱和位置，必須指定應用程式程式碼。</span><span class="sxs-lookup"><span data-stu-id="b4e78-103">To make an X.509 certificate accessible to Windows Communication Foundation (WCF), application code must specify the certificate store name and location.</span></span> <span data-ttu-id="b4e78-104">在某些狀況下，處理序身分識別必須能夠存取包含與 X.509 憑證相關聯之私密金鑰的檔案。</span><span class="sxs-lookup"><span data-stu-id="b4e78-104">In certain circumstances, the process identity must have access to the file that contains the private key associated with the X.509 certificate.</span></span> <span data-ttu-id="b4e78-105">若要取得相關聯的憑證存放區中 X.509 憑證的私密金鑰，WCF 必須進行此作業的權限。</span><span class="sxs-lookup"><span data-stu-id="b4e78-105">To obtain the private key associated with an X.509 certificate in a certificate store, WCF must have permission to do so.</span></span> <span data-ttu-id="b4e78-106">根據預設，只有擁有人和系統帳戶能夠存取憑證的私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="b4e78-106">By default, only the owner and the System account can access the private key of a certificate.</span></span>  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="b4e78-107">讓 WCF 能夠存取 X.509 憑證</span><span class="sxs-lookup"><span data-stu-id="b4e78-107">To make X.509 certificates accessible to WCF</span></span>  
  
1.  <span data-ttu-id="b4e78-108">授與 WCF 執行的讀取權限，其中包含與 X.509 憑證相關聯的私密金鑰檔案的帳戶。</span><span class="sxs-lookup"><span data-stu-id="b4e78-108">Give the account under which WCF is running read access to the file that contains the private key associated with the X.509 certificate.</span></span>  
  
    1.  <span data-ttu-id="b4e78-109">判斷 WCF 是否需要 X.509 憑證的私用金鑰的 「 讀取 」 權限。</span><span class="sxs-lookup"><span data-stu-id="b4e78-109">Determine whether WCF requires read access to the private key for the X.509 certificate.</span></span>  
  
         <span data-ttu-id="b4e78-110">下表詳細列出在使用 X.509 憑證時是否必須要提供私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="b4e78-110">The following table details whether a private key must be available when using an X.509 certificate.</span></span>  
  
        |<span data-ttu-id="b4e78-111">X.509 憑證使用方式</span><span class="sxs-lookup"><span data-stu-id="b4e78-111">X.509 certificate use</span></span>|<span data-ttu-id="b4e78-112">私密金鑰</span><span class="sxs-lookup"><span data-stu-id="b4e78-112">Private key</span></span>|  
        |---------------------------|-----------------|  
        |<span data-ttu-id="b4e78-113">數位簽署傳出的 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="b4e78-113">Digitally signing an outbound SOAP message.</span></span>|<span data-ttu-id="b4e78-114">是</span><span class="sxs-lookup"><span data-stu-id="b4e78-114">Yes</span></span>|  
        |<span data-ttu-id="b4e78-115">確認傳入之 SOAP 訊息的簽章。</span><span class="sxs-lookup"><span data-stu-id="b4e78-115">Verifying the signature of an inbound SOAP message.</span></span>|<span data-ttu-id="b4e78-116">否</span><span class="sxs-lookup"><span data-stu-id="b4e78-116">No</span></span>|  
        |<span data-ttu-id="b4e78-117">加密傳出的 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="b4e78-117">Encrypting an outbound SOAP message.</span></span>|<span data-ttu-id="b4e78-118">否</span><span class="sxs-lookup"><span data-stu-id="b4e78-118">No</span></span>|  
        |<span data-ttu-id="b4e78-119">解密傳入的 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="b4e78-119">Decrypting an inbound SOAP message.</span></span>|<span data-ttu-id="b4e78-120">是</span><span class="sxs-lookup"><span data-stu-id="b4e78-120">Yes</span></span>|  
  
    2.  <span data-ttu-id="b4e78-121">判斷憑證存放於其中的憑證存放區位置和名稱。</span><span class="sxs-lookup"><span data-stu-id="b4e78-121">Determine the certificate store location and name in which the certificate is stored.</span></span>  
  
         <span data-ttu-id="b4e78-122">憑證存放於其中的憑證存放區會指定於應用程式程式碼或組態中。</span><span class="sxs-lookup"><span data-stu-id="b4e78-122">The certificate store in which the certificate is stored is specified either in application code or in configuration.</span></span> <span data-ttu-id="b4e78-123">例如，下列範例會指定憑證是位於名為 `CurrentUser` 的 `My` 憑證存放區中。</span><span class="sxs-lookup"><span data-stu-id="b4e78-123">For example, the following example specifies that the certificate is located in the `CurrentUser` certificate store named `My`.</span></span>  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3.  <span data-ttu-id="b4e78-124">判斷憑證的私用金鑰所在的電腦上使用[FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)工具。</span><span class="sxs-lookup"><span data-stu-id="b4e78-124">Determine where the private key for the certificate is located on the computer by using the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool.</span></span>  
  
         <span data-ttu-id="b4e78-125">[FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)工具需要憑證存放區名稱、 憑證存放區位置，以及可以唯一識別該憑證。</span><span class="sxs-lookup"><span data-stu-id="b4e78-125">The [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool requires the certificate store name, certificate store location, and something that uniquely identifies the certificate.</span></span> <span data-ttu-id="b4e78-126">此工具會接受憑證的主體名稱或是其指紋來做為唯一識別項。</span><span class="sxs-lookup"><span data-stu-id="b4e78-126">The tool accepts either the certificate's subject name or its thumbprint as a unique identifier.</span></span> <span data-ttu-id="b4e78-127">如需如何判斷憑證指紋的詳細資訊，請參閱[How to:擷取憑證的指紋](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)。</span><span class="sxs-lookup"><span data-stu-id="b4e78-127">For more information about how to determine the thumbprint for a certificate, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
         <span data-ttu-id="b4e78-128">下列程式碼範例會使用[FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)工具來判斷的位置中的憑證的私密金鑰`My`存放`CurrentUser`指紋`46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`。</span><span class="sxs-lookup"><span data-stu-id="b4e78-128">The following code example uses the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool to determine the location of the private key for a certificate in the `My` store in `CurrentUser` with a thumbprint of `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span></span>  
  
        ```  
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4.  <span data-ttu-id="b4e78-129">判斷執行 WCF 的帳戶。</span><span class="sxs-lookup"><span data-stu-id="b4e78-129">Determine the account that WCF is running under.</span></span>  
  
         <span data-ttu-id="b4e78-130">下表詳細說明 WCF 執行指定之案例的帳戶。</span><span class="sxs-lookup"><span data-stu-id="b4e78-130">The following table details the account under which WCF is running for a given scenario.</span></span>  
  
        |<span data-ttu-id="b4e78-131">情節</span><span class="sxs-lookup"><span data-stu-id="b4e78-131">Scenario</span></span>|<span data-ttu-id="b4e78-132">處理序身分識別</span><span class="sxs-lookup"><span data-stu-id="b4e78-132">Process identity</span></span>|  
        |--------------|----------------------|  
        |<span data-ttu-id="b4e78-133">用戶端 (主控台或 WinForms 應用程式)。</span><span class="sxs-lookup"><span data-stu-id="b4e78-133">Client (console or WinForms application).</span></span>|<span data-ttu-id="b4e78-134">目前登入的使用者。</span><span class="sxs-lookup"><span data-stu-id="b4e78-134">Currently logged in user.</span></span>|  
        |<span data-ttu-id="b4e78-135">自我裝載的服務。</span><span class="sxs-lookup"><span data-stu-id="b4e78-135">Service that is self-hosted.</span></span>|<span data-ttu-id="b4e78-136">目前登入的使用者。</span><span class="sxs-lookup"><span data-stu-id="b4e78-136">Currently logged in user.</span></span>|  
        |<span data-ttu-id="b4e78-137">裝載於 IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) 或 IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]) 中的服務。</span><span class="sxs-lookup"><span data-stu-id="b4e78-137">Service that is hosted in IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) or IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).</span></span>|<span data-ttu-id="b4e78-138">網路服務</span><span class="sxs-lookup"><span data-stu-id="b4e78-138">NETWORK SERVICE</span></span>|  
        |<span data-ttu-id="b4e78-139">裝載於 IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]) 中的服務。</span><span class="sxs-lookup"><span data-stu-id="b4e78-139">Service that is hosted in IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).</span></span>|<span data-ttu-id="b4e78-140">由 Machine.config 檔中的 `<processModel>` 項目控制。</span><span class="sxs-lookup"><span data-stu-id="b4e78-140">Controlled by the `<processModel>` element in the Machine.config file.</span></span> <span data-ttu-id="b4e78-141">預設帳戶是 ASPNET。</span><span class="sxs-lookup"><span data-stu-id="b4e78-141">The default account is ASPNET.</span></span>|  
  
    5.  <span data-ttu-id="b4e78-142">授與讀取檔案，其中包含私密金鑰，以 WCF 在其下執行使用 icacls.exe 之類的工具的帳戶。</span><span class="sxs-lookup"><span data-stu-id="b4e78-142">Grant read access to the file that contains the private key to the account that WCF is running under, using a tool such as icacls.exe.</span></span>  
  
         <span data-ttu-id="b4e78-143">下列程式碼範例會編輯判別存取控制清單 (DACL) 授與 NETWORK SERVICE 帳戶讀取指定的檔案 (: R) 檔案的存取權。</span><span class="sxs-lookup"><span data-stu-id="b4e78-143">The following code example edits the discretionary access control list (DACL) for the specified file to grant the NETWORK SERVICE account read (:R) access to the file.</span></span>  
  
        ```  
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="b4e78-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4e78-144">See also</span></span>
- [<span data-ttu-id="b4e78-145">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="b4e78-145">FindPrivateKey</span></span>](../../../../docs/framework/wcf/samples/findprivatekey.md)
- [<span data-ttu-id="b4e78-146">如何：擷取憑證的指紋</span><span class="sxs-lookup"><span data-stu-id="b4e78-146">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [<span data-ttu-id="b4e78-147">使用憑證</span><span class="sxs-lookup"><span data-stu-id="b4e78-147">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
