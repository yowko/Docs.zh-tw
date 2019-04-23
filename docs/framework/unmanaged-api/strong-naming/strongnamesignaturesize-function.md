---
title: StrongNameSignatureSize 函式
ms.date: 03/30/2017
api_name:
- StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureSize
helpviewer_keywords:
- StrongNameSignatureSize function [.NET Framework strong naming]
ms.assetid: 4fde4cd0-f53e-4411-a2fe-fc5c54472f95
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01c0f9ca0299e817618d93133c0eaca9fc63788e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160312"
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="7d6c1-102">StrongNameSignatureSize 函式</span><span class="sxs-lookup"><span data-stu-id="7d6c1-102">StrongNameSignatureSize Function</span></span>
<span data-ttu-id="7d6c1-103">傳回強式名稱簽章的大小。</span><span class="sxs-lookup"><span data-stu-id="7d6c1-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="7d6c1-104">`StrongNameSignatureSize` 通常是由編譯器決定要建立的延遲簽署組件時，檔案中保留多少空間。</span><span class="sxs-lookup"><span data-stu-id="7d6c1-104">`StrongNameSignatureSize` is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="7d6c1-105">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="7d6c1-105">This function has been deprecated.</span></span> <span data-ttu-id="7d6c1-106">使用[iclrstrongname:: Strongnamesignaturesize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="7d6c1-106">Use the [ICLRStrongName::StrongNameSignatureSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d6c1-107">語法</span><span class="sxs-lookup"><span data-stu-id="7d6c1-107">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="7d6c1-108">參數</span><span class="sxs-lookup"><span data-stu-id="7d6c1-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="7d6c1-109">[in]類型的結構[PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) ，其中包含用來產生強式名稱簽章金鑰組的公開部分。</span><span class="sxs-lookup"><span data-stu-id="7d6c1-109">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="7d6c1-110">[in]大小，以位元組為單位的`pbPublicKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="7d6c1-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="7d6c1-111">[in]儲存的強式名稱簽章所需的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="7d6c1-111">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d6c1-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="7d6c1-112">Return Value</span></span>  
 <span data-ttu-id="7d6c1-113">`true` 如果成功地完成;否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="7d6c1-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d6c1-114">備註</span><span class="sxs-lookup"><span data-stu-id="7d6c1-114">Remarks</span></span>  
 <span data-ttu-id="7d6c1-115">如果`StrongNameSignatureSize`函式未順利完成，請呼叫[StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)函式來擷取最後一個產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="7d6c1-115">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d6c1-116">需求</span><span class="sxs-lookup"><span data-stu-id="7d6c1-116">Requirements</span></span>  
 <span data-ttu-id="7d6c1-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7d6c1-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d6c1-118">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="7d6c1-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="7d6c1-119">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7d6c1-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7d6c1-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d6c1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d6c1-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d6c1-121">See also</span></span>

- [<span data-ttu-id="7d6c1-122">StrongNameSignatureSize 方法</span><span class="sxs-lookup"><span data-stu-id="7d6c1-122">StrongNameSignatureSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [<span data-ttu-id="7d6c1-123">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="7d6c1-123">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
