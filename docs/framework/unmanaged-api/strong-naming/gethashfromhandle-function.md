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
ms.openlocfilehash: 3eac353252f5a97402cbd883895b3e397c39edd6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799176"
---
# <a name="gethashfromhandle-function"></a><span data-ttu-id="0c20f-102">GetHashFromHandle 函式</span><span class="sxs-lookup"><span data-stu-id="0c20f-102">GetHashFromHandle Function</span></span>
<span data-ttu-id="0c20f-103">使用指定的雜湊演算法產生以指定檔案控制代碼指定之檔案的雜湊。</span><span class="sxs-lookup"><span data-stu-id="0c20f-103">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="0c20f-104">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="0c20f-104">This function has been deprecated.</span></span> <span data-ttu-id="0c20f-105">請改用[ICLRStrongName：： GetHashFromHandle](../hosting/iclrstrongname-gethashfromhandle-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="0c20f-105">Use the [ICLRStrongName::GetHashFromHandle](../hosting/iclrstrongname-gethashfromhandle-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c20f-106">語法</span><span class="sxs-lookup"><span data-stu-id="0c20f-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c20f-107">參數</span><span class="sxs-lookup"><span data-stu-id="0c20f-107">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="0c20f-108">在要雜湊之檔案的控制碼。</span><span class="sxs-lookup"><span data-stu-id="0c20f-108">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="0c20f-109">[in、out]指定雜湊演算法的常數。</span><span class="sxs-lookup"><span data-stu-id="0c20f-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="0c20f-110">預設演算法使用零。</span><span class="sxs-lookup"><span data-stu-id="0c20f-110">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="0c20f-111">脫銷傳回的雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="0c20f-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="0c20f-112">在要求的大小`pbHash`上限。</span><span class="sxs-lookup"><span data-stu-id="0c20f-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="0c20f-113">脫銷傳回`pbHash`之的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="0c20f-113">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c20f-114">需求</span><span class="sxs-lookup"><span data-stu-id="0c20f-114">Requirements</span></span>  
 <span data-ttu-id="0c20f-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0c20f-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c20f-116">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="0c20f-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="0c20f-117">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0c20f-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0c20f-118">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c20f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c20f-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c20f-119">See also</span></span>

- [<span data-ttu-id="0c20f-120">GetHashFromHandle 方法</span><span class="sxs-lookup"><span data-stu-id="0c20f-120">GetHashFromHandle Method</span></span>](../hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="0c20f-121">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="0c20f-121">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
