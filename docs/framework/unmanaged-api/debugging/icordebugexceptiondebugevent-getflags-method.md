---
title: ICorDebugExceptionDebugEvent::GetFlags 方法
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
ms.openlocfilehash: 02a20b54b7fecc711bda010c6916fe036cf20dd9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729599"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="10255-102">ICorDebugExceptionDebugEvent::GetFlags 方法</span><span class="sxs-lookup"><span data-stu-id="10255-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>

<span data-ttu-id="10255-103">取得指出例外狀況是否可以被攔截的旗標。</span><span class="sxs-lookup"><span data-stu-id="10255-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10255-104">語法</span><span class="sxs-lookup"><span data-stu-id="10255-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10255-105">參數</span><span class="sxs-lookup"><span data-stu-id="10255-105">Parameters</span></span>  

 `pdwFlags`  
 <span data-ttu-id="10255-106">擴展 [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) 值的指標，指出是否可以攔截例外狀況。</span><span class="sxs-lookup"><span data-stu-id="10255-106">[out] A pointer to a [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10255-107">備註</span><span class="sxs-lookup"><span data-stu-id="10255-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="10255-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="10255-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10255-109">需求</span><span class="sxs-lookup"><span data-stu-id="10255-109">Requirements</span></span>  

 <span data-ttu-id="10255-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="10255-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10255-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10255-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10255-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10255-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10255-113">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10255-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10255-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10255-114">See also</span></span>

- [<span data-ttu-id="10255-115">ICorDebugExceptionDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="10255-115">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="10255-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="10255-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
