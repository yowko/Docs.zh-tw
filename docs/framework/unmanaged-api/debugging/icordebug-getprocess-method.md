---
title: "ICorDebug::GetProcess 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.GetProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::GetProcess method [.NET Framework debugging]
ms.assetid: 10a40ba0-1b65-4721-bd11-cf12d57b280d
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 189aab8a1e640d822dc8c45098b3af7cb81e916c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebuggetprocess-method"></a><span data-ttu-id="70ca1-102">ICorDebug::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="70ca1-102">ICorDebug::GetProcess Method</span></span>
<span data-ttu-id="70ca1-103">取得指定之處理序 」 ICorDebugProcess 」 執行個體的指標。</span><span class="sxs-lookup"><span data-stu-id="70ca1-103">Gets a pointer to the "ICorDebugProcess" instance for the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70ca1-104">語法</span><span class="sxs-lookup"><span data-stu-id="70ca1-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [in] DWORD               dwProcessId,  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="70ca1-105">參數</span><span class="sxs-lookup"><span data-stu-id="70ca1-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="70ca1-106">[in]處理序的識別碼。</span><span class="sxs-lookup"><span data-stu-id="70ca1-106">[in] The ID of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="70ca1-107">[out]位址指標`ICorDebugProcess`指定的處理序的執行個體。</span><span class="sxs-lookup"><span data-stu-id="70ca1-107">[out] A pointer to the address of a `ICorDebugProcess` instance for the specified process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70ca1-108">需求</span><span class="sxs-lookup"><span data-stu-id="70ca1-108">Requirements</span></span>  
 <span data-ttu-id="70ca1-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="70ca1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70ca1-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70ca1-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70ca1-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70ca1-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70ca1-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70ca1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70ca1-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70ca1-113">See Also</span></span>  
 [<span data-ttu-id="70ca1-114">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="70ca1-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
