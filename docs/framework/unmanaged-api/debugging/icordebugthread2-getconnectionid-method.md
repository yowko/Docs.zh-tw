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
ms.openlocfilehash: c630daa50d465622c421381ac080eaa8d9d8d01d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379069"
---
# <a name="icordebugthread2getconnectionid-method"></a><span data-ttu-id="3217e-102">ICorDebugThread2::GetConnectionID 方法</span><span class="sxs-lookup"><span data-stu-id="3217e-102">ICorDebugThread2::GetConnectionID Method</span></span>
<span data-ttu-id="3217e-103">取得這個 ICorDebugThread2 物件的連接識別碼。</span><span class="sxs-lookup"><span data-stu-id="3217e-103">Gets the connection identifier for this ICorDebugThread2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3217e-104">語法</span><span class="sxs-lookup"><span data-stu-id="3217e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3217e-105">參數</span><span class="sxs-lookup"><span data-stu-id="3217e-105">Parameters</span></span>  
 `pdwConnectionId`  
 <span data-ttu-id="3217e-106">脫銷`CONNID`，表示連接識別碼。</span><span class="sxs-lookup"><span data-stu-id="3217e-106">[out] A `CONNID` that represents the connection identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3217e-107">備註</span><span class="sxs-lookup"><span data-stu-id="3217e-107">Remarks</span></span>  
 <span data-ttu-id="3217e-108">`GetConnectionID` `pdwConnectionId` 如果這個執行緒不是連接的一部分，方法會在參數中傳回零。</span><span class="sxs-lookup"><span data-stu-id="3217e-108">The `GetConnectionID` method returns zero in the `pdwConnectionId` parameter, if this thread is not part of a connection.</span></span>  
  
 <span data-ttu-id="3217e-109">如果這個執行緒連接到 Microsoft SQL Server 2005 Analysis Services （SSAS）的實例，則會 `CONNID` 對應到伺服器處理序識別碼（SPID）。</span><span class="sxs-lookup"><span data-stu-id="3217e-109">If this thread is connected to an instance of Microsoft SQL Server 2005 Analysis Services (SSAS), the `CONNID` maps to a server process identifier (SPID).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3217e-110">需求</span><span class="sxs-lookup"><span data-stu-id="3217e-110">Requirements</span></span>  
 <span data-ttu-id="3217e-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3217e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3217e-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3217e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3217e-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3217e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3217e-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3217e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
