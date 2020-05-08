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
ms.openlocfilehash: b263fed7db5cb2ef687da45f8cbc99a02e1e3ea2
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976131"
---
# <a name="icordebugevalnewstring-method"></a><span data-ttu-id="40577-102">ICorDebugEval::NewString 方法</span><span class="sxs-lookup"><span data-stu-id="40577-102">ICorDebugEval::NewString Method</span></span>
<span data-ttu-id="40577-103">使用指定的內容，配置新的字串實例。</span><span class="sxs-lookup"><span data-stu-id="40577-103">Allocates a new string instance with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40577-104">語法</span><span class="sxs-lookup"><span data-stu-id="40577-104">Syntax</span></span>  
  
```cpp  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40577-105">參數</span><span class="sxs-lookup"><span data-stu-id="40577-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="40577-106">在字串內容的指標。</span><span class="sxs-lookup"><span data-stu-id="40577-106">[in] Pointer to the contents for the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40577-107">備註</span><span class="sxs-lookup"><span data-stu-id="40577-107">Remarks</span></span>  
 <span data-ttu-id="40577-108">此字串一律會線上程目前執行所在的應用程式域中建立。</span><span class="sxs-lookup"><span data-stu-id="40577-108">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40577-109">需求</span><span class="sxs-lookup"><span data-stu-id="40577-109">Requirements</span></span>  
 <span data-ttu-id="40577-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="40577-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40577-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="40577-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40577-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40577-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40577-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40577-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
