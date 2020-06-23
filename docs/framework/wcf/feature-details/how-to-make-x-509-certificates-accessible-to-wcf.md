---
title: HOW TO：讓 WCF 能夠存取 X.509 憑證
description: 瞭解如何讓 WCF 能夠存取 x.509 憑證。 應用程式代碼必須指定憑證存放區名稱和位置。 可能會有其他需求。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
ms.openlocfilehash: 5cc1118640bcf1262d88cb8cdb39939ae315cae3
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246866"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="e6f3e-105">HOW TO：讓 WCF 能夠存取 X.509 憑證</span><span class="sxs-lookup"><span data-stu-id="e6f3e-105">How to: Make X.509 Certificates Accessible to WCF</span></span>
<span data-ttu-id="e6f3e-106">若要讓 Windows Communication Foundation （WCF）可以存取 x.509 憑證，應用程式代碼必須指定憑證存放區名稱和位置。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-106">To make an X.509 certificate accessible to Windows Communication Foundation (WCF), application code must specify the certificate store name and location.</span></span> <span data-ttu-id="e6f3e-107">在某些狀況下，處理序身分識別必須能夠存取包含與 X.509 憑證相關聯之私密金鑰的檔案。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-107">In certain circumstances, the process identity must have access to the file that contains the private key associated with the X.509 certificate.</span></span> <span data-ttu-id="e6f3e-108">若要取得與憑證存放區中的 x.509 憑證相關聯的私密金鑰，WCF 必須擁有執行這項操作的許可權。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-108">To obtain the private key associated with an X.509 certificate in a certificate store, WCF must have permission to do so.</span></span> <span data-ttu-id="e6f3e-109">根據預設，只有擁有人和系統帳戶能夠存取憑證的私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-109">By default, only the owner and the System account can access the private key of a certificate.</span></span>  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="e6f3e-110">讓 WCF 能夠存取 X.509 憑證</span><span class="sxs-lookup"><span data-stu-id="e6f3e-110">To make X.509 certificates accessible to WCF</span></span>  
  
