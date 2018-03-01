---
title: "ICLRDataTarget::GetPointerSize 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRDataTarget.GetPointerSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetPointerSize
helpviewer_keywords:
- GetPointerSize method [.NET Framework debugging]
- ICLRDataTarget::GetPointerSize method [.NET Framework debugging]
ms.assetid: 51d9f4a4-81a7-4527-8537-5212bdb05c70
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4ca35246b82ed4adc982b6e7b157398d230dabe4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetgetpointersize-method"></a><span data-ttu-id="20ab8-102">ICLRDataTarget::GetPointerSize 方法</span><span class="sxs-lookup"><span data-stu-id="20ab8-102">ICLRDataTarget::GetPointerSize Method</span></span>
<span data-ttu-id="20ab8-103">取得大小，以位元組為單位，目標處理序會使用與指標類型。</span><span class="sxs-lookup"><span data-stu-id="20ab8-103">Gets the size, in bytes, of the pointer type that the target process uses.</span></span> <span data-ttu-id="20ab8-104">這個方法是由通用語言執行階段資料存取服務呼叫。</span><span class="sxs-lookup"><span data-stu-id="20ab8-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20ab8-105">語法</span><span class="sxs-lookup"><span data-stu-id="20ab8-105">Syntax</span></span>  
  
```  
HRESULT GetPointerSize (  
    [out] ULONG32     *pointerSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20ab8-106">參數</span><span class="sxs-lookup"><span data-stu-id="20ab8-106">Parameters</span></span>  
 `pointerSize`  
 <span data-ttu-id="20ab8-107">[out]整數值，指定的大小，以位元組為單位，在目標處理序上之指標的指標。</span><span class="sxs-lookup"><span data-stu-id="20ab8-107">[out] A pointer to an integer value that specifies the size, in bytes, of a pointer on the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20ab8-108">備註</span><span class="sxs-lookup"><span data-stu-id="20ab8-108">Remarks</span></span>  
 <span data-ttu-id="20ab8-109">此方法是由偵錯應用程式的作者來實作。</span><span class="sxs-lookup"><span data-stu-id="20ab8-109">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20ab8-110">需求</span><span class="sxs-lookup"><span data-stu-id="20ab8-110">Requirements</span></span>  
 <span data-ttu-id="20ab8-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="20ab8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20ab8-112">**標頭：** ClrData.idl、 ClrData.h</span><span class="sxs-lookup"><span data-stu-id="20ab8-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="20ab8-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20ab8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20ab8-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20ab8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20ab8-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="20ab8-115">See Also</span></span>  
 [<span data-ttu-id="20ab8-116">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="20ab8-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
