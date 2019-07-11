---
title: ICorDebugNativeFrame::GetLocalRegisterValue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalRegisterValue
helpviewer_keywords:
- GetLocalRegisterValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalRegisterValue method [.NET Framework debugging]
ms.assetid: 5ccb74f3-f891-430c-b70a-e370624edde2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d287305934c7884d5474935e50de3d26e225975
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746158"
---
# <a name="icordebugnativeframegetlocalregistervalue-method"></a><span data-ttu-id="38dbc-102">ICorDebugNativeFrame::GetLocalRegisterValue 方法</span><span class="sxs-lookup"><span data-stu-id="38dbc-102">ICorDebugNativeFrame::GetLocalRegisterValue Method</span></span>
<span data-ttu-id="38dbc-103">取得引數或儲存在指定的暫存器，這個原生框架中區域變數的值。</span><span class="sxs-lookup"><span data-stu-id="38dbc-103">Gets the value of an argument or local variable that is stored in the specified register for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38dbc-104">語法</span><span class="sxs-lookup"><span data-stu-id="38dbc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalRegisterValue (  
    [in]  CorDebugRegister   reg,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38dbc-105">參數</span><span class="sxs-lookup"><span data-stu-id="38dbc-105">Parameters</span></span>  
 `reg`  
 <span data-ttu-id="38dbc-106">[in]指定的暫存器包含值"CorDebugRegister 」 列舉值。</span><span class="sxs-lookup"><span data-stu-id="38dbc-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="38dbc-107">[in]整數，指定所參考的二進位中繼資料簽章大小`pvSigBlob`參數。</span><span class="sxs-lookup"><span data-stu-id="38dbc-107">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="38dbc-108">[in]A`PCCOR_SIGNATURE`指向的值類型的二進位中繼資料簽章的值。</span><span class="sxs-lookup"><span data-stu-id="38dbc-108">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="38dbc-109">[out]「 ICorDebugValue 」 物件，代表儲存在指定的暫存器中擷取的值的位址指標。</span><span class="sxs-lookup"><span data-stu-id="38dbc-109">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38dbc-110">備註</span><span class="sxs-lookup"><span data-stu-id="38dbc-110">Remarks</span></span>  
 <span data-ttu-id="38dbc-111">`GetLocalRegisterValue`方法可以用在原生框架或在 just-in-time (JIT)-編譯框架。</span><span class="sxs-lookup"><span data-stu-id="38dbc-111">The `GetLocalRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38dbc-112">需求</span><span class="sxs-lookup"><span data-stu-id="38dbc-112">Requirements</span></span>  
 <span data-ttu-id="38dbc-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="38dbc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38dbc-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38dbc-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38dbc-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38dbc-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38dbc-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38dbc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38dbc-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38dbc-117">See also</span></span>
