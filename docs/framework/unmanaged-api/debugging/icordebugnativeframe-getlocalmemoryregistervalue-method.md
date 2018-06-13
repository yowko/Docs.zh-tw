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
ms.openlocfilehash: 44f220f12f72ca8d0be6a9fc50b363c9bccb85fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417585"
---
# <a name="icordebugnativeframegetlocalmemoryregistervalue-method"></a><span data-ttu-id="d7ca5-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue 方法</span><span class="sxs-lookup"><span data-stu-id="d7ca5-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue Method</span></span>
<span data-ttu-id="d7ca5-103">取得引數或本機變數，其中低 word 與 word 高分別儲存在指定的暫存器和記憶體位置，這個原生的畫面格的值。</span><span class="sxs-lookup"><span data-stu-id="d7ca5-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the specified register and memory location, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7ca5-104">語法</span><span class="sxs-lookup"><span data-stu-id="d7ca5-104">Syntax</span></span>  
  
```  
HRESULT GetLocalMemoryRegisterValue (  
    [in] CORDB_ADDRESS      highWordAddress,  
    [in] CorDebugRegister   lowWordRegister,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d7ca5-105">參數</span><span class="sxs-lookup"><span data-stu-id="d7ca5-105">Parameters</span></span>  
 `highWordAddress`  
 <span data-ttu-id="d7ca5-106">[in]A`CORDB_ADDRESS`值，指定包含高值的文字的記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="d7ca5-106">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the high word of the value.</span></span>  
  
 `lowWordRegister`  
 <span data-ttu-id="d7ca5-107">[in]指定包含低值的 「 註冊 」 CorDebugRegister 」 列舉值。</span><span class="sxs-lookup"><span data-stu-id="d7ca5-107">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="d7ca5-108">[in]整數，指定所參考的二進位中繼資料簽章的大小`pvSigBlob`參數。</span><span class="sxs-lookup"><span data-stu-id="d7ca5-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="d7ca5-109">[in]A`PCCOR_SIGNATURE`實值類型的二進位中繼資料簽章所指向的值。</span><span class="sxs-lookup"><span data-stu-id="d7ca5-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="d7ca5-110">[out]代表儲存在指定的暫存器和記憶體位置的擷取的值的"ICorDebugValue 」 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="d7ca5-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7ca5-111">需求</span><span class="sxs-lookup"><span data-stu-id="d7ca5-111">Requirements</span></span>  
 <span data-ttu-id="d7ca5-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d7ca5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7ca5-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7ca5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7ca5-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7ca5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7ca5-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7ca5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7ca5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7ca5-116">See Also</span></span>  
 
