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
ms.openlocfilehash: 8f5cb89294004dfb1f020627ceb1edb58735f72c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732277"
---
# <a name="strongnamegetblob-function"></a><span data-ttu-id="f1608-102">StrongNameGetBlob 函式</span><span class="sxs-lookup"><span data-stu-id="f1608-102">StrongNameGetBlob Function</span></span>

<span data-ttu-id="f1608-103">使用位於所指定位址之可執行檔的二進位表示法填滿指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f1608-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
 <span data-ttu-id="f1608-104">此函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="f1608-104">This function has been deprecated.</span></span> <span data-ttu-id="f1608-105">請改用 [ICLRStrongName：： StrongNameGetBLob](../hosting/iclrstrongname-strongnamegetblob-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="f1608-105">Use the [ICLRStrongName::StrongNameGetBLob](../hosting/iclrstrongname-strongnamegetblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1608-106">語法</span><span class="sxs-lookup"><span data-stu-id="f1608-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1608-107">參數</span><span class="sxs-lookup"><span data-stu-id="f1608-107">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="f1608-108">在要載入之可執行檔的有效路徑。</span><span class="sxs-lookup"><span data-stu-id="f1608-108">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="f1608-109">在要在其中載入可執行檔的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f1608-109">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="f1608-110">[in，out]要求的大小上限（以位元組為單位） `pbBlob` 。</span><span class="sxs-lookup"><span data-stu-id="f1608-110">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="f1608-111">傳回時，的實際大小（以位元組為單位） `pbBlob` 。</span><span class="sxs-lookup"><span data-stu-id="f1608-111">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1608-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="f1608-112">Return Value</span></span>  

 <span data-ttu-id="f1608-113">`true` 成功完成時;否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="f1608-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1608-114">備註</span><span class="sxs-lookup"><span data-stu-id="f1608-114">Remarks</span></span>  

 <span data-ttu-id="f1608-115">如果函式 `StrongNameGetBlob` 未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式來取出最後產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="f1608-115">If the `StrongNameGetBlob` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1608-116">需求</span><span class="sxs-lookup"><span data-stu-id="f1608-116">Requirements</span></span>  

 <span data-ttu-id="f1608-117">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f1608-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1608-118">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="f1608-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="f1608-119">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="f1608-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f1608-120">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1608-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1608-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1608-121">See also</span></span>

- [<span data-ttu-id="f1608-122">StrongNameGetBlob 方法</span><span class="sxs-lookup"><span data-stu-id="f1608-122">StrongNameGetBlob Method</span></span>](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="f1608-123">StrongNameGetBlobFromImage 方法</span><span class="sxs-lookup"><span data-stu-id="f1608-123">StrongNameGetBlobFromImage Method</span></span>](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="f1608-124">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="f1608-124">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
