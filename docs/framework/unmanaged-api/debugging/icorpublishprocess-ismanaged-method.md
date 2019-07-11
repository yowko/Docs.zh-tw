---
title: ICorPublishProcess::IsManaged 方法
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee3a0c27d350dec8e9f3e9448174d978c7d50e81
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775695"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="4a1d6-102">ICorPublishProcess::IsManaged 方法</span><span class="sxs-lookup"><span data-stu-id="4a1d6-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="4a1d6-103">取得值，指出是否在程序參考這[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)稱為具有 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a1d6-104">語法</span><span class="sxs-lookup"><span data-stu-id="4a1d6-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a1d6-105">參數</span><span class="sxs-lookup"><span data-stu-id="4a1d6-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="4a1d6-106">[out]布林值，指出是否在程序具有 managed 程式碼指標。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="4a1d6-107">值是`true`如果處理程序具有 managed 程式碼; 否則`false`。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a1d6-108">備註</span><span class="sxs-lookup"><span data-stu-id="4a1d6-108">Remarks</span></span>  
 <span data-ttu-id="4a1d6-109">因為最新版`ICorPublishProcess`可讓您擁有的 managed 程式碼的處理序存取`IsManaged`一律會傳回`true`。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a1d6-110">需求</span><span class="sxs-lookup"><span data-stu-id="4a1d6-110">Requirements</span></span>  
 <span data-ttu-id="4a1d6-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a1d6-112">**標頭：** CorPub.idl CorPub.h</span><span class="sxs-lookup"><span data-stu-id="4a1d6-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="4a1d6-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a1d6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a1d6-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a1d6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a1d6-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a1d6-115">See also</span></span>

- [<span data-ttu-id="4a1d6-116">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="4a1d6-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
