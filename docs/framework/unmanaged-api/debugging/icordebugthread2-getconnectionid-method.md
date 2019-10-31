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
ms.openlocfilehash: a81842132769934a6f5f34e6dc462bba77b3854a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138680"
---
# <a name="icordebugthread2getconnectionid-method"></a><span data-ttu-id="f15be-102">ICorDebugThread2::GetConnectionID 方法</span><span class="sxs-lookup"><span data-stu-id="f15be-102">ICorDebugThread2::GetConnectionID Method</span></span>
<span data-ttu-id="f15be-103">取得這個 ICorDebugThread2 物件的連接識別碼。</span><span class="sxs-lookup"><span data-stu-id="f15be-103">Gets the connection identifier for this ICorDebugThread2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f15be-104">語法</span><span class="sxs-lookup"><span data-stu-id="f15be-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f15be-105">參數</span><span class="sxs-lookup"><span data-stu-id="f15be-105">Parameters</span></span>  
 `pdwConnectionId`  
 <span data-ttu-id="f15be-106">脫銷表示連接識別碼的 `CONNID`。</span><span class="sxs-lookup"><span data-stu-id="f15be-106">[out] A `CONNID` that represents the connection identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f15be-107">備註</span><span class="sxs-lookup"><span data-stu-id="f15be-107">Remarks</span></span>  
 <span data-ttu-id="f15be-108">如果這個執行緒不是連接的一部分，`GetConnectionID` 方法會在 `pdwConnectionId` 參數中傳回零。</span><span class="sxs-lookup"><span data-stu-id="f15be-108">The `GetConnectionID` method returns zero in the `pdwConnectionId` parameter, if this thread is not part of a connection.</span></span>  
  
 <span data-ttu-id="f15be-109">如果這個執行緒連接到 Microsoft SQL Server 2005 Analysis Services （SSAS）的實例，`CONNID` 會對應到伺服器處理序識別碼（SPID）。</span><span class="sxs-lookup"><span data-stu-id="f15be-109">If this thread is connected to an instance of Microsoft SQL Server 2005 Analysis Services (SSAS), the `CONNID` maps to a server process identifier (SPID).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f15be-110">需求</span><span class="sxs-lookup"><span data-stu-id="f15be-110">Requirements</span></span>  
 <span data-ttu-id="f15be-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f15be-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f15be-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f15be-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f15be-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f15be-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f15be-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f15be-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
