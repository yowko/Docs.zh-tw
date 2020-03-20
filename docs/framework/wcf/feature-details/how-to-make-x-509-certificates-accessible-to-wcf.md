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
ms.openlocfilehash: 14f2242ab55795c74fa169382fef846bc0e60ace
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184901"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="048f2-102">HOW TO：讓 WCF 能夠存取 X.509 憑證</span><span class="sxs-lookup"><span data-stu-id="048f2-102">How to: Make X.509 Certificates Accessible to WCF</span></span>
<span data-ttu-id="048f2-103">要使 X.509 憑證可供 Windows 通信基礎 （WCF） 訪問，應用程式代碼必須指定憑證存放區名稱和位置。</span><span class="sxs-lookup"><span data-stu-id="048f2-103">To make an X.509 certificate accessible to Windows Communication Foundation (WCF), application code must specify the certificate store name and location.</span></span> <span data-ttu-id="048f2-104">在某些狀況下，處理序身分識別必須能夠存取包含與 X.509 憑證相關聯之私密金鑰的檔案。</span><span class="sxs-lookup"><span data-stu-id="048f2-104">In certain circumstances, the process identity must have access to the file that contains the private key associated with the X.509 certificate.</span></span> <span data-ttu-id="048f2-105">要獲取憑證存放區中與 X.509 憑證關聯的私密金鑰，WCF 必須具有執行此操作的許可權。</span><span class="sxs-lookup"><span data-stu-id="048f2-105">To obtain the private key associated with an X.509 certificate in a certificate store, WCF must have permission to do so.</span></span> <span data-ttu-id="048f2-106">根據預設，只有擁有人和系統帳戶能夠存取憑證的私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="048f2-106">By default, only the owner and the System account can access the private key of a certificate.</span></span>  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="048f2-107">讓 WCF 能夠存取 X.509 憑證</span><span class="sxs-lookup"><span data-stu-id="048f2-107">To make X.509 certificates accessible to WCF</span></span>  
  
