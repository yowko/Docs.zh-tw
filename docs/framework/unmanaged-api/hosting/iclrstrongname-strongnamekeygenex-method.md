---
title: ICLRStrongName::StrongNameKeyGenEx 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGenEx
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyGenEx method [.NET Framework hosting]
- StrongNameKeyGenEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 1f8b59d0-5b72-45b8-ab74-c2b43ffc806e
topic_type:
- apiref
ms.openlocfilehash: 9ba50616b25f9c7c592f19947c82a890ae6b5a4a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671677"
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a><span data-ttu-id="5e618-102">ICLRStrongName::StrongNameKeyGenEx 方法</span><span class="sxs-lookup"><span data-stu-id="5e618-102">ICLRStrongName::StrongNameKeyGenEx Method</span></span>

<span data-ttu-id="5e618-103">使用指定的金鑰大小產生新的公開/私密金鑰組，以供強式名稱使用。</span><span class="sxs-lookup"><span data-stu-id="5e618-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e618-104">語法</span><span class="sxs-lookup"><span data-stu-id="5e618-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e618-105">參數</span><span class="sxs-lookup"><span data-stu-id="5e618-105">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="5e618-106">在要求的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="5e618-106">[in] The requested key container name.</span></span> <span data-ttu-id="5e618-107">`wszKeyContainer` 必須為非空白字串或 null，才能產生暫存名稱。</span><span class="sxs-lookup"><span data-stu-id="5e618-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="5e618-108">在值，指定是否要保留註冊的金鑰。</span><span class="sxs-lookup"><span data-stu-id="5e618-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="5e618-109">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="5e618-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="5e618-110">0x00000000-當 `wszKeyContainer` 為 null 時，用來產生暫存金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="5e618-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="5e618-111">0x00000001 (`SN_LEAVE_KEY`) -指定應該將金鑰保持在註冊。</span><span class="sxs-lookup"><span data-stu-id="5e618-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="5e618-112">在要求的金鑰大小（以位為單位）。</span><span class="sxs-lookup"><span data-stu-id="5e618-112">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="5e618-113">擴展傳回的公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="5e618-113">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="5e618-114">擴展的大小（以位元組為單位） `ppbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="5e618-114">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e618-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="5e618-115">Return Value</span></span>  

 <span data-ttu-id="5e618-116">`S_OK` 如果方法成功完成，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。</span><span class="sxs-lookup"><span data-stu-id="5e618-116">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e618-117">備註</span><span class="sxs-lookup"><span data-stu-id="5e618-117">Remarks</span></span>  

 <span data-ttu-id="5e618-118">.NET Framework 版本1.0 和1.1 需要 `dwKeySize` 1024 位來簽署具有強式名稱的元件; 2.0 版新增了針對2048位金鑰支援的功能。</span><span class="sxs-lookup"><span data-stu-id="5e618-118">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="5e618-119">在抓取金鑰之後，您應該呼叫 [ICLRStrongName：： StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) 方法來釋放已配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="5e618-119">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e618-120">需求</span><span class="sxs-lookup"><span data-stu-id="5e618-120">Requirements</span></span>  

 <span data-ttu-id="5e618-121">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5e618-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e618-122">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="5e618-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5e618-123">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="5e618-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5e618-124">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e618-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e618-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e618-125">See also</span></span>

- [<span data-ttu-id="5e618-126">StrongNameKeyGen 方法</span><span class="sxs-lookup"><span data-stu-id="5e618-126">StrongNameKeyGen Method</span></span>](iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="5e618-127">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="5e618-127">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
