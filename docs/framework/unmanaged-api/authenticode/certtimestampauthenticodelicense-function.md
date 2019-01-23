---
title: CertTimestampAuthenticodeLicense 函式
ms.date: 03/30/2017
api_name:
- CertTimestampAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d468325a-21c5-43ce-8567-84e342b22308
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9987640f988f2239a01d2dfdbcd6b1684579d8bc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601502"
---
# <a name="certtimestampauthenticodelicense-function"></a><span data-ttu-id="f3dc1-102">CertTimestampAuthenticodeLicense 函式</span><span class="sxs-lookup"><span data-stu-id="f3dc1-102">CertTimestampAuthenticodeLicense Function</span></span>
<span data-ttu-id="f3dc1-103">為 Authenticode XrML 授權加上時間戳記。</span><span class="sxs-lookup"><span data-stu-id="f3dc1-103">Time-stamps an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3dc1-104">語法</span><span class="sxs-lookup"><span data-stu-id="f3dc1-104">Syntax</span></span>  
  
```  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f3dc1-105">參數</span><span class="sxs-lookup"><span data-stu-id="f3dc1-105">Parameters</span></span>  
 `pSignedLicenseBlob`  
 <span data-ttu-id="f3dc1-106">[in] 要加上時間戳記的已簽署 Authenticode XrML 授權。</span><span class="sxs-lookup"><span data-stu-id="f3dc1-106">[in] The signed Authenticode XrML license to be time-stamped.</span></span> <span data-ttu-id="f3dc1-107">請參閱[CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob)結構。</span><span class="sxs-lookup"><span data-stu-id="f3dc1-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `pwszTimestampURI`  
 <span data-ttu-id="f3dc1-108">[in] 時間戳記伺服器的 URI。</span><span class="sxs-lookup"><span data-stu-id="f3dc1-108">[in] The time-stamp server's URI.</span></span>  
  
 `pTimestampSignatureBlob`  
 <span data-ttu-id="f3dc1-109">[out] CRYPT_DATA_BLOB (要接收 Base 64 編碼的時間戳記簽章) 的指標。</span><span class="sxs-lookup"><span data-stu-id="f3dc1-109">[out] A pointer to CRYPT_DATA_BLOB to receive the base64-encoded time-stamp signature.</span></span> <span data-ttu-id="f3dc1-110">是免費的呼叫者的責任`pTimestampSignatureBlob` -> `pbData`使用`HepFree()`之後使用。</span><span class="sxs-lookup"><span data-stu-id="f3dc1-110">It is the caller's responsibility to free `pTimestampSignatureBlob`->`pbData` with `HepFree()` after use.</span></span> <span data-ttu-id="f3dc1-111">請參閱[CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob)結構。</span><span class="sxs-lookup"><span data-stu-id="f3dc1-111">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3dc1-112">備註</span><span class="sxs-lookup"><span data-stu-id="f3dc1-112">Remarks</span></span>  
 <span data-ttu-id="f3dc1-113">時間戳記簽章實際上是 PKCS #7 SignedData 訊息，其內容是來自授權簽章的 SignatureValue 二進位格式。</span><span class="sxs-lookup"><span data-stu-id="f3dc1-113">The time-stamp signature is actually a PKCS #7 SignedData message whose content is the binary form of the SignatureValue from the license's signature.</span></span> <span data-ttu-id="f3dc1-114">基本上是將此當作授權的副署。</span><span class="sxs-lookup"><span data-stu-id="f3dc1-114">Basically, this acts as a counter-signature of the license.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3dc1-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="f3dc1-115">Return Value</span></span>  
 <span data-ttu-id="f3dc1-116">若函式成功則傳回 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="f3dc1-116">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="f3dc1-117">反之則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="f3dc1-117">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3dc1-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3dc1-118">See also</span></span>
- [<span data-ttu-id="f3dc1-119">Authenticode</span><span class="sxs-lookup"><span data-stu-id="f3dc1-119">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
