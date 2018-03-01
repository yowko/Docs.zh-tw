---
title: "ICorDebugChain::EnumerateFrames 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugChain.EnumerateFrames
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d9df99c239568948c04f61ca4ec5e2b9207930f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchainenumerateframes-method"></a><span data-ttu-id="39df8-102">ICorDebugChain::EnumerateFrames 方法</span><span class="sxs-lookup"><span data-stu-id="39df8-102">ICorDebugChain::EnumerateFrames Method</span></span>
<span data-ttu-id="39df8-103">取得列舉值，其中包含鏈結中的所有受管理的堆疊框架開頭為最新的框架。</span><span class="sxs-lookup"><span data-stu-id="39df8-103">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39df8-104">語法</span><span class="sxs-lookup"><span data-stu-id="39df8-104">Syntax</span></span>  
  
```  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="39df8-105">參數</span><span class="sxs-lookup"><span data-stu-id="39df8-105">Parameters</span></span>  
 `ppFrames`  
 <span data-ttu-id="39df8-106">[out]ICorDebugFrameEnum 堆疊框架的列舉值物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="39df8-106">[out] A pointer to the address of an ICorDebugFrameEnum object that is the enumerator for the stack frames.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39df8-107">備註</span><span class="sxs-lookup"><span data-stu-id="39df8-107">Remarks</span></span>  
 <span data-ttu-id="39df8-108">鏈結代表執行緒的實際呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="39df8-108">The chain represents the physical call stack for the thread.</span></span>  
  
 <span data-ttu-id="39df8-109">`EnumerateFrames`方法應該呼叫只會針對受管理的鏈結。</span><span class="sxs-lookup"><span data-stu-id="39df8-109">The `EnumerateFrames` method should be called only for managed chains.</span></span> <span data-ttu-id="39df8-110">偵錯 API 不提供方法以取得包含 unmanaged 鏈結中的框架。</span><span class="sxs-lookup"><span data-stu-id="39df8-110">The debugging API does not provide methods for obtaining frames contained in unmanaged chains.</span></span> <span data-ttu-id="39df8-111">偵錯工具必須使用其他方法來取得這項資訊。</span><span class="sxs-lookup"><span data-stu-id="39df8-111">The debugger must use other means to obtain this information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39df8-112">需求</span><span class="sxs-lookup"><span data-stu-id="39df8-112">Requirements</span></span>  
 <span data-ttu-id="39df8-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="39df8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39df8-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39df8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39df8-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39df8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39df8-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39df8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
