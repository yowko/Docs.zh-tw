---
title: ICorDebug::GetProcess 方法
ms.date: 03/30/2017
api_name:
- ICorDebug.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::GetProcess method [.NET Framework debugging]
ms.assetid: 10a40ba0-1b65-4721-bd11-cf12d57b280d
topic_type:
- apiref
ms.openlocfilehash: 46c2b444984c5a0062f1cfbc0cd29dbe409b16fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723437"
---
# <a name="icordebuggetprocess-method"></a><span data-ttu-id="5030b-102">ICorDebug::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="5030b-102">ICorDebug::GetProcess Method</span></span>

<span data-ttu-id="5030b-103">取得指定進程之 "ICorDebugProcess" 實例的指標。</span><span class="sxs-lookup"><span data-stu-id="5030b-103">Gets a pointer to the "ICorDebugProcess" instance for the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5030b-104">語法</span><span class="sxs-lookup"><span data-stu-id="5030b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [in] DWORD               dwProcessId,  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5030b-105">參數</span><span class="sxs-lookup"><span data-stu-id="5030b-105">Parameters</span></span>  

 `dwProcessId`  
 <span data-ttu-id="5030b-106">在進程的識別碼。</span><span class="sxs-lookup"><span data-stu-id="5030b-106">[in] The ID of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="5030b-107">擴展指定之進程的實例位址指標 `ICorDebugProcess` 。</span><span class="sxs-lookup"><span data-stu-id="5030b-107">[out] A pointer to the address of a `ICorDebugProcess` instance for the specified process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5030b-108">需求</span><span class="sxs-lookup"><span data-stu-id="5030b-108">Requirements</span></span>  

 <span data-ttu-id="5030b-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5030b-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5030b-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5030b-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5030b-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5030b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5030b-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5030b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5030b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5030b-113">See also</span></span>

- [<span data-ttu-id="5030b-114">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="5030b-114">ICorDebug Interface</span></span>](icordebug-interface.md)
