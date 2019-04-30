---
title: ICorDebugModule::IsInMemory 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsInMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsInMemory
helpviewer_keywords:
- IsInMemory method [.NET Framework debugging]
- ICorDebugModule::IsInMemory method [.NET Framework debugging]
ms.assetid: 89940711-98e7-4aa6-bffc-5e39e91e1b7d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d79a8b0c3c56ffe2b8f57ec26f5942ee0d681194
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994834"
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="c3eb7-102">ICorDebugModule::IsInMemory 方法</span><span class="sxs-lookup"><span data-stu-id="c3eb7-102">ICorDebugModule::IsInMemory Method</span></span>
<span data-ttu-id="c3eb7-103">取得值，指出是否此模組只存在於記憶體。</span><span class="sxs-lookup"><span data-stu-id="c3eb7-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3eb7-104">語法</span><span class="sxs-lookup"><span data-stu-id="c3eb7-104">Syntax</span></span>  
  
```  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3eb7-105">參數</span><span class="sxs-lookup"><span data-stu-id="c3eb7-105">Parameters</span></span>  
 `pInMemory`  
 <span data-ttu-id="c3eb7-106">[out]`true`如果此模組只存在於記憶體中; 否則`false`。</span><span class="sxs-lookup"><span data-stu-id="c3eb7-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3eb7-107">備註</span><span class="sxs-lookup"><span data-stu-id="c3eb7-107">Remarks</span></span>  
 <span data-ttu-id="c3eb7-108">Common language runtime (CLR) 支援從未經處理的資料流的位元組的模組的載入。</span><span class="sxs-lookup"><span data-stu-id="c3eb7-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="c3eb7-109">這類模組稱為*記憶體中模組*並不存在於磁碟上。</span><span class="sxs-lookup"><span data-stu-id="c3eb7-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3eb7-110">需求</span><span class="sxs-lookup"><span data-stu-id="c3eb7-110">Requirements</span></span>  
 <span data-ttu-id="c3eb7-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c3eb7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3eb7-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c3eb7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3eb7-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3eb7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3eb7-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3eb7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3eb7-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3eb7-115">See also</span></span>
