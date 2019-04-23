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
ms.openlocfilehash: 29c5f96bab374d6e2d43424370bff2a4a2ab6df3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59218286"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="4e618-102">ICorPublishProcess::IsManaged 方法</span><span class="sxs-lookup"><span data-stu-id="4e618-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="4e618-103">取得值，指出是否在程序參考這[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)稱為具有 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="4e618-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e618-104">語法</span><span class="sxs-lookup"><span data-stu-id="4e618-104">Syntax</span></span>  
  
```  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e618-105">參數</span><span class="sxs-lookup"><span data-stu-id="4e618-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="4e618-106">[out]布林值，指出是否在程序具有 managed 程式碼指標。</span><span class="sxs-lookup"><span data-stu-id="4e618-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="4e618-107">值是`true`如果處理程序具有 managed 程式碼; 否則`false`。</span><span class="sxs-lookup"><span data-stu-id="4e618-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e618-108">備註</span><span class="sxs-lookup"><span data-stu-id="4e618-108">Remarks</span></span>  
 <span data-ttu-id="4e618-109">因為最新版`ICorPublishProcess`可讓您擁有的 managed 程式碼的處理序存取`IsManaged`一律會傳回`true`。</span><span class="sxs-lookup"><span data-stu-id="4e618-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e618-110">需求</span><span class="sxs-lookup"><span data-stu-id="4e618-110">Requirements</span></span>  
 <span data-ttu-id="4e618-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4e618-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e618-112">**標頭：** CorPub.idl CorPub.h</span><span class="sxs-lookup"><span data-stu-id="4e618-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="4e618-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e618-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e618-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e618-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e618-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e618-115">See also</span></span>

- [<span data-ttu-id="4e618-116">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="4e618-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
