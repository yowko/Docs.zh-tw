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
ms.openlocfilehash: 68931ba16ea1f8f61176c6d6ed8300e762b61690
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790531"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="9031b-102">ICorPublishProcess::IsManaged 方法</span><span class="sxs-lookup"><span data-stu-id="9031b-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="9031b-103">取得值，指出此[ICorPublishProcess](icorpublishprocess-interface.md)所參考的進程是否已知具有 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="9031b-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9031b-104">語法</span><span class="sxs-lookup"><span data-stu-id="9031b-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9031b-105">參數</span><span class="sxs-lookup"><span data-stu-id="9031b-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="9031b-106">脫銷布林值的指標，指出進程是否有 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="9031b-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="9031b-107">如果進程具有 managed 程式碼，則此值為 `true`;否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="9031b-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9031b-108">備註</span><span class="sxs-lookup"><span data-stu-id="9031b-108">Remarks</span></span>  
 <span data-ttu-id="9031b-109">由於目前的 `ICorPublishProcess` 版本只允許存取具有 managed 程式碼的進程，`IsManaged` 一律會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="9031b-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9031b-110">需求</span><span class="sxs-lookup"><span data-stu-id="9031b-110">Requirements</span></span>  
 <span data-ttu-id="9031b-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9031b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9031b-112">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="9031b-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="9031b-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9031b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9031b-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9031b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9031b-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="9031b-115">See also</span></span>

- [<span data-ttu-id="9031b-116">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="9031b-116">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
