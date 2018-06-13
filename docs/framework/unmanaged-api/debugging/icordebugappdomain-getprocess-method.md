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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d172af14aba418d6e97fe77724bf91b0eaf1c56a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403110"
---
# <a name="icordebugappdomaingetprocess-method"></a><span data-ttu-id="9d5cb-102">ICorDebugAppDomain::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="9d5cb-102">ICorDebugAppDomain::GetProcess Method</span></span>
<span data-ttu-id="9d5cb-103">取得包含在應用程式定義域的處理序。</span><span class="sxs-lookup"><span data-stu-id="9d5cb-103">Gets the process containing the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d5cb-104">語法</span><span class="sxs-lookup"><span data-stu-id="9d5cb-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d5cb-105">參數</span><span class="sxs-lookup"><span data-stu-id="9d5cb-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="9d5cb-106">[out]ICorDebugProcess 物件代表處理程序的位址指標。</span><span class="sxs-lookup"><span data-stu-id="9d5cb-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d5cb-107">需求</span><span class="sxs-lookup"><span data-stu-id="9d5cb-107">Requirements</span></span>  
 <span data-ttu-id="9d5cb-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9d5cb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d5cb-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d5cb-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d5cb-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d5cb-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d5cb-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d5cb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
