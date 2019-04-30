---
title: ICorDebugNativeFrame::GetLocalMemoryRegisterValue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalMemoryRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalMemoryRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalMemoryRegisterValue method [.NET Framework debugging]
- GetLocalMemoryRegisterValue method
ms.assetid: 33a19f6e-1029-4d53-af64-19591c6e58ee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9b2244ec1be6fc0e5e19fac5adc7ecb38d68a0af
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987983"
---
# <a name="icordebugnativeframegetlocalmemoryregistervalue-method"></a><span data-ttu-id="923b9-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue 方法</span><span class="sxs-lookup"><span data-stu-id="923b9-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue Method</span></span>
<span data-ttu-id="923b9-103">取得值的引數或區域變數，其中低位文字和高位文字會儲存在指定的暫存器和記憶體位置，分別針對此原生框架。</span><span class="sxs-lookup"><span data-stu-id="923b9-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the specified register and memory location, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="923b9-104">語法</span><span class="sxs-lookup"><span data-stu-id="923b9-104">Syntax</span></span>  
  
```  
HRESULT GetLocalMemoryRegisterValue (  
    [in] CORDB_ADDRESS      highWordAddress,  
    [in] CorDebugRegister   lowWordRegister,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="923b9-105">參數</span><span class="sxs-lookup"><span data-stu-id="923b9-105">Parameters</span></span>  
 `highWordAddress`  
 <span data-ttu-id="923b9-106">[in]A`CORDB_ADDRESS`值，指定包含值的高位文字的記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="923b9-106">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the high word of the value.</span></span>  
  
 `lowWordRegister`  
 <span data-ttu-id="923b9-107">[in]指定的暫存器包含的低位文字值的"CorDebugRegister 」 列舉值。</span><span class="sxs-lookup"><span data-stu-id="923b9-107">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="923b9-108">[in]整數，指定所參考的二進位中繼資料簽章大小`pvSigBlob`參數。</span><span class="sxs-lookup"><span data-stu-id="923b9-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="923b9-109">[in]A`PCCOR_SIGNATURE`指向的值類型的二進位中繼資料簽章的值。</span><span class="sxs-lookup"><span data-stu-id="923b9-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="923b9-110">[out]「 ICorDebugValue 」 物件，代表儲存在指定的暫存器和記憶體位置的擷取的值的位址指標。</span><span class="sxs-lookup"><span data-stu-id="923b9-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="923b9-111">需求</span><span class="sxs-lookup"><span data-stu-id="923b9-111">Requirements</span></span>  
 <span data-ttu-id="923b9-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="923b9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="923b9-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="923b9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="923b9-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="923b9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="923b9-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="923b9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="923b9-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="923b9-116">See also</span></span>
