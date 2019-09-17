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
ms.openlocfilehash: 38f98b971e430a2c35a4c484f4f9c4bf387c640c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798963"
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="65f44-102">StrongNameSignatureSize 函式</span><span class="sxs-lookup"><span data-stu-id="65f44-102">StrongNameSignatureSize Function</span></span>
<span data-ttu-id="65f44-103">傳回強式名稱簽章的大小。</span><span class="sxs-lookup"><span data-stu-id="65f44-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="65f44-104">`StrongNameSignatureSize`在建立延遲簽署的元件時，編譯器通常會用來決定要在檔案中保留多少空間。</span><span class="sxs-lookup"><span data-stu-id="65f44-104">`StrongNameSignatureSize` is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="65f44-105">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="65f44-105">This function has been deprecated.</span></span> <span data-ttu-id="65f44-106">請改用[ICLRStrongName：： StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="65f44-106">Use the [ICLRStrongName::StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65f44-107">語法</span><span class="sxs-lookup"><span data-stu-id="65f44-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="65f44-108">參數</span><span class="sxs-lookup"><span data-stu-id="65f44-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="65f44-109">在[PublicKeyBlob](publickeyblob-structure.md)類型的結構，其中包含用來產生強式名稱簽章之金鑰組的公開部分。</span><span class="sxs-lookup"><span data-stu-id="65f44-109">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="65f44-110">在的大小（以位元組為單位`pbPublicKeyBlob`）。</span><span class="sxs-lookup"><span data-stu-id="65f44-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="65f44-111">在儲存強式名稱簽章所需的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="65f44-111">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="65f44-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="65f44-112">Return Value</span></span>  
 <span data-ttu-id="65f44-113">`true`成功完成時;否則為`false`。</span><span class="sxs-lookup"><span data-stu-id="65f44-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65f44-114">備註</span><span class="sxs-lookup"><span data-stu-id="65f44-114">Remarks</span></span>  
 <span data-ttu-id="65f44-115">如果 `StrongNameSignatureSize`函式未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式，以取出最後產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="65f44-115">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65f44-116">需求</span><span class="sxs-lookup"><span data-stu-id="65f44-116">Requirements</span></span>  
 <span data-ttu-id="65f44-117">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="65f44-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65f44-118">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="65f44-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="65f44-119">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="65f44-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="65f44-120">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65f44-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65f44-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65f44-121">See also</span></span>

- [<span data-ttu-id="65f44-122">StrongNameSignatureSize 方法</span><span class="sxs-lookup"><span data-stu-id="65f44-122">StrongNameSignatureSize Method</span></span>](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [<span data-ttu-id="65f44-123">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="65f44-123">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
