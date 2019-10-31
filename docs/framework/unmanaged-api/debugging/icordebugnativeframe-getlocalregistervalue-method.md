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
ms.openlocfilehash: 132e0868426670ba61d8ee12ba7007be1a8a52de
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139404"
---
# <a name="icordebugnativeframegetlocalregistervalue-method"></a><span data-ttu-id="164ff-102">ICorDebugNativeFrame::GetLocalRegisterValue 方法</span><span class="sxs-lookup"><span data-stu-id="164ff-102">ICorDebugNativeFrame::GetLocalRegisterValue Method</span></span>
<span data-ttu-id="164ff-103">取得儲存在這個原生框架之指定暫存器中的引數或區域變數的值。</span><span class="sxs-lookup"><span data-stu-id="164ff-103">Gets the value of an argument or local variable that is stored in the specified register for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="164ff-104">語法</span><span class="sxs-lookup"><span data-stu-id="164ff-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalRegisterValue (  
    [in]  CorDebugRegister   reg,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="164ff-105">參數</span><span class="sxs-lookup"><span data-stu-id="164ff-105">Parameters</span></span>  
 `reg`  
 <span data-ttu-id="164ff-106">在"CorDebugRegister" 列舉的值，指定包含值的暫存器。</span><span class="sxs-lookup"><span data-stu-id="164ff-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="164ff-107">在整數，指定 `pvSigBlob` 參數所參考的二進位中繼資料簽章大小。</span><span class="sxs-lookup"><span data-stu-id="164ff-107">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="164ff-108">在`PCCOR_SIGNATURE` 值，指向數值型別的二進位中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="164ff-108">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="164ff-109">脫銷"ICorDebugValue" 物件位址的指標，代表儲存在指定之暫存器中的已抓取值。</span><span class="sxs-lookup"><span data-stu-id="164ff-109">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="164ff-110">備註</span><span class="sxs-lookup"><span data-stu-id="164ff-110">Remarks</span></span>  
 <span data-ttu-id="164ff-111">`GetLocalRegisterValue` 方法可以在原生框架或即時（JIT）編譯的框架中使用。</span><span class="sxs-lookup"><span data-stu-id="164ff-111">The `GetLocalRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="164ff-112">需求</span><span class="sxs-lookup"><span data-stu-id="164ff-112">Requirements</span></span>  
 <span data-ttu-id="164ff-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="164ff-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="164ff-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="164ff-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="164ff-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="164ff-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="164ff-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="164ff-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="164ff-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="164ff-117">See also</span></span>
