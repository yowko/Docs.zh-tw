---
title: "ICorDebugNativeFrame::GetLocalRegisterMemoryValue 方法"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 47520e6ab4c8c3bba7383ddd08b7ff23be9dddc3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframegetlocalregistermemoryvalue-method"></a><span data-ttu-id="9558d-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue 方法</span><span class="sxs-lookup"><span data-stu-id="9558d-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue Method</span></span>
<span data-ttu-id="9558d-103">取得值的引數或本機變數，其中的斷低和高的字組會儲存在記憶體位置，指定暫存器，分別針對這個原生框架。</span><span class="sxs-lookup"><span data-stu-id="9558d-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the memory location and specified register, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9558d-104">語法</span><span class="sxs-lookup"><span data-stu-id="9558d-104">Syntax</span></span>  
  
```  
HRESULT GetLocalRegisterMemoryValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CORDB_ADDRESS      lowWordAddress,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9558d-105">參數</span><span class="sxs-lookup"><span data-stu-id="9558d-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="9558d-106">[in]指定的暫存器會包含值的 「 高 」 CorDebugRegister 」 列舉值。</span><span class="sxs-lookup"><span data-stu-id="9558d-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordAddress`  
 <span data-ttu-id="9558d-107">[in]A`CORDB_ADDRESS`值，指定包含低序位文字值的記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="9558d-107">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="9558d-108">[in]整數，指定所參考的二進位中繼資料簽章的大小`pvSigBlob`參數。</span><span class="sxs-lookup"><span data-stu-id="9558d-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="9558d-109">[in]A`PCCOR_SIGNATURE`實值類型的二進位中繼資料簽章所指向的值。</span><span class="sxs-lookup"><span data-stu-id="9558d-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="9558d-110">[out]代表儲存在指定的暫存器和記憶體位置的擷取的值的"ICorDebugValue 」 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="9558d-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9558d-111">需求</span><span class="sxs-lookup"><span data-stu-id="9558d-111">Requirements</span></span>  
 <span data-ttu-id="9558d-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9558d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9558d-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9558d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9558d-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9558d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9558d-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9558d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9558d-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="9558d-116">See Also</span></span>  
 
