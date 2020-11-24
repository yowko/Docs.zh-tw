---
title: ICorDebugAppDomain::GetProcess 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebugAppDomain interface [.NET Framework debugging]
- ICorDebugAppDomain::GetProcess method [.NET Framework debugging]
ms.assetid: 9d0b9628-a91c-40d0-b9bc-00b34a396b8f
topic_type:
- apiref
ms.openlocfilehash: 6521341499df52c1851401f3f2f5c48a3b68ccd3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675954"
---
# <a name="icordebugappdomaingetprocess-method"></a><span data-ttu-id="7e218-102">ICorDebugAppDomain::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="7e218-102">ICorDebugAppDomain::GetProcess Method</span></span>

<span data-ttu-id="7e218-103">取得包含應用程式域的進程。</span><span class="sxs-lookup"><span data-stu-id="7e218-103">Gets the process containing the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e218-104">語法</span><span class="sxs-lookup"><span data-stu-id="7e218-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e218-105">參數</span><span class="sxs-lookup"><span data-stu-id="7e218-105">Parameters</span></span>  

 `ppProcess`  
 <span data-ttu-id="7e218-106">擴展代表進程之 ICorDebugProcess 物件位址的指標。</span><span class="sxs-lookup"><span data-stu-id="7e218-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e218-107">需求</span><span class="sxs-lookup"><span data-stu-id="7e218-107">Requirements</span></span>  

 <span data-ttu-id="7e218-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7e218-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e218-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e218-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e218-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e218-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e218-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e218-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
