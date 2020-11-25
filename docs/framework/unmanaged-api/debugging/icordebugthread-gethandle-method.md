---
title: ICorDebugThread::GetHandle 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetHandle method [.NET Framework debugging]
ms.assetid: 172ef8c4-2ead-4cfc-bd2e-dee4fb7191cd
topic_type:
- apiref
ms.openlocfilehash: 5debd09f3ca0b4562f62913f9530cc4fa6f9110b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728026"
---
# <a name="icordebugthreadgethandle-method"></a><span data-ttu-id="b1cd9-102">ICorDebugThread::GetHandle 方法</span><span class="sxs-lookup"><span data-stu-id="b1cd9-102">ICorDebugThread::GetHandle Method</span></span>

<span data-ttu-id="b1cd9-103">取得此 ICorDebugThread 之使用中部分的目前控制碼。</span><span class="sxs-lookup"><span data-stu-id="b1cd9-103">Gets the current handle for the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1cd9-104">語法</span><span class="sxs-lookup"><span data-stu-id="b1cd9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1cd9-105">參數</span><span class="sxs-lookup"><span data-stu-id="b1cd9-105">Parameters</span></span>  

 `phThreadHandle`  
 <span data-ttu-id="b1cd9-106">擴展HTHREAD 的指標，該指標是此執行緒之使用中部分的控制碼。</span><span class="sxs-lookup"><span data-stu-id="b1cd9-106">[out] A pointer to an HTHREAD that is the handle of the active part of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1cd9-107">備註</span><span class="sxs-lookup"><span data-stu-id="b1cd9-107">Remarks</span></span>  

 <span data-ttu-id="b1cd9-108">當程式執行時，控制碼可能會變更，而執行緒的不同部分可能會有不同的控制碼。</span><span class="sxs-lookup"><span data-stu-id="b1cd9-108">The handle may change as the process executes, and may be different for different parts of the thread.</span></span>  
  
 <span data-ttu-id="b1cd9-109">這個控制碼是由偵錯工具 API 所擁有。</span><span class="sxs-lookup"><span data-stu-id="b1cd9-109">This handle is owned by the debugging API.</span></span> <span data-ttu-id="b1cd9-110">偵錯工具應該在使用之前複製它。</span><span class="sxs-lookup"><span data-stu-id="b1cd9-110">The debugger should duplicate it before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1cd9-111">需求</span><span class="sxs-lookup"><span data-stu-id="b1cd9-111">Requirements</span></span>  

 <span data-ttu-id="b1cd9-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b1cd9-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1cd9-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1cd9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1cd9-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1cd9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1cd9-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1cd9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
