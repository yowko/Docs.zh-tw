---
title: ICorDebugNativeFrame::GetLocalDoubleRegisterValue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalDoubleRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue method [.NET Framework debugging]
- GetLocalDoubleRegisterValue method [.NET Framework debugging]
ms.assetid: 1f838215-ac8a-434f-8ce6-03021d3098d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13e1e3369c4e7a185c2167facc8514b5cfc85a85
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115865"
---
# <a name="icordebugnativeframegetlocaldoubleregistervalue-method"></a><span data-ttu-id="c33ad-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue 方法</span><span class="sxs-lookup"><span data-stu-id="c33ad-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue Method</span></span>
<span data-ttu-id="c33ad-103">取得引數或儲存在兩個指定的暫存器，這個原生框架中區域變數的值。</span><span class="sxs-lookup"><span data-stu-id="c33ad-103">Gets the value of an argument or local variable that is stored in the two specified registers for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c33ad-104">語法</span><span class="sxs-lookup"><span data-stu-id="c33ad-104">Syntax</span></span>  
  
```  
HRESULT GetLocalDoubleRegisterValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CorDebugRegister   lowWordReg,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c33ad-105">參數</span><span class="sxs-lookup"><span data-stu-id="c33ad-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="c33ad-106">[in]指定的暫存器包含值的高位文字"CorDebugRegister 」 列舉值。</span><span class="sxs-lookup"><span data-stu-id="c33ad-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordReg`  
 <span data-ttu-id="c33ad-107">[in]值為`CorDebugRegister`列舉，指定包含之值的低位文字的暫存器。</span><span class="sxs-lookup"><span data-stu-id="c33ad-107">[in] A value of the `CorDebugRegister` enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="c33ad-108">[in]整數，指定所參考的二進位中繼資料簽章大小`pvSigBlob`參數。</span><span class="sxs-lookup"><span data-stu-id="c33ad-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="c33ad-109">[in]A`PCCOR_SIGNATURE`指向的值類型的二進位中繼資料簽章的值。</span><span class="sxs-lookup"><span data-stu-id="c33ad-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="c33ad-110">[out]「 ICorDebugValue 」 物件，代表儲存在指定的暫存器中擷取的值的位址指標。</span><span class="sxs-lookup"><span data-stu-id="c33ad-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified registers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c33ad-111">備註</span><span class="sxs-lookup"><span data-stu-id="c33ad-111">Remarks</span></span>  
 <span data-ttu-id="c33ad-112">`GetLocalDoubleRegisterValue`方法可以用在原生框架或在 just-in-time (JIT)-編譯框架。</span><span class="sxs-lookup"><span data-stu-id="c33ad-112">The `GetLocalDoubleRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c33ad-113">需求</span><span class="sxs-lookup"><span data-stu-id="c33ad-113">Requirements</span></span>  
 <span data-ttu-id="c33ad-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c33ad-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c33ad-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c33ad-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c33ad-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c33ad-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c33ad-117">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c33ad-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c33ad-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c33ad-118">See also</span></span>
