---
title: ICorDebugNativeFrame::GetLocalMemoryValue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalMemoryValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalMemoryValue
helpviewer_keywords:
- GetLocalMemoryValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalMemoryValue method [.NET Framework debugging]
ms.assetid: b600b3a2-9908-42d8-8093-ab6f39e9a2c9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e8d0c16000c78fab0371b68c3a350bd2018aa1c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664521"
---
# <a name="icordebugnativeframegetlocalmemoryvalue-method"></a><span data-ttu-id="dcca4-102">ICorDebugNativeFrame::GetLocalMemoryValue 方法</span><span class="sxs-lookup"><span data-stu-id="dcca4-102">ICorDebugNativeFrame::GetLocalMemoryValue Method</span></span>
<span data-ttu-id="dcca4-103">取得引數或儲存在指定的記憶體位置，這個原生框架中區域變數的值。</span><span class="sxs-lookup"><span data-stu-id="dcca4-103">Gets the value of an argument or local variable that is stored in the specified memory location for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcca4-104">語法</span><span class="sxs-lookup"><span data-stu-id="dcca4-104">Syntax</span></span>  
  
```  
HRESULT GetLocalMemoryValue (  
    [in]  CORDB_ADDRESS      address,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dcca4-105">參數</span><span class="sxs-lookup"><span data-stu-id="dcca4-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="dcca4-106">[in]A`CORDB_ADDRESS`值，指定記憶體位置包含的值。</span><span class="sxs-lookup"><span data-stu-id="dcca4-106">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="dcca4-107">[in]整數，指定所參考的二進位中繼資料簽章大小`pvSigBlob`參數。</span><span class="sxs-lookup"><span data-stu-id="dcca4-107">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="dcca4-108">[in]A`PCCOR_SIGNATURE`指向的值類型的二進位中繼資料簽章的值。</span><span class="sxs-lookup"><span data-stu-id="dcca4-108">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="dcca4-109">[out]「 ICorDebugValue 」 物件，代表儲存在指定的記憶體位置的擷取的值的位址指標。</span><span class="sxs-lookup"><span data-stu-id="dcca4-109">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcca4-110">需求</span><span class="sxs-lookup"><span data-stu-id="dcca4-110">Requirements</span></span>  
 <span data-ttu-id="dcca4-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dcca4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcca4-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dcca4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dcca4-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dcca4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dcca4-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcca4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcca4-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dcca4-115">See also</span></span>

