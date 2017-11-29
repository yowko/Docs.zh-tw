---
title: "ICorDebugNativeFrame::GetLocalRegisterValue 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame.GetLocalRegisterValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame::GetLocalRegisterValue
helpviewer_keywords:
- GetLocalRegisterValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalRegisterValue method [.NET Framework debugging]
ms.assetid: 5ccb74f3-f891-430c-b70a-e370624edde2
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 43fdfc5cf4f17aaa9b26fc4a028c98c63a1b3c54
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugnativeframegetlocalregistervalue-method"></a><span data-ttu-id="6a753-102">ICorDebugNativeFrame::GetLocalRegisterValue 方法</span><span class="sxs-lookup"><span data-stu-id="6a753-102">ICorDebugNativeFrame::GetLocalRegisterValue Method</span></span>
<span data-ttu-id="6a753-103">取得引數或儲存在指定的暫存器，針對這個原生框架中區域變數的值。</span><span class="sxs-lookup"><span data-stu-id="6a753-103">Gets the value of an argument or local variable that is stored in the specified register for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a753-104">語法</span><span class="sxs-lookup"><span data-stu-id="6a753-104">Syntax</span></span>  
  
```  
HRESULT GetLocalRegisterValue (  
    [in]  CorDebugRegister   reg,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6a753-105">參數</span><span class="sxs-lookup"><span data-stu-id="6a753-105">Parameters</span></span>  
 `reg`  
 <span data-ttu-id="6a753-106">[in]指定的暫存器包含值"CorDebugRegister 」 列舉值。</span><span class="sxs-lookup"><span data-stu-id="6a753-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="6a753-107">[in]整數，指定所參考的二進位中繼資料簽章的大小`pvSigBlob`參數。</span><span class="sxs-lookup"><span data-stu-id="6a753-107">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="6a753-108">[in]A`PCCOR_SIGNATURE`實值類型的二進位中繼資料簽章所指向的值。</span><span class="sxs-lookup"><span data-stu-id="6a753-108">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="6a753-109">[out]代表儲存在指定的登錄中擷取的值的"ICorDebugValue 」 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="6a753-109">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a753-110">備註</span><span class="sxs-lookup"><span data-stu-id="6a753-110">Remarks</span></span>  
 <span data-ttu-id="6a753-111">`GetLocalRegisterValue`方法可以用在原生框架或在 just-in-time (JIT)-編譯框架。</span><span class="sxs-lookup"><span data-stu-id="6a753-111">The `GetLocalRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a753-112">需求</span><span class="sxs-lookup"><span data-stu-id="6a753-112">Requirements</span></span>  
 <span data-ttu-id="6a753-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6a753-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a753-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a753-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a753-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a753-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a753-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a753-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a753-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a753-117">See Also</span></span>  
 
