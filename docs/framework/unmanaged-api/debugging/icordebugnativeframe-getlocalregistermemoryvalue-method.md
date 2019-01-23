---
title: ICorDebugNativeFrame::GetLocalRegisterMemoryValue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalRegisterMemoryValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalRegisterMemoryValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalRegisterMemoryValue method [.NET Framework debugging]
- GetLocalRegisterMemoryValue method [.NET Framework debugging]
ms.assetid: d350f69d-9aff-4f5a-8301-daea22dee2da
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa9e168b36c8408583ca23dee070fc36b2cb076c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572990"
---
# <a name="icordebugnativeframegetlocalregistermemoryvalue-method"></a><span data-ttu-id="4bff4-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue 方法</span><span class="sxs-lookup"><span data-stu-id="4bff4-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue Method</span></span>
<span data-ttu-id="4bff4-103">取得值的引數或區域變數，其中的低位文字和高的字組會儲存在記憶體位置，分別將暫存器，指定這個原生框架。</span><span class="sxs-lookup"><span data-stu-id="4bff4-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the memory location and specified register, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bff4-104">語法</span><span class="sxs-lookup"><span data-stu-id="4bff4-104">Syntax</span></span>  
  
```  
HRESULT GetLocalRegisterMemoryValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CORDB_ADDRESS      lowWordAddress,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4bff4-105">參數</span><span class="sxs-lookup"><span data-stu-id="4bff4-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="4bff4-106">[in]指定的暫存器包含值的高位文字"CorDebugRegister 」 列舉值。</span><span class="sxs-lookup"><span data-stu-id="4bff4-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordAddress`  
 <span data-ttu-id="4bff4-107">[in]A`CORDB_ADDRESS`值，指定包含低序位文字值的記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="4bff4-107">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="4bff4-108">[in]整數，指定所參考的二進位中繼資料簽章大小`pvSigBlob`參數。</span><span class="sxs-lookup"><span data-stu-id="4bff4-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="4bff4-109">[in]A`PCCOR_SIGNATURE`指向的值類型的二進位中繼資料簽章的值。</span><span class="sxs-lookup"><span data-stu-id="4bff4-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="4bff4-110">[out]「 ICorDebugValue 」 物件，代表儲存在指定的暫存器和記憶體位置的擷取的值的位址指標。</span><span class="sxs-lookup"><span data-stu-id="4bff4-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bff4-111">需求</span><span class="sxs-lookup"><span data-stu-id="4bff4-111">Requirements</span></span>  
 <span data-ttu-id="4bff4-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4bff4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bff4-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4bff4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4bff4-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4bff4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4bff4-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bff4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bff4-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4bff4-116">See also</span></span>

