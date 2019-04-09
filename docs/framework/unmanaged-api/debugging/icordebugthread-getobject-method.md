---
title: ICorDebugThread::GetObject 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetObject method [.NET Framework debugging]
ms.assetid: 1590febe-96c2-4046-97db-d81d81d67e01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7fa90aff73d94baf2cbf7d01f41710cb2aa10213
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178733"
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="22ec0-102">ICorDebugThread::GetObject 方法</span><span class="sxs-lookup"><span data-stu-id="22ec0-102">ICorDebugThread::GetObject Method</span></span>
<span data-ttu-id="22ec0-103">取得 common language runtime (CLR) 執行緒的介面指標。</span><span class="sxs-lookup"><span data-stu-id="22ec0-103">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22ec0-104">語法</span><span class="sxs-lookup"><span data-stu-id="22ec0-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22ec0-105">參數</span><span class="sxs-lookup"><span data-stu-id="22ec0-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="22ec0-106">[out]ICorDebugValue 介面物件，表示 CLR 執行緒的位址指標。</span><span class="sxs-lookup"><span data-stu-id="22ec0-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22ec0-107">需求</span><span class="sxs-lookup"><span data-stu-id="22ec0-107">Requirements</span></span>  
 <span data-ttu-id="22ec0-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="22ec0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22ec0-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="22ec0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="22ec0-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22ec0-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="22ec0-111">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="22ec0-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="22ec0-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22ec0-112">See also</span></span>

- <xref:System.Threading.Thread>
