---
title: ICorPublishEnum::Clone 方法
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.Clone
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Clone
helpviewer_keywords:
- Clone method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::Clone method [.NET Framework debugging]
ms.assetid: c9a26ea3-b8eb-4b8e-854f-9a2ca26b3b39
topic_type:
- apiref
ms.openlocfilehash: afd16f1f31be9148422dd6d0be748036a8e5d99a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790665"
---
# <a name="icorpublishenumclone-method"></a><span data-ttu-id="2c91b-102">ICorPublishEnum::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="2c91b-102">ICorPublishEnum::Clone Method</span></span>
<span data-ttu-id="2c91b-103">建立這個[ICorPublishEnum](icorpublishenum-interface.md)物件的複本。</span><span class="sxs-lookup"><span data-stu-id="2c91b-103">Creates a copy of this [ICorPublishEnum](icorpublishenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c91b-104">語法</span><span class="sxs-lookup"><span data-stu-id="2c91b-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c91b-105">參數</span><span class="sxs-lookup"><span data-stu-id="2c91b-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="2c91b-106">脫銷這個 `ICorPublishEnum` 物件之複本的 `ICorPublishEnum` 物件位址的指標。</span><span class="sxs-lookup"><span data-stu-id="2c91b-106">[out] A pointer to the address of an `ICorPublishEnum` object that is a copy of this `ICorPublishEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c91b-107">需求</span><span class="sxs-lookup"><span data-stu-id="2c91b-107">Requirements</span></span>  
 <span data-ttu-id="2c91b-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2c91b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c91b-109">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="2c91b-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="2c91b-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c91b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c91b-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c91b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c91b-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="2c91b-112">See also</span></span>

- [<span data-ttu-id="2c91b-113">ICorPublishEnum 介面</span><span class="sxs-lookup"><span data-stu-id="2c91b-113">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)
