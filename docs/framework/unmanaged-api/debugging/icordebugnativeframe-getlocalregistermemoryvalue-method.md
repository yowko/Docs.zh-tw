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
ms.openlocfilehash: f16150ad7d9ecec4b4aceee5c9266e9a7859f1cb
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213292"
---
# <a name="icordebugnativeframegetlocalregistermemoryvalue-method"></a><span data-ttu-id="89d3e-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue 方法</span><span class="sxs-lookup"><span data-stu-id="89d3e-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue Method</span></span>
<span data-ttu-id="89d3e-103">取得引數或區域變數的值，其中的低字和高單字會分別儲存在記憶體位置，並為這個原生框架指定 register。</span><span class="sxs-lookup"><span data-stu-id="89d3e-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the memory location and specified register, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89d3e-104">語法</span><span class="sxs-lookup"><span data-stu-id="89d3e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalRegisterMemoryValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CORDB_ADDRESS      lowWordAddress,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89d3e-105">參數</span><span class="sxs-lookup"><span data-stu-id="89d3e-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="89d3e-106">在"CorDebugRegister" 列舉的值，指定包含值高字的暫存器。</span><span class="sxs-lookup"><span data-stu-id="89d3e-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordAddress`  
 <span data-ttu-id="89d3e-107">在`CORDB_ADDRESS`值，指定包含值之低字的記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="89d3e-107">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="89d3e-108">在整數，指定參數所參考的二進位中繼資料簽章大小 `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="89d3e-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="89d3e-109">在`PCCOR_SIGNATURE`值，指向數值型別的二進位中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="89d3e-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="89d3e-110">脫銷"ICorDebugValue" 物件位址的指標，代表儲存在指定的暫存器和記憶體位置的已抓取值。</span><span class="sxs-lookup"><span data-stu-id="89d3e-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89d3e-111">需求</span><span class="sxs-lookup"><span data-stu-id="89d3e-111">Requirements</span></span>  
 <span data-ttu-id="89d3e-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="89d3e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89d3e-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89d3e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89d3e-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89d3e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89d3e-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89d3e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89d3e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89d3e-116">See also</span></span>
