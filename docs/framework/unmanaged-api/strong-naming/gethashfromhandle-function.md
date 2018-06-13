---
title: GetHashFromHandle 函式
ms.date: 03/30/2017
api_name:
- GetHashFromHandle
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle function [.NET Framework strong naming]
ms.assetid: 9e00337f-b307-4602-9bc3-965a8dbf02cd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 30aad6fc62c8fee7448163ca69117b804203d505
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456478"
---
# <a name="gethashfromhandle-function"></a><span data-ttu-id="dce97-102">GetHashFromHandle 函式</span><span class="sxs-lookup"><span data-stu-id="dce97-102">GetHashFromHandle Function</span></span>
<span data-ttu-id="dce97-103">產生之雜湊與指定的檔案控制代碼，使用指定的雜湊演算法檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="dce97-103">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="dce97-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="dce97-104">This function has been deprecated.</span></span> <span data-ttu-id="dce97-105">使用[iclrstrongname:: Gethashfromhandle](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="dce97-105">Use the [ICLRStrongName::GetHashFromHandle](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dce97-106">語法</span><span class="sxs-lookup"><span data-stu-id="dce97-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dce97-107">參數</span><span class="sxs-lookup"><span data-stu-id="dce97-107">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="dce97-108">[in]要雜湊的檔案控制代碼。</span><span class="sxs-lookup"><span data-stu-id="dce97-108">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="dce97-109">[in、 out]常數，指定的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="dce97-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="dce97-110">使用預設演算法為零。</span><span class="sxs-lookup"><span data-stu-id="dce97-110">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="dce97-111">[out]傳回雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="dce97-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="dce97-112">[in]要求的大小上限的`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="dce97-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="dce97-113">[out]大小，以位元組為單位傳回`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="dce97-113">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dce97-114">需求</span><span class="sxs-lookup"><span data-stu-id="dce97-114">Requirements</span></span>  
 <span data-ttu-id="dce97-115">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dce97-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dce97-116">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="dce97-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="dce97-117">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="dce97-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dce97-118">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dce97-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dce97-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dce97-119">See Also</span></span>  
 [<span data-ttu-id="dce97-120">GetHashFromHandle 方法</span><span class="sxs-lookup"><span data-stu-id="dce97-120">GetHashFromHandle Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)  
 [<span data-ttu-id="dce97-121">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="dce97-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
