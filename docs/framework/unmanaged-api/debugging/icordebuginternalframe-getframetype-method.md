---
title: "ICorDebugInternalFrame::GetFrameType 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugInternalFrame.GetFrameType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugInternalFrame::GetFrameType
helpviewer_keywords:
- GetFrameType method [.NET Framework debugging]
- ICorDebugInternalFrame::GetFrameType method [.NET Framework debugging]
ms.assetid: da278a29-dc2e-4bf7-96ce-801bdc4d7025
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 476903ae8f1461a46d685bc3e549c3b6553d5c68
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginternalframegetframetype-method"></a><span data-ttu-id="df035-102">ICorDebugInternalFrame::GetFrameType 方法</span><span class="sxs-lookup"><span data-stu-id="df035-102">ICorDebugInternalFrame::GetFrameType Method</span></span>
<span data-ttu-id="df035-103">取得這個內部框架的類型。</span><span class="sxs-lookup"><span data-stu-id="df035-103">Gets the type of this internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df035-104">語法</span><span class="sxs-lookup"><span data-stu-id="df035-104">Syntax</span></span>  
  
```  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="df035-105">參數</span><span class="sxs-lookup"><span data-stu-id="df035-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="df035-106">[out]CorDebugInternalFrameType 列舉，指出所表示的內部框架的類型值的指標`ICorDebugInternalFrame`物件。</span><span class="sxs-lookup"><span data-stu-id="df035-106">[out] A pointer to a value of the CorDebugInternalFrameType enumeration that indicates the type of internal frame represented by this `ICorDebugInternalFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df035-107">備註</span><span class="sxs-lookup"><span data-stu-id="df035-107">Remarks</span></span>  
 <span data-ttu-id="df035-108">內部框架類型絕對不會 STUBFRAME_NONE。</span><span class="sxs-lookup"><span data-stu-id="df035-108">The internal frame type will never be STUBFRAME_NONE.</span></span> <span data-ttu-id="df035-109">偵錯工具應該依正常程序會忽略無法辨識內部框架的類型。</span><span class="sxs-lookup"><span data-stu-id="df035-109">Debuggers should gracefully ignore unrecognized internal frame types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df035-110">需求</span><span class="sxs-lookup"><span data-stu-id="df035-110">Requirements</span></span>  
 <span data-ttu-id="df035-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="df035-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df035-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="df035-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df035-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df035-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df035-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df035-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
