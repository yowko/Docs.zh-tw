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
ms.openlocfilehash: 2762d0680c5299732196cafe09f6e346e873f19a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785145"
---
# <a name="icordebuggetprocess-method"></a><span data-ttu-id="4333c-102">ICorDebug::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="4333c-102">ICorDebug::GetProcess Method</span></span>
<span data-ttu-id="4333c-103">取得指定進程之 "ICorDebugProcess" 實例的指標。</span><span class="sxs-lookup"><span data-stu-id="4333c-103">Gets a pointer to the "ICorDebugProcess" instance for the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4333c-104">語法</span><span class="sxs-lookup"><span data-stu-id="4333c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [in] DWORD               dwProcessId,  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4333c-105">參數</span><span class="sxs-lookup"><span data-stu-id="4333c-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="4333c-106">在進程的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4333c-106">[in] The ID of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="4333c-107">脫銷指定進程之 `ICorDebugProcess` 實例位址的指標。</span><span class="sxs-lookup"><span data-stu-id="4333c-107">[out] A pointer to the address of a `ICorDebugProcess` instance for the specified process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4333c-108">需求</span><span class="sxs-lookup"><span data-stu-id="4333c-108">Requirements</span></span>  
 <span data-ttu-id="4333c-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4333c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4333c-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4333c-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4333c-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4333c-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4333c-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4333c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4333c-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="4333c-113">See also</span></span>

- [<span data-ttu-id="4333c-114">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="4333c-114">ICorDebug Interface</span></span>](icordebug-interface.md)
