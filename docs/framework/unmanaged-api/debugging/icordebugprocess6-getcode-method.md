---
title: ICorDebugProcess6::GetCode 方法
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
ms.openlocfilehash: 94882c67752705f9f13b858ae3b386a19dc103a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178548"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="6b97f-102">ICorDebugProcess6::GetCode 方法</span><span class="sxs-lookup"><span data-stu-id="6b97f-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="6b97f-103">取得特定程式碼位址之 Managed 程式碼的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="6b97f-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b97f-104">語法</span><span class="sxs-lookup"><span data-stu-id="6b97f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b97f-105">參數</span><span class="sxs-lookup"><span data-stu-id="6b97f-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="6b97f-106">[在]指定託管程式碼片段的起始位址[CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)值。</span><span class="sxs-lookup"><span data-stu-id="6b97f-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="6b97f-107">[出]指向表示託管程式碼片段的"ICorDebugCode"物件位址的指標。</span><span class="sxs-lookup"><span data-stu-id="6b97f-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b97f-108">備註</span><span class="sxs-lookup"><span data-stu-id="6b97f-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6b97f-109">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="6b97f-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b97f-110">需求</span><span class="sxs-lookup"><span data-stu-id="6b97f-110">Requirements</span></span>  
 <span data-ttu-id="6b97f-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6b97f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b97f-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b97f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b97f-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b97f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b97f-114">**.NET 框架版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b97f-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b97f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b97f-115">See also</span></span>

- [<span data-ttu-id="6b97f-116">ICorDebugProcess6 介面</span><span class="sxs-lookup"><span data-stu-id="6b97f-116">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="6b97f-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6b97f-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
