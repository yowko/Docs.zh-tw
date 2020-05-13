---
title: ICorDebugStringValue 介面
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue
helpviewer_keywords:
- ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: bf84d0af-53e1-4c04-bc5b-7e5f81ba2cc2
topic_type:
- apiref
ms.openlocfilehash: 5537a48fd085ce98de855fa1ec0913e2637e58e0
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83376200"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="c6430-102">ICorDebugStringValue 介面</span><span class="sxs-lookup"><span data-stu-id="c6430-102">ICorDebugStringValue Interface</span></span>
<span data-ttu-id="c6430-103">適用于字串值之 ICorDebugHeapValue 的子類別。</span><span class="sxs-lookup"><span data-stu-id="c6430-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c6430-104">方法</span><span class="sxs-lookup"><span data-stu-id="c6430-104">Methods</span></span>  
  
|<span data-ttu-id="c6430-105">方法</span><span class="sxs-lookup"><span data-stu-id="c6430-105">Method</span></span>|<span data-ttu-id="c6430-106">描述</span><span class="sxs-lookup"><span data-stu-id="c6430-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c6430-107">GetLength 方法</span><span class="sxs-lookup"><span data-stu-id="c6430-107">GetLength Method</span></span>](icordebugstringvalue-getlength-method.md)|<span data-ttu-id="c6430-108">取得這個所參考字串中的字元數 `ICorDebugStringValue` 。</span><span class="sxs-lookup"><span data-stu-id="c6430-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="c6430-109">GetString 方法</span><span class="sxs-lookup"><span data-stu-id="c6430-109">GetString Method</span></span>](icordebugstringvalue-getstring-method.md)|<span data-ttu-id="c6430-110">取得這個所參考的字串 `ICorDebugStringValue` 。</span><span class="sxs-lookup"><span data-stu-id="c6430-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6430-111">備註</span><span class="sxs-lookup"><span data-stu-id="c6430-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c6430-112">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="c6430-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6430-113">需求</span><span class="sxs-lookup"><span data-stu-id="c6430-113">Requirements</span></span>  
 <span data-ttu-id="c6430-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c6430-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6430-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6430-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6430-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6430-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6430-117">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6430-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6430-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="c6430-118">See also</span></span>

- [<span data-ttu-id="c6430-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="c6430-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
