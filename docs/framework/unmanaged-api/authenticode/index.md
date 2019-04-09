---
title: Authenticode (Unmanaged API 參考)
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 408219307015d5c39cb581b3884ed9810f4c0566
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216341"
---
# <a name="authenticode-unmanaged-api-reference"></a><span data-ttu-id="eea31-102">Authenticode (Unmanaged API 參考)</span><span class="sxs-lookup"><span data-stu-id="eea31-102">Authenticode (Unmanaged API Reference)</span></span>
<span data-ttu-id="eea31-103">支援 Authenticode XrML 授權的建立及驗證模組。</span><span class="sxs-lookup"><span data-stu-id="eea31-103">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eea31-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="eea31-104">In This Section</span></span>  
 [<span data-ttu-id="eea31-105">_AxlGetIssuerPublicKeyHash 函式</span><span class="sxs-lookup"><span data-stu-id="eea31-105">_AxlGetIssuerPublicKeyHash Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axlgetissuerpublickeyhash-function.md)  
 <span data-ttu-id="eea31-106">擷取公開金鑰的 SHA-1 雜湊，該公開金鑰與用來簽署指定憑證的私密金鑰相關聯。</span><span class="sxs-lookup"><span data-stu-id="eea31-106">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
 [<span data-ttu-id="eea31-107">_AxlPublicKeyBlobToPublicKeyToken 函式</span><span class="sxs-lookup"><span data-stu-id="eea31-107">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axlpublickeyblobtopublickeytoken-function.md)  
 <span data-ttu-id="eea31-108">從 CSP PUBLICKEYBLOB 格式運算強式名稱公開金鑰語彙基元。</span><span class="sxs-lookup"><span data-stu-id="eea31-108">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
 [<span data-ttu-id="eea31-109">_AxlRSAKeyValueToPublicKeyToken 函式</span><span class="sxs-lookup"><span data-stu-id="eea31-109">_AxlRSAKeyValueToPublicKeyToken Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axlrsakeyvaluetopublickeytoken-function.md)  
 <span data-ttu-id="eea31-110">將模數和指數轉換成強式名稱公開金鑰語彙基元。</span><span class="sxs-lookup"><span data-stu-id="eea31-110">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
 [<span data-ttu-id="eea31-111">CertFreeAuthenticodeSignerInfo 函式</span><span class="sxs-lookup"><span data-stu-id="eea31-111">CertFreeAuthenticodeSignerInfo Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md)  
 <span data-ttu-id="eea31-112">釋出配置給 AXL_AUTHENTICODE_SIGNER_INFO 結構的資源。</span><span class="sxs-lookup"><span data-stu-id="eea31-112">Frees resources allocated for the AXL_AUTHENTICODE_SIGNER_INFO structure.</span></span>  
  
 [<span data-ttu-id="eea31-113">CertFreeAuthenticodeTimestamperInfo 函式</span><span class="sxs-lookup"><span data-stu-id="eea31-113">CertFreeAuthenticodeTimestamperInfo Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md)  
 <span data-ttu-id="eea31-114">釋出配置給 AXL_AUTHENTICODE_TIMESTAMPER_INFO 結構的資源。</span><span class="sxs-lookup"><span data-stu-id="eea31-114">Frees resources allocated for the AXL_AUTHENTICODE_TIMESTAMPER_INFO structure.</span></span>  
  
 [<span data-ttu-id="eea31-115">CertTimestampAuthenticodeLicense 函式</span><span class="sxs-lookup"><span data-stu-id="eea31-115">CertTimestampAuthenticodeLicense Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certtimestampauthenticodelicense-function.md)  
 <span data-ttu-id="eea31-116">為 CertCreateAuthenticodeLicense 建立的 Authenticode XrML 授權加註時間戳記。</span><span class="sxs-lookup"><span data-stu-id="eea31-116">Time stamps an Authenticode XrML license created by CertCreateAuthenticodeLicense.</span></span>  
  
 [<span data-ttu-id="eea31-117">CertVerifyAuthenticodeLicense 函式</span><span class="sxs-lookup"><span data-stu-id="eea31-117">CertVerifyAuthenticodeLicense Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certverifyauthenticodelicense-function.md)  
 <span data-ttu-id="eea31-118">驗證 Authenticode XrML 授權的有效性。</span><span class="sxs-lookup"><span data-stu-id="eea31-118">Verifies the validity of an Authenticode XrML license.</span></span>  
  
 [<span data-ttu-id="eea31-119">AXL_AUTHENTICODE_SIGNER_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="eea31-119">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)  
 <span data-ttu-id="eea31-120">定義 Authenticode 簽署人資訊。</span><span class="sxs-lookup"><span data-stu-id="eea31-120">Defines the Authenticode signer information.</span></span>  
  
 [<span data-ttu-id="eea31-121">AXL_AUTHENTICODE_TIMESTAMPER_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="eea31-121">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md)  
 <span data-ttu-id="eea31-122">定義 Authenticode 時間戳記程式資訊。</span><span class="sxs-lookup"><span data-stu-id="eea31-122">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eea31-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eea31-123">See also</span></span>

- [<span data-ttu-id="eea31-124">Unmanaged API 參考</span><span class="sxs-lookup"><span data-stu-id="eea31-124">Unmanaged API Reference</span></span>](../../../../docs/framework/unmanaged-api/index.md)
