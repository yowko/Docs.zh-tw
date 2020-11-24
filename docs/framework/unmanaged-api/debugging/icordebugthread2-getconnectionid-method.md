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
ms.openlocfilehash: 1507715e80761c871dfdb0b8d25dc708a2130678
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678684"
---
# <a name="icordebugthread2getconnectionid-method"></a><span data-ttu-id="2dcd7-102">ICorDebugThread2::GetConnectionID 方法</span><span class="sxs-lookup"><span data-stu-id="2dcd7-102">ICorDebugThread2::GetConnectionID Method</span></span>

<span data-ttu-id="2dcd7-103">取得這個 ICorDebugThread2 物件的連接識別碼。</span><span class="sxs-lookup"><span data-stu-id="2dcd7-103">Gets the connection identifier for this ICorDebugThread2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dcd7-104">語法</span><span class="sxs-lookup"><span data-stu-id="2dcd7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2dcd7-105">參數</span><span class="sxs-lookup"><span data-stu-id="2dcd7-105">Parameters</span></span>  

 `pdwConnectionId`  
 <span data-ttu-id="2dcd7-106">擴展 `CONNID` 表示連接識別碼的。</span><span class="sxs-lookup"><span data-stu-id="2dcd7-106">[out] A `CONNID` that represents the connection identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2dcd7-107">備註</span><span class="sxs-lookup"><span data-stu-id="2dcd7-107">Remarks</span></span>  

 <span data-ttu-id="2dcd7-108">`GetConnectionID` `pdwConnectionId` 如果這個執行緒不是連接的一部分，方法會在參數中傳回零。</span><span class="sxs-lookup"><span data-stu-id="2dcd7-108">The `GetConnectionID` method returns zero in the `pdwConnectionId` parameter, if this thread is not part of a connection.</span></span>  
  
 <span data-ttu-id="2dcd7-109">如果這個執行緒連接到 Microsoft SQL Server 2005 Analysis Services (SSAS) 的實例，會 `CONNID` 對應至伺服器處理序識別碼 (SPID) 。</span><span class="sxs-lookup"><span data-stu-id="2dcd7-109">If this thread is connected to an instance of Microsoft SQL Server 2005 Analysis Services (SSAS), the `CONNID` maps to a server process identifier (SPID).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2dcd7-110">需求</span><span class="sxs-lookup"><span data-stu-id="2dcd7-110">Requirements</span></span>  

 <span data-ttu-id="2dcd7-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2dcd7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2dcd7-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2dcd7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2dcd7-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2dcd7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2dcd7-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2dcd7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
