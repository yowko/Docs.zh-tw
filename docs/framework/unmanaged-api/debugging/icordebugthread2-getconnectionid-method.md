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
ms.openlocfilehash: 1c0e76b179854a380e66ac9daedffa8ccf4aa4ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422710"
---
# <a name="icordebugthread2getconnectionid-method"></a><span data-ttu-id="02d6a-102">ICorDebugThread2::GetConnectionID 方法</span><span class="sxs-lookup"><span data-stu-id="02d6a-102">ICorDebugThread2::GetConnectionID Method</span></span>
<span data-ttu-id="02d6a-103">取得此 ICorDebugThread2 物件的連接識別碼。</span><span class="sxs-lookup"><span data-stu-id="02d6a-103">Gets the connection identifier for this ICorDebugThread2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02d6a-104">語法</span><span class="sxs-lookup"><span data-stu-id="02d6a-104">Syntax</span></span>  
  
```  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="02d6a-105">參數</span><span class="sxs-lookup"><span data-stu-id="02d6a-105">Parameters</span></span>  
 `pdwConnectionId`  
 <span data-ttu-id="02d6a-106">[out]A`CONNID`表示連接識別碼。</span><span class="sxs-lookup"><span data-stu-id="02d6a-106">[out] A `CONNID` that represents the connection identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02d6a-107">備註</span><span class="sxs-lookup"><span data-stu-id="02d6a-107">Remarks</span></span>  
 <span data-ttu-id="02d6a-108">`GetConnectionID`方法會傳回零`pdwConnectionId`參數，如果這個執行緒不是連接的一部分。</span><span class="sxs-lookup"><span data-stu-id="02d6a-108">The `GetConnectionID` method returns zero in the `pdwConnectionId` parameter, if this thread is not part of a connection.</span></span>  
  
 <span data-ttu-id="02d6a-109">如果這個執行緒已連線到執行個體的 Microsoft SQL Server 2005 Analysis Services (SSAS)，`CONNID`對應至伺服器處理序識別碼 (SPID)。</span><span class="sxs-lookup"><span data-stu-id="02d6a-109">If this thread is connected to an instance of Microsoft SQL Server 2005 Analysis Services (SSAS), the `CONNID` maps to a server process identifier (SPID).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02d6a-110">需求</span><span class="sxs-lookup"><span data-stu-id="02d6a-110">Requirements</span></span>  
 <span data-ttu-id="02d6a-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="02d6a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02d6a-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="02d6a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="02d6a-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02d6a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02d6a-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02d6a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
