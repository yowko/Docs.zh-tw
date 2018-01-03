---
title: "ICorDebugAssembly::GetAppDomain 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAssembly.GetAppDomain
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAssembly::GetAppDomain
helpviewer_keywords:
- ICorDebugAssembly::GetAppDomain method [.NET Framework debugging]
- GetAppDomain method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 14e18510-23ac-4cba-9f96-c86147a2df9d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f97795568b9811d0dbf7852fd64d5256c29b8f30
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="3136d-102">ICorDebugAssembly::GetAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="3136d-102">ICorDebugAssembly::GetAppDomain Method</span></span>
<span data-ttu-id="3136d-103">取得包含這個應用程式定義域的介面指標`ICorDebugAssembly`執行個體。</span><span class="sxs-lookup"><span data-stu-id="3136d-103">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3136d-104">語法</span><span class="sxs-lookup"><span data-stu-id="3136d-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3136d-105">參數</span><span class="sxs-lookup"><span data-stu-id="3136d-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="3136d-106">[out]ICorDebugAppDomain 介面，表示應用程式定義域的位址指標。</span><span class="sxs-lookup"><span data-stu-id="3136d-106">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3136d-107">備註</span><span class="sxs-lookup"><span data-stu-id="3136d-107">Remarks</span></span>  
 <span data-ttu-id="3136d-108">如果這個組件是系統組件`GetAppDomain`會傳回 null。</span><span class="sxs-lookup"><span data-stu-id="3136d-108">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3136d-109">需求</span><span class="sxs-lookup"><span data-stu-id="3136d-109">Requirements</span></span>  
 <span data-ttu-id="3136d-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3136d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3136d-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3136d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3136d-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3136d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3136d-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3136d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
