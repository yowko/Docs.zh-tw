---
title: ICorDebugAssembly::GetAppDomain 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetAppDomain
helpviewer_keywords:
- ICorDebugAssembly::GetAppDomain method [.NET Framework debugging]
- GetAppDomain method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 14e18510-23ac-4cba-9f96-c86147a2df9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4fced656168952c1064de213405147baf7856b2c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737352"
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="d9935-102">ICorDebugAssembly::GetAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="d9935-102">ICorDebugAssembly::GetAppDomain Method</span></span>
<span data-ttu-id="d9935-103">取得包含這個應用程式定義域的介面指標`ICorDebugAssembly`執行個體。</span><span class="sxs-lookup"><span data-stu-id="d9935-103">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9935-104">語法</span><span class="sxs-lookup"><span data-stu-id="d9935-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9935-105">參數</span><span class="sxs-lookup"><span data-stu-id="d9935-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="d9935-106">[out]ICorDebugAppDomain 介面，代表應用程式定義域的位址指標。</span><span class="sxs-lookup"><span data-stu-id="d9935-106">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9935-107">備註</span><span class="sxs-lookup"><span data-stu-id="d9935-107">Remarks</span></span>  
 <span data-ttu-id="d9935-108">如果這個組件是系統組件`GetAppDomain`會傳回 null。</span><span class="sxs-lookup"><span data-stu-id="d9935-108">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9935-109">需求</span><span class="sxs-lookup"><span data-stu-id="d9935-109">Requirements</span></span>  
 <span data-ttu-id="d9935-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d9935-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9935-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d9935-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d9935-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9935-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9935-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9935-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