1. <span data-ttu-id="048f2-108">向 WCF 運行對包含與 X.509 憑證關聯的私密金鑰的檔的讀取存取許可權的帳戶。</span><span class="sxs-lookup"><span data-stu-id="048f2-108">Give the account under which WCF is running read access to the file that contains the private key associated with the X.509 certificate.</span></span>  
  
    1. <span data-ttu-id="048f2-109">確定 WCF 是否需要對 X.509 憑證的私密金鑰進行讀取存取。</span><span class="sxs-lookup"><span data-stu-id="048f2-109">Determine whether WCF requires read access to the private key for the X.509 certificate.</span></span>  
  
         <span data-ttu-id="048f2-110">下表詳細列出在使用 X.509 憑證時是否必須要提供私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="048f2-110">The following table details whether a private key must be available when using an X.509 certificate.</span></span>  
  
        |<span data-ttu-id="048f2-111">X.509 憑證使用方式</span><span class="sxs-lookup"><span data-stu-id="048f2-111">X.509 certificate use</span></span>|<span data-ttu-id="048f2-112">私密金鑰</span><span class="sxs-lookup"><span data-stu-id="048f2-112">Private key</span></span>|  
        |---------------------------|-----------------|  
        |<span data-ttu-id="048f2-113">數位簽署傳出的 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="048f2-113">Digitally signing an outbound SOAP message.</span></span>|<span data-ttu-id="048f2-114">是</span><span class="sxs-lookup"><span data-stu-id="048f2-114">Yes</span></span>|  
        |<span data-ttu-id="048f2-115">確認傳入之 SOAP 訊息的簽章。</span><span class="sxs-lookup"><span data-stu-id="048f2-115">Verifying the signature of an inbound SOAP message.</span></span>|<span data-ttu-id="048f2-116">否</span><span class="sxs-lookup"><span data-stu-id="048f2-116">No</span></span>|  
        |<span data-ttu-id="048f2-117">加密傳出的 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="048f2-117">Encrypting an outbound SOAP message.</span></span>|<span data-ttu-id="048f2-118">否</span><span class="sxs-lookup"><span data-stu-id="048f2-118">No</span></span>|  
        |<span data-ttu-id="048f2-119">解密傳入的 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="048f2-119">Decrypting an inbound SOAP message.</span></span>|<span data-ttu-id="048f2-120">是</span><span class="sxs-lookup"><span data-stu-id="048f2-120">Yes</span></span>|  
  
    2. <span data-ttu-id="048f2-121">判斷憑證存放於其中的憑證存放區位置和名稱。</span><span class="sxs-lookup"><span data-stu-id="048f2-121">Determine the certificate store location and name in which the certificate is stored.</span></span>  
  
         <span data-ttu-id="048f2-122">憑證存放於其中的憑證存放區會指定於應用程式程式碼或組態中。</span><span class="sxs-lookup"><span data-stu-id="048f2-122">The certificate store in which the certificate is stored is specified either in application code or in configuration.</span></span> <span data-ttu-id="048f2-123">例如，下列範例會指定憑證是位於名為 `CurrentUser` 的 `My` 憑證存放區中。</span><span class="sxs-lookup"><span data-stu-id="048f2-123">For example, the following example specifies that the certificate is located in the `CurrentUser` certificate store named `My`.</span></span>  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3. <span data-ttu-id="048f2-124">使用[FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)工具確定證書的私密金鑰位於電腦上的位置。</span><span class="sxs-lookup"><span data-stu-id="048f2-124">Determine where the private key for the certificate is located on the computer by using the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool.</span></span>  
  
         <span data-ttu-id="048f2-125">[FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)工具需要憑證存放區名稱、憑證存放區位置以及唯一標識證書的內容。</span><span class="sxs-lookup"><span data-stu-id="048f2-125">The [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool requires the certificate store name, certificate store location, and something that uniquely identifies the certificate.</span></span> <span data-ttu-id="048f2-126">此工具會接受憑證的主體名稱或是其指紋來做為唯一識別項。</span><span class="sxs-lookup"><span data-stu-id="048f2-126">The tool accepts either the certificate's subject name or its thumbprint as a unique identifier.</span></span> <span data-ttu-id="048f2-127">有關如何確定證書的指紋的詳細資訊，請參閱[如何：檢索證書的指紋](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)。</span><span class="sxs-lookup"><span data-stu-id="048f2-127">For more information about how to determine the thumbprint for a certificate, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
         <span data-ttu-id="048f2-128">以下代碼示例使用[FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)工具確定`My``CurrentUser`存儲中的證書的私密金鑰的位置，並帶有 的`46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`指紋。</span><span class="sxs-lookup"><span data-stu-id="048f2-128">The following code example uses the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool to determine the location of the private key for a certificate in the `My` store in `CurrentUser` with a thumbprint of `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span></span>  
  
        ```console
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4. <span data-ttu-id="048f2-129">確定 WCF 正在運行的帳戶。</span><span class="sxs-lookup"><span data-stu-id="048f2-129">Determine the account that WCF is running under.</span></span>  
  
         <span data-ttu-id="048f2-130">下表詳細介紹了為給定方案運行 WCF 的帳戶。</span><span class="sxs-lookup"><span data-stu-id="048f2-130">The following table details the account under which WCF is running for a given scenario.</span></span>  
  
        |<span data-ttu-id="048f2-131">狀況</span><span class="sxs-lookup"><span data-stu-id="048f2-131">Scenario</span></span>|<span data-ttu-id="048f2-132">處理序身分識別</span><span class="sxs-lookup"><span data-stu-id="048f2-132">Process identity</span></span>|  
        |--------------|----------------------|  
        |<span data-ttu-id="048f2-133">用戶端 (主控台或 WinForms 應用程式)。</span><span class="sxs-lookup"><span data-stu-id="048f2-133">Client (console or WinForms application).</span></span>|<span data-ttu-id="048f2-134">目前登入的使用者。</span><span class="sxs-lookup"><span data-stu-id="048f2-134">Currently logged in user.</span></span>|  
        |<span data-ttu-id="048f2-135">自我裝載的服務。</span><span class="sxs-lookup"><span data-stu-id="048f2-135">Service that is self-hosted.</span></span>|<span data-ttu-id="048f2-136">目前登入的使用者。</span><span class="sxs-lookup"><span data-stu-id="048f2-136">Currently logged in user.</span></span>|  
        |<span data-ttu-id="048f2-137">託管在 IIS 6.0（Windows 伺服器 2003）或 IIS 7.0（Windows Vista）中的服務。</span><span class="sxs-lookup"><span data-stu-id="048f2-137">Service that is hosted in IIS 6.0 (Windows Server 2003) or IIS 7.0 (Windows Vista).</span></span>|<span data-ttu-id="048f2-138">NETWORK SERVICE</span><span class="sxs-lookup"><span data-stu-id="048f2-138">NETWORK SERVICE</span></span>|  
        |<span data-ttu-id="048f2-139">在 IIS 5.X （Windows XP） 中託管的服務。</span><span class="sxs-lookup"><span data-stu-id="048f2-139">Service that is hosted in IIS 5.X (Windows XP).</span></span>|<span data-ttu-id="048f2-140">由 Machine.config 檔中的 `<processModel>` 項目控制。</span><span class="sxs-lookup"><span data-stu-id="048f2-140">Controlled by the `<processModel>` element in the Machine.config file.</span></span> <span data-ttu-id="048f2-141">預設帳戶是 ASPNET。</span><span class="sxs-lookup"><span data-stu-id="048f2-141">The default account is ASPNET.</span></span>|  
  
    5. <span data-ttu-id="048f2-142">使用 icacls.exe 等工具授予對包含 WCF 運行帳戶的私密金鑰的檔的讀取存取許可權。</span><span class="sxs-lookup"><span data-stu-id="048f2-142">Grant read access to the file that contains the private key to the account that WCF is running under, using a tool such as icacls.exe.</span></span>  
  
         <span data-ttu-id="048f2-143">以下代碼示例編輯指定檔的可自由存取控制清單 （DACL）， 以授予網路服務帳戶對該檔的讀取 （：R） 存取權限。</span><span class="sxs-lookup"><span data-stu-id="048f2-143">The following code example edits the discretionary access control list (DACL) for the specified file to grant the NETWORK SERVICE account read (:R) access to the file.</span></span>  
  
        ```console
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="048f2-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="048f2-144">See also</span></span>

- [<span data-ttu-id="048f2-145">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="048f2-145">FindPrivateKey</span></span>](../../../../docs/framework/wcf/samples/findprivatekey.md)
- [<span data-ttu-id="048f2-146">HOW TO：擷取憑證的指紋</span><span class="sxs-lookup"><span data-stu-id="048f2-146">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [<span data-ttu-id="048f2-147">Working with Certificates</span><span class="sxs-lookup"><span data-stu-id="048f2-147">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
