---
title: ICorDebugModule::GetSize 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetSize method [.NET Framework debugging]
ms.assetid: 5c68375d-145d-46ef-a7c8-2dc4257472de
topic_type:
- apiref
ms.openlocfilehash: 0cfc31839b263c2e8cf44d15439b44ffacccf5bf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709891"
---
# <a name="icordebugmodulegetsize-method"></a><span data-ttu-id="8e509-102">ICorDebugModule::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="8e509-102">ICorDebugModule::GetSize Method</span></span>

<span data-ttu-id="8e509-103">取得模組的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="8e509-103">Gets the size, in bytes, of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e509-104">語法</span><span class="sxs-lookup"><span data-stu-id="8e509-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
    [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e509-105">參數</span><span class="sxs-lookup"><span data-stu-id="8e509-105">Parameters</span></span>  

 `pcBytes`  
 <span data-ttu-id="8e509-106">擴展模組的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="8e509-106">[out] The size of the module in bytes.</span></span>  
  
 <span data-ttu-id="8e509-107">如果模組是從原生映射產生器 ( # A0) 產生，則模組的大小會是零。</span><span class="sxs-lookup"><span data-stu-id="8e509-107">If the module was produced from the native image generator (NGen.exe), the size of the module will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e509-108">需求</span><span class="sxs-lookup"><span data-stu-id="8e509-108">Requirements</span></span>  

 <span data-ttu-id="8e509-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8e509-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e509-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8e509-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8e509-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e509-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e509-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e509-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
