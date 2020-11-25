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
ms.openlocfilehash: c675ba4b56cecd1990184cd2f0e805250c3dfeb7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724880"
---
# <a name="icordebuginternalframegetframetype-method"></a><span data-ttu-id="ad1d5-102">ICorDebugInternalFrame::GetFrameType 方法</span><span class="sxs-lookup"><span data-stu-id="ad1d5-102">ICorDebugInternalFrame::GetFrameType Method</span></span>

<span data-ttu-id="ad1d5-103">取得此內部框架的型別。</span><span class="sxs-lookup"><span data-stu-id="ad1d5-103">Gets the type of this internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad1d5-104">語法</span><span class="sxs-lookup"><span data-stu-id="ad1d5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad1d5-105">參數</span><span class="sxs-lookup"><span data-stu-id="ad1d5-105">Parameters</span></span>  

 `pType`  
 <span data-ttu-id="ad1d5-106">擴展CorDebugInternalFrameType 列舉值的指標，指出這個物件所表示的內部框架型別 `ICorDebugInternalFrame` 。</span><span class="sxs-lookup"><span data-stu-id="ad1d5-106">[out] A pointer to a value of the CorDebugInternalFrameType enumeration that indicates the type of internal frame represented by this `ICorDebugInternalFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad1d5-107">備註</span><span class="sxs-lookup"><span data-stu-id="ad1d5-107">Remarks</span></span>  

 <span data-ttu-id="ad1d5-108">內部畫面格類型永遠不會 STUBFRAME_NONE。</span><span class="sxs-lookup"><span data-stu-id="ad1d5-108">The internal frame type will never be STUBFRAME_NONE.</span></span> <span data-ttu-id="ad1d5-109">偵錯工具應該會正常地忽略無法辨識的內部畫面格類型。</span><span class="sxs-lookup"><span data-stu-id="ad1d5-109">Debuggers should gracefully ignore unrecognized internal frame types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad1d5-110">需求</span><span class="sxs-lookup"><span data-stu-id="ad1d5-110">Requirements</span></span>  

 <span data-ttu-id="ad1d5-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ad1d5-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad1d5-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad1d5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad1d5-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad1d5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad1d5-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad1d5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
