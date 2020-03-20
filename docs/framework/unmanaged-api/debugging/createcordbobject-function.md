---
title: CreateCordbObject 函式
ms.date: 03/30/2017
api_name:
- CreateCoredbObject
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type:
- apiref
ms.openlocfilehash: 2716adcc8c79c8003202561ea2011c2469a6bc5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179224"
---
# <a name="createcordbobject-function"></a><span data-ttu-id="23cfd-102">CreateCordbObject 函式</span><span class="sxs-lookup"><span data-stu-id="23cfd-102">CreateCordbObject Function</span></span>
<span data-ttu-id="23cfd-103">創建調試器介面 （[ICorDebug](icordebug-interface.md)）， 提供在遠端進程上具現化託管調試會話的功能。</span><span class="sxs-lookup"><span data-stu-id="23cfd-103">Creates a debugger interface ([ICorDebug](icordebug-interface.md)) that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23cfd-104">語法</span><span class="sxs-lookup"><span data-stu-id="23cfd-104">Syntax</span></span>  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23cfd-105">參數</span><span class="sxs-lookup"><span data-stu-id="23cfd-105">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="23cfd-106">[in] 目標處理序的偵錯工具版本。</span><span class="sxs-lookup"><span data-stu-id="23cfd-106">[in] Debugger version of the target process.</span></span> <span data-ttu-id="23cfd-107">這個參數必須是 CorDebugVersion_2_0，才能進行遠端偵錯。</span><span class="sxs-lookup"><span data-stu-id="23cfd-107">This parameter must be CorDebugVersion_2_0 for remote debugging.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="23cfd-108">[出]指向將強制轉換為[ICorDebug](icordebug-interface.md)介面並返回的物件的指標。</span><span class="sxs-lookup"><span data-stu-id="23cfd-108">[out] Pointer to a pointer to an object that will be cast to an [ICorDebug](icordebug-interface.md) interface and returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23cfd-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="23cfd-109">Return Value</span></span>  
 <span data-ttu-id="23cfd-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="23cfd-110">S_OK</span></span>  
 <span data-ttu-id="23cfd-111">已成功確定處理序中的 CLR 數目，並且已正確填入對應的控制代碼和路徑陣列。</span><span class="sxs-lookup"><span data-stu-id="23cfd-111">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="23cfd-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="23cfd-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="23cfd-113">`ppCordb` 為 null，或 `iDebuggerVersion` 不是 CorDebugVersion_2_0。</span><span class="sxs-lookup"><span data-stu-id="23cfd-113">`ppCordb` is null, or `iDebuggerVersion` is not CorDebugVersion_2_0.</span></span>  
  
 <span data-ttu-id="23cfd-114">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="23cfd-114">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="23cfd-115">無法為 `ppCordb` 配置足夠的記憶體。</span><span class="sxs-lookup"><span data-stu-id="23cfd-115">Unable to allocate enough memory for `ppCordb`</span></span>  
  
 <span data-ttu-id="23cfd-116">E_FAIL (或其他 E_ 傳回碼)</span><span class="sxs-lookup"><span data-stu-id="23cfd-116">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="23cfd-117">其他失敗。</span><span class="sxs-lookup"><span data-stu-id="23cfd-117">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23cfd-118">備註</span><span class="sxs-lookup"><span data-stu-id="23cfd-118">Remarks</span></span>  
 <span data-ttu-id="23cfd-119">返回的`ppCordb` [ICorDebug](icordebug-interface.md)介面是所有託管調試服務的頂級調試介面。</span><span class="sxs-lookup"><span data-stu-id="23cfd-119">The [ICorDebug](icordebug-interface.md) interface that is returned in `ppCordb` is the top-level debugging interface for all managed debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23cfd-120">需求</span><span class="sxs-lookup"><span data-stu-id="23cfd-120">Requirements</span></span>  
 <span data-ttu-id="23cfd-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="23cfd-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23cfd-122">**標題：** 核心Clr遠端偵錯介面.h</span><span class="sxs-lookup"><span data-stu-id="23cfd-122">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="23cfd-123">**資料庫：** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="23cfd-123">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="23cfd-124">**.NET 框架版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="23cfd-124">**.NET Framework Versions:** 3.5 SP1</span></span>
