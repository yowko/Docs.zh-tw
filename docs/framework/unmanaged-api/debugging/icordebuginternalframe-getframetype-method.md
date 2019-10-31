---
title: ICorDebugInternalFrame::GetFrameType 方法
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame.GetFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame::GetFrameType
helpviewer_keywords:
- GetFrameType method [.NET Framework debugging]
- ICorDebugInternalFrame::GetFrameType method [.NET Framework debugging]
ms.assetid: da278a29-dc2e-4bf7-96ce-801bdc4d7025
topic_type:
- apiref
ms.openlocfilehash: b7a33fd6e2178e0e9188b81f516b231702fb6460
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122720"
---
# <a name="icordebuginternalframegetframetype-method"></a><span data-ttu-id="9e9e9-102">ICorDebugInternalFrame::GetFrameType 方法</span><span class="sxs-lookup"><span data-stu-id="9e9e9-102">ICorDebugInternalFrame::GetFrameType Method</span></span>
<span data-ttu-id="9e9e9-103">取得此內部框架的類型。</span><span class="sxs-lookup"><span data-stu-id="9e9e9-103">Gets the type of this internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e9e9-104">語法</span><span class="sxs-lookup"><span data-stu-id="9e9e9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e9e9-105">參數</span><span class="sxs-lookup"><span data-stu-id="9e9e9-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="9e9e9-106">脫銷CorDebugInternalFrameType 列舉值的指標，指出這個 `ICorDebugInternalFrame` 物件所表示之內部框架的類型。</span><span class="sxs-lookup"><span data-stu-id="9e9e9-106">[out] A pointer to a value of the CorDebugInternalFrameType enumeration that indicates the type of internal frame represented by this `ICorDebugInternalFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e9e9-107">備註</span><span class="sxs-lookup"><span data-stu-id="9e9e9-107">Remarks</span></span>  
 <span data-ttu-id="9e9e9-108">內部框架類型永遠不會 STUBFRAME_NONE。</span><span class="sxs-lookup"><span data-stu-id="9e9e9-108">The internal frame type will never be STUBFRAME_NONE.</span></span> <span data-ttu-id="9e9e9-109">偵錯工具應該會正常地忽略無法辨識的內部框架類型。</span><span class="sxs-lookup"><span data-stu-id="9e9e9-109">Debuggers should gracefully ignore unrecognized internal frame types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e9e9-110">需求</span><span class="sxs-lookup"><span data-stu-id="9e9e9-110">Requirements</span></span>  
 <span data-ttu-id="9e9e9-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9e9e9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e9e9-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e9e9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e9e9-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e9e9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e9e9-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e9e9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
