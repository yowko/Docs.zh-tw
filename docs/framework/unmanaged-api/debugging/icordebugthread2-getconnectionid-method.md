---
title: ICorDebugThread2::GetConnectionID 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetConnectionID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetConnectionID
helpviewer_keywords:
- ICorDebugThread2::GetConnectionID method [.NET Framework debugging]
- GetConnectionID method [.NET Framework debugging]
ms.assetid: 9c76b587-f941-4fa1-8b86-f3494fb10c8e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc4963dcf686fe62f473aea1af86868df03718df
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768963"
---
# <a name="icordebugthread2getconnectionid-method"></a><span data-ttu-id="828d6-102">ICorDebugThread2::GetConnectionID 方法</span><span class="sxs-lookup"><span data-stu-id="828d6-102">ICorDebugThread2::GetConnectionID Method</span></span>
<span data-ttu-id="828d6-103">取得這個 ICorDebugThread2 物件的連接識別碼。</span><span class="sxs-lookup"><span data-stu-id="828d6-103">Gets the connection identifier for this ICorDebugThread2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="828d6-104">語法</span><span class="sxs-lookup"><span data-stu-id="828d6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="828d6-105">參數</span><span class="sxs-lookup"><span data-stu-id="828d6-105">Parameters</span></span>  
 `pdwConnectionId`  
 <span data-ttu-id="828d6-106">[out]A`CONNID`表示的連接識別碼。</span><span class="sxs-lookup"><span data-stu-id="828d6-106">[out] A `CONNID` that represents the connection identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="828d6-107">備註</span><span class="sxs-lookup"><span data-stu-id="828d6-107">Remarks</span></span>  
 <span data-ttu-id="828d6-108">`GetConnectionID`方法會傳回零`pdwConnectionId`參數，如果這個執行緒不是連接的一部分。</span><span class="sxs-lookup"><span data-stu-id="828d6-108">The `GetConnectionID` method returns zero in the `pdwConnectionId` parameter, if this thread is not part of a connection.</span></span>  
  
 <span data-ttu-id="828d6-109">如果這個執行緒已連線到執行個體的 Microsoft SQL Server 2005 Analysis Services (SSAS)，`CONNID`對應至伺服器處理序識別碼 (SPID)。</span><span class="sxs-lookup"><span data-stu-id="828d6-109">If this thread is connected to an instance of Microsoft SQL Server 2005 Analysis Services (SSAS), the `CONNID` maps to a server process identifier (SPID).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="828d6-110">需求</span><span class="sxs-lookup"><span data-stu-id="828d6-110">Requirements</span></span>  
 <span data-ttu-id="828d6-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="828d6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="828d6-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="828d6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="828d6-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="828d6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="828d6-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="828d6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
