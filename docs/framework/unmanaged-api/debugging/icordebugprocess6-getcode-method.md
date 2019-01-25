---
title: ICorDebugProcess6::GetCode 方法
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 30464956adf09ee4cc55db183c34396beacf070e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720447"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="32dbe-102">ICorDebugProcess6::GetCode 方法</span><span class="sxs-lookup"><span data-stu-id="32dbe-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="32dbe-103">取得特定程式碼位址之 Managed 程式碼的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="32dbe-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32dbe-104">語法</span><span class="sxs-lookup"><span data-stu-id="32dbe-104">Syntax</span></span>  
  
```  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,   
    [out] ICorDebugCode **ppCode);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32dbe-105">參數</span><span class="sxs-lookup"><span data-stu-id="32dbe-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="32dbe-106">[in]A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)值，指定 managed 程式碼區段的起始位址。</span><span class="sxs-lookup"><span data-stu-id="32dbe-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="32dbe-107">[out]代表一段 managed 程式碼 」 ICorDebugCode 」 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="32dbe-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32dbe-108">備註</span><span class="sxs-lookup"><span data-stu-id="32dbe-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32dbe-109">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="32dbe-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32dbe-110">需求</span><span class="sxs-lookup"><span data-stu-id="32dbe-110">Requirements</span></span>  
 <span data-ttu-id="32dbe-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="32dbe-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32dbe-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="32dbe-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32dbe-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32dbe-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32dbe-114">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32dbe-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32dbe-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32dbe-115">See also</span></span>
- [<span data-ttu-id="32dbe-116">ICorDebugProcess6 介面</span><span class="sxs-lookup"><span data-stu-id="32dbe-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="32dbe-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="32dbe-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
