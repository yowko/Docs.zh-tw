---
title: GetHashFromAssemblyFile 函式
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFile
helpviewer_keywords:
- GetHashFromAssemblyFile function [.NET Framework strong naming]
ms.assetid: 751ed69f-b7ab-4e07-80de-e17ca9319b0c
topic_type:
- apiref
ms.openlocfilehash: 866b34acae333f043d8e13f4d0ebd55f32046334
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140725"
---
# <a name="gethashfromassemblyfile-function"></a><span data-ttu-id="b87fb-102">GetHashFromAssemblyFile 函式</span><span class="sxs-lookup"><span data-stu-id="b87fb-102">GetHashFromAssemblyFile Function</span></span>
<span data-ttu-id="b87fb-103">使用指定的雜湊演算法取得所指定組件檔案的雜湊。</span><span class="sxs-lookup"><span data-stu-id="b87fb-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="b87fb-104">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="b87fb-104">This function has been deprecated.</span></span> <span data-ttu-id="b87fb-105">請改用[ICLRStrongName：： GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="b87fb-105">Use the [ICLRStrongName::GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b87fb-106">語法</span><span class="sxs-lookup"><span data-stu-id="b87fb-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b87fb-107">參數</span><span class="sxs-lookup"><span data-stu-id="b87fb-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="b87fb-108">在要雜湊之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="b87fb-108">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="b87fb-109">[in、out]指定雜湊演算法的常數。</span><span class="sxs-lookup"><span data-stu-id="b87fb-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="b87fb-110">預設雜湊演算法使用零。</span><span class="sxs-lookup"><span data-stu-id="b87fb-110">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="b87fb-111">脫銷傳回的雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="b87fb-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="b87fb-112">在`pbHash`的要求大小上限。</span><span class="sxs-lookup"><span data-stu-id="b87fb-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="b87fb-113">脫銷傳回的大小，以位元組為單位，`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="b87fb-113">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b87fb-114">需求</span><span class="sxs-lookup"><span data-stu-id="b87fb-114">Requirements</span></span>  
 <span data-ttu-id="b87fb-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b87fb-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b87fb-116">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="b87fb-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="b87fb-117">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b87fb-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b87fb-118">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b87fb-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b87fb-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="b87fb-119">See also</span></span>

- [<span data-ttu-id="b87fb-120">GetHashFromAssemblyFile 方法</span><span class="sxs-lookup"><span data-stu-id="b87fb-120">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="b87fb-121">GetHashFromAssemblyFileW 方法</span><span class="sxs-lookup"><span data-stu-id="b87fb-121">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="b87fb-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="b87fb-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
