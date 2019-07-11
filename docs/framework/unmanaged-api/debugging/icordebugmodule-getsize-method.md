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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46ee21a9fd7b9267672a14107c1706af5d5cdcc5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763580"
---
# <a name="icordebugmodulegetsize-method"></a><span data-ttu-id="b38c9-102">ICorDebugModule::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="b38c9-102">ICorDebugModule::GetSize Method</span></span>
<span data-ttu-id="b38c9-103">取得大小，以位元組為單位的模組。</span><span class="sxs-lookup"><span data-stu-id="b38c9-103">Gets the size, in bytes, of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b38c9-104">語法</span><span class="sxs-lookup"><span data-stu-id="b38c9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
    [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b38c9-105">參數</span><span class="sxs-lookup"><span data-stu-id="b38c9-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="b38c9-106">[out]該模組，以位元組為單位的大小。</span><span class="sxs-lookup"><span data-stu-id="b38c9-106">[out] The size of the module in bytes.</span></span>  
  
 <span data-ttu-id="b38c9-107">如果從原生映像產生器 (NGen.exe) 產生的模組，模組的大小會是零。</span><span class="sxs-lookup"><span data-stu-id="b38c9-107">If the module was produced from the native image generator (NGen.exe), the size of the module will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b38c9-108">需求</span><span class="sxs-lookup"><span data-stu-id="b38c9-108">Requirements</span></span>  
 <span data-ttu-id="b38c9-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b38c9-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b38c9-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b38c9-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b38c9-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b38c9-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b38c9-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b38c9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
