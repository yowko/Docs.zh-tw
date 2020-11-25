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
ms.openlocfilehash: 15485ac94ed9074baacc4fd2662a04bdcefcf1e7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709317"
---
# <a name="icordebugnativeframegetlocalmemoryregistervalue-method"></a><span data-ttu-id="5f5b0-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue 方法</span><span class="sxs-lookup"><span data-stu-id="5f5b0-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue Method</span></span>

<span data-ttu-id="5f5b0-103">取得引數或區域變數的值，此值會在這個原生框架分別儲存在指定的暫存器和記憶體位置中。</span><span class="sxs-lookup"><span data-stu-id="5f5b0-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the specified register and memory location, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f5b0-104">語法</span><span class="sxs-lookup"><span data-stu-id="5f5b0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalMemoryRegisterValue (  
    [in] CORDB_ADDRESS      highWordAddress,  
    [in] CorDebugRegister   lowWordRegister,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f5b0-105">參數</span><span class="sxs-lookup"><span data-stu-id="5f5b0-105">Parameters</span></span>  

 `highWordAddress`  
 <span data-ttu-id="5f5b0-106">在 `CORDB_ADDRESS` 值，指定包含值的最高文字的記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="5f5b0-106">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the high word of the value.</span></span>  
  
 `lowWordRegister`  
 <span data-ttu-id="5f5b0-107">在"CorDebugRegister" 列舉值，指定包含值低字的暫存器。</span><span class="sxs-lookup"><span data-stu-id="5f5b0-107">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="5f5b0-108">在整數，指定參數所參考之二進位中繼資料簽章的大小 `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="5f5b0-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="5f5b0-109">在 `PCCOR_SIGNATURE` 指向值型別之二進位中繼資料簽章的值。</span><span class="sxs-lookup"><span data-stu-id="5f5b0-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="5f5b0-110">擴展"ICorDebugValue" 物件位址的指標，表示儲存在指定的暫存器和記憶體位置中的已抓取值。</span><span class="sxs-lookup"><span data-stu-id="5f5b0-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f5b0-111">需求</span><span class="sxs-lookup"><span data-stu-id="5f5b0-111">Requirements</span></span>  

 <span data-ttu-id="5f5b0-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5f5b0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f5b0-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5f5b0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5f5b0-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f5b0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f5b0-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f5b0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f5b0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f5b0-116">See also</span></span>
