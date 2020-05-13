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
ms.openlocfilehash: 6b598352f734cf47514a82de1d0fca65d430a9ab
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209964"
---
# <a name="icordebuginternalframegetframetype-method"></a><span data-ttu-id="5fc57-102">ICorDebugInternalFrame::GetFrameType 方法</span><span class="sxs-lookup"><span data-stu-id="5fc57-102">ICorDebugInternalFrame::GetFrameType Method</span></span>
<span data-ttu-id="5fc57-103">取得此內部框架的類型。</span><span class="sxs-lookup"><span data-stu-id="5fc57-103">Gets the type of this internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fc57-104">語法</span><span class="sxs-lookup"><span data-stu-id="5fc57-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fc57-105">參數</span><span class="sxs-lookup"><span data-stu-id="5fc57-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="5fc57-106">脫銷CorDebugInternalFrameType 列舉值的指標，指出這個物件所代表的內部框架類型 `ICorDebugInternalFrame` 。</span><span class="sxs-lookup"><span data-stu-id="5fc57-106">[out] A pointer to a value of the CorDebugInternalFrameType enumeration that indicates the type of internal frame represented by this `ICorDebugInternalFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fc57-107">備註</span><span class="sxs-lookup"><span data-stu-id="5fc57-107">Remarks</span></span>  
 <span data-ttu-id="5fc57-108">內部框架類型永遠不會 STUBFRAME_NONE。</span><span class="sxs-lookup"><span data-stu-id="5fc57-108">The internal frame type will never be STUBFRAME_NONE.</span></span> <span data-ttu-id="5fc57-109">偵錯工具應該會正常地忽略無法辨識的內部框架類型。</span><span class="sxs-lookup"><span data-stu-id="5fc57-109">Debuggers should gracefully ignore unrecognized internal frame types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fc57-110">需求</span><span class="sxs-lookup"><span data-stu-id="5fc57-110">Requirements</span></span>  
 <span data-ttu-id="5fc57-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5fc57-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fc57-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5fc57-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5fc57-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5fc57-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5fc57-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fc57-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