1. <span data-ttu-id="e6f3e-111">授與執行 WCF 所用的帳戶，其中包含與 x.509 憑證相關聯的私密金鑰之檔案的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-111">Give the account under which WCF is running read access to the file that contains the private key associated with the X.509 certificate.</span></span>  
  
    1. <span data-ttu-id="e6f3e-112">判斷 WCF 是否需要 x.509 憑證之私密金鑰的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-112">Determine whether WCF requires read access to the private key for the X.509 certificate.</span></span>  
  
         <span data-ttu-id="e6f3e-113">下表詳細列出在使用 X.509 憑證時是否必須要提供私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-113">The following table details whether a private key must be available when using an X.509 certificate.</span></span>  
  
        |<span data-ttu-id="e6f3e-114">X.509 憑證使用方式</span><span class="sxs-lookup"><span data-stu-id="e6f3e-114">X.509 certificate use</span></span>|<span data-ttu-id="e6f3e-115">私密金鑰</span><span class="sxs-lookup"><span data-stu-id="e6f3e-115">Private key</span></span>|  
        |---------------------------|-----------------|  
        |<span data-ttu-id="e6f3e-116">數位簽署傳出的 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-116">Digitally signing an outbound SOAP message.</span></span>|<span data-ttu-id="e6f3e-117">Yes</span><span class="sxs-lookup"><span data-stu-id="e6f3e-117">Yes</span></span>|  
        |<span data-ttu-id="e6f3e-118">確認傳入之 SOAP 訊息的簽章。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-118">Verifying the signature of an inbound SOAP message.</span></span>|<span data-ttu-id="e6f3e-119">No</span><span class="sxs-lookup"><span data-stu-id="e6f3e-119">No</span></span>|  
        |<span data-ttu-id="e6f3e-120">加密傳出的 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-120">Encrypting an outbound SOAP message.</span></span>|<span data-ttu-id="e6f3e-121">No</span><span class="sxs-lookup"><span data-stu-id="e6f3e-121">No</span></span>|  
        |<span data-ttu-id="e6f3e-122">解密傳入的 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-122">Decrypting an inbound SOAP message.</span></span>|<span data-ttu-id="e6f3e-123">Yes</span><span class="sxs-lookup"><span data-stu-id="e6f3e-123">Yes</span></span>|  
  
    2. <span data-ttu-id="e6f3e-124">判斷憑證存放於其中的憑證存放區位置和名稱。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-124">Determine the certificate store location and name in which the certificate is stored.</span></span>  
  
         <span data-ttu-id="e6f3e-125">憑證存放於其中的憑證存放區會指定於應用程式程式碼或組態中。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-125">The certificate store in which the certificate is stored is specified either in application code or in configuration.</span></span> <span data-ttu-id="e6f3e-126">例如，下列範例會指定憑證是位於名為 `CurrentUser` 的 `My` 憑證存放區中。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-126">For example, the following example specifies that the certificate is located in the `CurrentUser` certificate store named `My`.</span></span>  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3. <span data-ttu-id="e6f3e-127">使用[FindPrivateKey](../samples/findprivatekey.md)工具，判斷憑證的私密金鑰位於電腦上的哪個位置。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-127">Determine where the private key for the certificate is located on the computer by using the [FindPrivateKey](../samples/findprivatekey.md) tool.</span></span>  
  
         <span data-ttu-id="e6f3e-128">[FindPrivateKey](../samples/findprivatekey.md)工具需要憑證存放區名稱、憑證存放區位置，以及可唯一識別憑證的內容。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-128">The [FindPrivateKey](../samples/findprivatekey.md) tool requires the certificate store name, certificate store location, and something that uniquely identifies the certificate.</span></span> <span data-ttu-id="e6f3e-129">此工具會接受憑證的主體名稱或是其指紋來做為唯一識別項。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-129">The tool accepts either the certificate's subject name or its thumbprint as a unique identifier.</span></span> <span data-ttu-id="e6f3e-130">如需如何判斷憑證指紋的詳細資訊，請參閱[如何：取出憑證的指紋](how-to-retrieve-the-thumbprint-of-a-certificate.md)。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-130">For more information about how to determine the thumbprint for a certificate, see [How to: Retrieve the Thumbprint of a Certificate](how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
         <span data-ttu-id="e6f3e-131">下列程式碼範例會使用[FindPrivateKey](../samples/findprivatekey.md)工具，以的指紋，判斷 `My` 存放區中之憑證的私密金鑰位置 `CurrentUser` `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d` 。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-131">The following code example uses the [FindPrivateKey](../samples/findprivatekey.md) tool to determine the location of the private key for a certificate in the `My` store in `CurrentUser` with a thumbprint of `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span></span>  
  
        ```console
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4. <span data-ttu-id="e6f3e-132">判斷正在執行 WCF 的帳戶。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-132">Determine the account that WCF is running under.</span></span>  
  
         <span data-ttu-id="e6f3e-133">下表詳細說明針對指定案例執行 WCF 所使用的帳戶。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-133">The following table details the account under which WCF is running for a given scenario.</span></span>  
  
        |<span data-ttu-id="e6f3e-134">狀況</span><span class="sxs-lookup"><span data-stu-id="e6f3e-134">Scenario</span></span>|<span data-ttu-id="e6f3e-135">處理序身分識別</span><span class="sxs-lookup"><span data-stu-id="e6f3e-135">Process identity</span></span>|  
        |--------------|----------------------|  
        |<span data-ttu-id="e6f3e-136">用戶端 (主控台或 WinForms 應用程式)。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-136">Client (console or WinForms application).</span></span>|<span data-ttu-id="e6f3e-137">目前登入的使用者。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-137">Currently logged in user.</span></span>|  
        |<span data-ttu-id="e6f3e-138">自我裝載的服務。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-138">Service that is self-hosted.</span></span>|<span data-ttu-id="e6f3e-139">目前登入的使用者。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-139">Currently logged in user.</span></span>|  
        |<span data-ttu-id="e6f3e-140">裝載于 IIS 6.0 （Windows Server 2003）或 IIS 7.0 （Windows Vista）中的服務。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-140">Service that is hosted in IIS 6.0 (Windows Server 2003) or IIS 7.0 (Windows Vista).</span></span>|<span data-ttu-id="e6f3e-141">NETWORK SERVICE</span><span class="sxs-lookup"><span data-stu-id="e6f3e-141">NETWORK SERVICE</span></span>|  
        |<span data-ttu-id="e6f3e-142">裝載于 IIS 5.x （Windows XP）中的服務。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-142">Service that is hosted in IIS 5.X (Windows XP).</span></span>|<span data-ttu-id="e6f3e-143">由 Machine.config 檔中的 `<processModel>` 項目控制。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-143">Controlled by the `<processModel>` element in the Machine.config file.</span></span> <span data-ttu-id="e6f3e-144">預設帳戶是 ASPNET。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-144">The default account is ASPNET.</span></span>|  
  
    5. <span data-ttu-id="e6f3e-145">使用 icacls.exe 之類的工具，將包含私密金鑰之檔案的讀取權限授與執行 WCF 的帳戶。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-145">Grant read access to the file that contains the private key to the account that WCF is running under, using a tool such as icacls.exe.</span></span>  
  
         <span data-ttu-id="e6f3e-146">下列程式碼範例會編輯指定檔案的任意存取控制清單（DACL），以將檔案的讀取（： R）存取權授與網路服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="e6f3e-146">The following code example edits the discretionary access control list (DACL) for the specified file to grant the NETWORK SERVICE account read (:R) access to the file.</span></span>  
  
        ```console
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="e6f3e-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6f3e-147">See also</span></span>

- [<span data-ttu-id="e6f3e-148">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="e6f3e-148">FindPrivateKey</span></span>](../samples/findprivatekey.md)
- [<span data-ttu-id="e6f3e-149">HOW TO：擷取憑證的指紋</span><span class="sxs-lookup"><span data-stu-id="e6f3e-149">How to: Retrieve the Thumbprint of a Certificate</span></span>](how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [<span data-ttu-id="e6f3e-150">Working with Certificates</span><span class="sxs-lookup"><span data-stu-id="e6f3e-150">Working with Certificates</span></span>](working-with-certificates.md)
