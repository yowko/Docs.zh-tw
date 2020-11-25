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
ms.openlocfilehash: e3dfd3cae83c7891d246ff3a81427c161cc0e2d1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731384"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a><span data-ttu-id="fa3b2-102">ICorDebugProcess5::EnableNGENPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="fa3b2-102">ICorDebugProcess5::EnableNGENPolicy Method</span></span>

<span data-ttu-id="fa3b2-103">設定值，這個值會決定應用程式如何在 managed 偵錯工具下執行時載入原生映射。</span><span class="sxs-lookup"><span data-stu-id="fa3b2-103">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa3b2-104">語法</span><span class="sxs-lookup"><span data-stu-id="fa3b2-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa3b2-105">參數</span><span class="sxs-lookup"><span data-stu-id="fa3b2-105">Parameters</span></span>  

 `ePolicy`  
 <span data-ttu-id="fa3b2-106">在 [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md) 常數，決定應用程式如何在 managed 偵錯工具下執行時載入原生映射。</span><span class="sxs-lookup"><span data-stu-id="fa3b2-106">[in] A [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md) constant that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa3b2-107">備註</span><span class="sxs-lookup"><span data-stu-id="fa3b2-107">Remarks</span></span>  

 <span data-ttu-id="fa3b2-108">如果原則已設定成功，則方法會傳回 `S_OK` 。</span><span class="sxs-lookup"><span data-stu-id="fa3b2-108">If the policy is set successfully, the method returns `S_OK`.</span></span> <span data-ttu-id="fa3b2-109">如果超出 `ePolicy` [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md)所定義之列舉值的範圍，則方法會傳回 `E_INVALIDARG` ，而且方法呼叫不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="fa3b2-109">If `ePolicy` is outside the range of the enumerated values defined by [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md), the method returns `E_INVALIDARG` and the method call has no effect.</span></span> <span data-ttu-id="fa3b2-110">如果無法更新原生映射產生器 ( # A0) 的原則，則方法會傳回 `E_FAIL` 。</span><span class="sxs-lookup"><span data-stu-id="fa3b2-110">If the policy of the Native Image Generator (Ngen.exe) cannot be updated, the method returns `E_FAIL`.</span></span>  
  
 <span data-ttu-id="fa3b2-111">在 `ICorDebugProcess5::EnableNGenPolicy` 進程的存留期內，您隨時都可以呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="fa3b2-111">The `ICorDebugProcess5::EnableNGenPolicy` method can be called at any time during the lifetime of the process.</span></span> <span data-ttu-id="fa3b2-112">原則適用于設定原則之後所載入的任何模組。</span><span class="sxs-lookup"><span data-stu-id="fa3b2-112">The policy is in effect for any modules that are loaded after the policy is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa3b2-113">需求</span><span class="sxs-lookup"><span data-stu-id="fa3b2-113">Requirements</span></span>  

 <span data-ttu-id="fa3b2-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fa3b2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa3b2-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa3b2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa3b2-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa3b2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa3b2-117">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa3b2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa3b2-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa3b2-118">See also</span></span>

- [<span data-ttu-id="fa3b2-119">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="fa3b2-119">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="fa3b2-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="fa3b2-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="fa3b2-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="fa3b2-121">Debugging</span></span>](index.md)
