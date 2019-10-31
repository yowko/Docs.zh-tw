---
title: StrongNameGetBlob 函式
ms.date: 03/30/2017
api_name:
- StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlob
helpviewer_keywords:
- StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type:
- apiref
ms.openlocfilehash: e99346ecca651346b46c220a5e427cbc7f4c4697
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095019"
---
# <a name="strongnamegetblob-function"></a><span data-ttu-id="fd331-102">StrongNameGetBlob 函式</span><span class="sxs-lookup"><span data-stu-id="fd331-102">StrongNameGetBlob Function</span></span>
<span data-ttu-id="fd331-103">使用位於所指定位址之可執行檔的二進位表示法填滿指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="fd331-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
 <span data-ttu-id="fd331-104">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="fd331-104">This function has been deprecated.</span></span> <span data-ttu-id="fd331-105">請改用[ICLRStrongName：： StrongNameGetBLob](../hosting/iclrstrongname-strongnamegetblob-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="fd331-105">Use the [ICLRStrongName::StrongNameGetBLob](../hosting/iclrstrongname-strongnamegetblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd331-106">語法</span><span class="sxs-lookup"><span data-stu-id="fd331-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd331-107">參數</span><span class="sxs-lookup"><span data-stu-id="fd331-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="fd331-108">在要載入之可執行檔的有效路徑。</span><span class="sxs-lookup"><span data-stu-id="fd331-108">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="fd331-109">在要載入可執行檔的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="fd331-109">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="fd331-110">[in、out]`pbBlob`的要求大小上限（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="fd331-110">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="fd331-111">傳回時，`pbBlob`的實際大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="fd331-111">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd331-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="fd331-112">Return Value</span></span>  
 <span data-ttu-id="fd331-113">成功完成時 `true`;否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="fd331-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd331-114">備註</span><span class="sxs-lookup"><span data-stu-id="fd331-114">Remarks</span></span>  
 <span data-ttu-id="fd331-115">如果 `StrongNameGetBlob` 函式未順利完成，請呼叫[StrongNameErrorInfo](strongnameerrorinfo-function.md)函式，以取出最後產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="fd331-115">If the `StrongNameGetBlob` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd331-116">需求</span><span class="sxs-lookup"><span data-stu-id="fd331-116">Requirements</span></span>  
 <span data-ttu-id="fd331-117">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fd331-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd331-118">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="fd331-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="fd331-119">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fd331-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fd331-120">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd331-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd331-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="fd331-121">See also</span></span>

- [<span data-ttu-id="fd331-122">StrongNameGetBlob 方法</span><span class="sxs-lookup"><span data-stu-id="fd331-122">StrongNameGetBlob Method</span></span>](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="fd331-123">StrongNameGetBlobFromImage 方法</span><span class="sxs-lookup"><span data-stu-id="fd331-123">StrongNameGetBlobFromImage Method</span></span>](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="fd331-124">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="fd331-124">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
