---
title: "StrongNameGetBlob 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameGetBlob
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameGetBlob
helpviewer_keywords: StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1948a0d8a8536ebe9b0531eecaf3df446252b0a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamegetblob-function"></a><span data-ttu-id="cd2bc-102">StrongNameGetBlob 函式</span><span class="sxs-lookup"><span data-stu-id="cd2bc-102">StrongNameGetBlob Function</span></span>
<span data-ttu-id="cd2bc-103">在指定位址之可執行檔的二進位表示法中填入指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="cd2bc-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
 <span data-ttu-id="cd2bc-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="cd2bc-104">This function has been deprecated.</span></span> <span data-ttu-id="cd2bc-105">使用[iclrstrongname:: Strongnamegetblob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="cd2bc-105">Use the [ICLRStrongName::StrongNameGetBLob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd2bc-106">語法</span><span class="sxs-lookup"><span data-stu-id="cd2bc-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cd2bc-107">參數</span><span class="sxs-lookup"><span data-stu-id="cd2bc-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="cd2bc-108">[in]要載入可執行檔的有效路徑。</span><span class="sxs-lookup"><span data-stu-id="cd2bc-108">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="cd2bc-109">[in]在其中載入可執行檔的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="cd2bc-109">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="cd2bc-110">[in、 out]要求的大小上限，以位元組為單位， `pbBlob`。</span><span class="sxs-lookup"><span data-stu-id="cd2bc-110">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="cd2bc-111">傳回時，實際的大小，以位元組為單位的`pbBlob`。</span><span class="sxs-lookup"><span data-stu-id="cd2bc-111">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd2bc-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="cd2bc-112">Return Value</span></span>  
 <span data-ttu-id="cd2bc-113">`true`如果成功地完成。否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="cd2bc-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd2bc-114">備註</span><span class="sxs-lookup"><span data-stu-id="cd2bc-114">Remarks</span></span>  
 <span data-ttu-id="cd2bc-115">如果`StrongNameGetBlob`函式未順利完成，請呼叫[StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)函式可擷取的最後一個產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="cd2bc-115">If the `StrongNameGetBlob` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd2bc-116">需求</span><span class="sxs-lookup"><span data-stu-id="cd2bc-116">Requirements</span></span>  
 <span data-ttu-id="cd2bc-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cd2bc-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd2bc-118">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="cd2bc-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="cd2bc-119">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="cd2bc-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cd2bc-120">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd2bc-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd2bc-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="cd2bc-121">See Also</span></span>  
 [<span data-ttu-id="cd2bc-122">StrongNameGetBlob 方法</span><span class="sxs-lookup"><span data-stu-id="cd2bc-122">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)  
 [<span data-ttu-id="cd2bc-123">StrongNameGetBlobFromImage 方法</span><span class="sxs-lookup"><span data-stu-id="cd2bc-123">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [<span data-ttu-id="cd2bc-124">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="cd2bc-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
