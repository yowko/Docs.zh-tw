---
title: ICorDebugFrame::GetCallee 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCallee
helpviewer_keywords:
- ICorDebugFrame::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 92d8136d-0436-4c7e-a6b2-80765f892a0d
topic_type:
- apiref
ms.openlocfilehash: 6347e0109f256dc46eb0140ffd1f51977c205b51
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678801"
---
# <a name="icordebugframegetcallee-method"></a><span data-ttu-id="28ad7-102">ICorDebugFrame::GetCallee 方法</span><span class="sxs-lookup"><span data-stu-id="28ad7-102">ICorDebugFrame::GetCallee Method</span></span>

<span data-ttu-id="28ad7-103">取得此框架所呼叫之目前鏈中 ICorDebugFrame 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="28ad7-103">Gets a pointer to the ICorDebugFrame object in the current chain that this frame called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28ad7-104">語法</span><span class="sxs-lookup"><span data-stu-id="28ad7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28ad7-105">參數</span><span class="sxs-lookup"><span data-stu-id="28ad7-105">Parameters</span></span>  

 `ppFrame`  
 <span data-ttu-id="28ad7-106">擴展物件位址的指標 `ICorDebugFrame` ，該物件表示所呼叫的框架。</span><span class="sxs-lookup"><span data-stu-id="28ad7-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the called frame.</span></span> <span data-ttu-id="28ad7-107">如果呼叫的框架是目前鏈中最內層的框架，則此值為 null。</span><span class="sxs-lookup"><span data-stu-id="28ad7-107">This value is null if the calling frame is the innermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28ad7-108">需求</span><span class="sxs-lookup"><span data-stu-id="28ad7-108">Requirements</span></span>  

 <span data-ttu-id="28ad7-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="28ad7-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28ad7-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="28ad7-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="28ad7-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28ad7-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28ad7-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28ad7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
