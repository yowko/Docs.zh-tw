---
title: ICorDebugProcess5::EnableNGENPolicy 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5::EnableNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnableNGENPolicy
helpviewer_keywords:
- ICorDebugProcess5::EnableNGENPolicy method [.NET Framework debugging]
- EnableNGENPolicy method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 3b8e15ca-3c72-4685-a937-da4c739cb9e9
topic_type:
- apiref
ms.openlocfilehash: fa3cbfee0359b8477f9efe88fe72837b86611bf7
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212798"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a><span data-ttu-id="74ebc-102">ICorDebugProcess5::EnableNGENPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="74ebc-102">ICorDebugProcess5::EnableNGENPolicy Method</span></span>
<span data-ttu-id="74ebc-103">設定值，決定應用程式在 managed 偵錯工具下執行時，載入原生影像的方式。</span><span class="sxs-lookup"><span data-stu-id="74ebc-103">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74ebc-104">語法</span><span class="sxs-lookup"><span data-stu-id="74ebc-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74ebc-105">參數</span><span class="sxs-lookup"><span data-stu-id="74ebc-105">Parameters</span></span>  
 `ePolicy`  
 <span data-ttu-id="74ebc-106">在[CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md)常數，可決定應用程式在 managed 偵錯工具下執行時，載入原生影像的方式。</span><span class="sxs-lookup"><span data-stu-id="74ebc-106">[in] A [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md) constant that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74ebc-107">備註</span><span class="sxs-lookup"><span data-stu-id="74ebc-107">Remarks</span></span>  
 <span data-ttu-id="74ebc-108">如果已成功設定原則，則方法會傳回 `S_OK` 。</span><span class="sxs-lookup"><span data-stu-id="74ebc-108">If the policy is set successfully, the method returns `S_OK`.</span></span> <span data-ttu-id="74ebc-109">如果超出 `ePolicy` [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md)所定義之列舉值的範圍，此方法會傳回 `E_INVALIDARG` ，且方法呼叫不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="74ebc-109">If `ePolicy` is outside the range of the enumerated values defined by [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md), the method returns `E_INVALIDARG` and the method call has no effect.</span></span> <span data-ttu-id="74ebc-110">如果無法更新原生映射產生器（Ngen.exe）的原則，則方法會傳回 `E_FAIL` 。</span><span class="sxs-lookup"><span data-stu-id="74ebc-110">If the policy of the Native Image Generator (Ngen.exe) cannot be updated, the method returns `E_FAIL`.</span></span>  
  
 <span data-ttu-id="74ebc-111">在 `ICorDebugProcess5::EnableNGenPolicy` 進程的存留期間內，任何時間都可以呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="74ebc-111">The `ICorDebugProcess5::EnableNGenPolicy` method can be called at any time during the lifetime of the process.</span></span> <span data-ttu-id="74ebc-112">原則會在設定原則之後載入的任何模組生效。</span><span class="sxs-lookup"><span data-stu-id="74ebc-112">The policy is in effect for any modules that are loaded after the policy is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74ebc-113">需求</span><span class="sxs-lookup"><span data-stu-id="74ebc-113">Requirements</span></span>  
 <span data-ttu-id="74ebc-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="74ebc-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74ebc-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="74ebc-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74ebc-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74ebc-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74ebc-117">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74ebc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74ebc-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="74ebc-118">See also</span></span>

- [<span data-ttu-id="74ebc-119">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="74ebc-119">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="74ebc-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="74ebc-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="74ebc-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="74ebc-121">Debugging</span></span>](index.md)
