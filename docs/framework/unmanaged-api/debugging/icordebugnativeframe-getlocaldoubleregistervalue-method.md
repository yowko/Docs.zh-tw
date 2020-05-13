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
ms.openlocfilehash: 21c4d00e4156b9db27ae4188aace19764a2be53e
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213071"
---
# <a name="icordebugnativeframegetlocaldoubleregistervalue-method"></a><span data-ttu-id="661f5-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue 方法</span><span class="sxs-lookup"><span data-stu-id="661f5-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue Method</span></span>
<span data-ttu-id="661f5-103">取得在這個原生框架中，儲存在兩個指定暫存器中的引數或區域變數的值。</span><span class="sxs-lookup"><span data-stu-id="661f5-103">Gets the value of an argument or local variable that is stored in the two specified registers for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="661f5-104">語法</span><span class="sxs-lookup"><span data-stu-id="661f5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalDoubleRegisterValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CorDebugRegister   lowWordReg,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="661f5-105">參數</span><span class="sxs-lookup"><span data-stu-id="661f5-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="661f5-106">在"CorDebugRegister" 列舉的值，指定包含值高字的暫存器。</span><span class="sxs-lookup"><span data-stu-id="661f5-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordReg`  
 <span data-ttu-id="661f5-107">在`CorDebugRegister`列舉的值，指定包含值之低字的暫存器。</span><span class="sxs-lookup"><span data-stu-id="661f5-107">[in] A value of the `CorDebugRegister` enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="661f5-108">在整數，指定參數所參考的二進位中繼資料簽章大小 `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="661f5-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="661f5-109">在`PCCOR_SIGNATURE`值，指向數值型別的二進位中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="661f5-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="661f5-110">脫銷"ICorDebugValue" 物件位址的指標，代表儲存在指定暫存器中的已抓取值。</span><span class="sxs-lookup"><span data-stu-id="661f5-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified registers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="661f5-111">備註</span><span class="sxs-lookup"><span data-stu-id="661f5-111">Remarks</span></span>  
 <span data-ttu-id="661f5-112">`GetLocalDoubleRegisterValue`方法可以在原生框架或即時（JIT）編譯的框架中使用。</span><span class="sxs-lookup"><span data-stu-id="661f5-112">The `GetLocalDoubleRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="661f5-113">需求</span><span class="sxs-lookup"><span data-stu-id="661f5-113">Requirements</span></span>  
 <span data-ttu-id="661f5-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="661f5-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="661f5-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="661f5-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="661f5-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="661f5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="661f5-117">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="661f5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="661f5-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="661f5-118">See also</span></span>
