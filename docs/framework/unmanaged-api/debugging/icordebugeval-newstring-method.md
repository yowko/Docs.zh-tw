---
title: ICorDebugEval::NewString 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewString
helpviewer_keywords:
- NewString method [.NET Framework debugging]
- ICorDebugEval::NewString method [.NET Framework debugging]
ms.assetid: 29e7a14b-d50e-4852-bfda-011b76c0c9ee
topic_type:
- apiref
ms.openlocfilehash: c2d29a0cc344539bf515793c071fe839aa441ebc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729716"
---
# <a name="icordebugevalnewstring-method"></a><span data-ttu-id="809b2-102">ICorDebugEval::NewString 方法</span><span class="sxs-lookup"><span data-stu-id="809b2-102">ICorDebugEval::NewString Method</span></span>

<span data-ttu-id="809b2-103">使用指定的內容配置新的字串實例。</span><span class="sxs-lookup"><span data-stu-id="809b2-103">Allocates a new string instance with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="809b2-104">語法</span><span class="sxs-lookup"><span data-stu-id="809b2-104">Syntax</span></span>  
  
```cpp  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="809b2-105">參數</span><span class="sxs-lookup"><span data-stu-id="809b2-105">Parameters</span></span>  

 `string`  
 <span data-ttu-id="809b2-106">在字串內容的指標。</span><span class="sxs-lookup"><span data-stu-id="809b2-106">[in] Pointer to the contents for the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="809b2-107">備註</span><span class="sxs-lookup"><span data-stu-id="809b2-107">Remarks</span></span>  

 <span data-ttu-id="809b2-108">字串一律會建立線上程目前執行所在的應用程式域中。</span><span class="sxs-lookup"><span data-stu-id="809b2-108">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="809b2-109">需求</span><span class="sxs-lookup"><span data-stu-id="809b2-109">Requirements</span></span>  

 <span data-ttu-id="809b2-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="809b2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="809b2-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="809b2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="809b2-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="809b2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="809b2-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="809b2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
