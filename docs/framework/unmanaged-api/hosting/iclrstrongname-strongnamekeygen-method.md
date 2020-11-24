---
title: ICLRStrongName::StrongNameKeyGen 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyGen method [.NET Framework hosting]
ms.assetid: ac5c1245-9acf-4271-9c08-3d9b7c670df3
topic_type:
- apiref
ms.openlocfilehash: 42a9fc1a05e97bbd893f0a2e77087e6524ad844f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674537"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a><span data-ttu-id="272ec-102">ICLRStrongName::StrongNameKeyGen 方法</span><span class="sxs-lookup"><span data-stu-id="272ec-102">ICLRStrongName::StrongNameKeyGen Method</span></span>

<span data-ttu-id="272ec-103">建立將供強式名稱使用的新公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="272ec-103">Creates a new public/private key pair for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="272ec-104">語法</span><span class="sxs-lookup"><span data-stu-id="272ec-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="272ec-105">參數</span><span class="sxs-lookup"><span data-stu-id="272ec-105">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="272ec-106">在要求的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="272ec-106">[in] The requested key container name.</span></span> <span data-ttu-id="272ec-107">`wszKeyContainer` 必須為非空白字串或 null，才能產生暫存名稱。</span><span class="sxs-lookup"><span data-stu-id="272ec-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="272ec-108">在值，指定是否要保留註冊的金鑰。</span><span class="sxs-lookup"><span data-stu-id="272ec-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="272ec-109">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="272ec-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="272ec-110">0x00000000-當 `wszKeyContainer` 為 null 時，用來產生暫存金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="272ec-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="272ec-111">0x00000001 (`SN_LEAVE_KEY`) -指定應該將金鑰保持在註冊。</span><span class="sxs-lookup"><span data-stu-id="272ec-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="272ec-112">擴展傳回的公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="272ec-112">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="272ec-113">擴展的大小（以位元組為單位） `ppbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="272ec-113">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="272ec-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="272ec-114">Return Value</span></span>  

 <span data-ttu-id="272ec-115">`S_OK` 如果方法成功完成，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。</span><span class="sxs-lookup"><span data-stu-id="272ec-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="272ec-116">備註</span><span class="sxs-lookup"><span data-stu-id="272ec-116">Remarks</span></span>  

 <span data-ttu-id="272ec-117">[ICLRStrongName：： StrongNameKeyGen](iclrstrongname-strongnamekeygen-method.md)方法會建立1024位的金鑰。</span><span class="sxs-lookup"><span data-stu-id="272ec-117">The [ICLRStrongName::StrongNameKeyGen](iclrstrongname-strongnamekeygen-method.md) method creates a 1024-bit key.</span></span> <span data-ttu-id="272ec-118">在抓取金鑰之後，您應該呼叫 [ICLRStrongName：： StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) 方法來釋放已配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="272ec-118">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="272ec-119">需求</span><span class="sxs-lookup"><span data-stu-id="272ec-119">Requirements</span></span>  

 <span data-ttu-id="272ec-120">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="272ec-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="272ec-121">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="272ec-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="272ec-122">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="272ec-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="272ec-123">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="272ec-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="272ec-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="272ec-124">See also</span></span>

- [<span data-ttu-id="272ec-125">StrongNameKeyGenEx 方法</span><span class="sxs-lookup"><span data-stu-id="272ec-125">StrongNameKeyGenEx Method</span></span>](iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="272ec-126">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="272ec-126">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
