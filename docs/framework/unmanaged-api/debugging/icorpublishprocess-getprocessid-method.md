---
title: ICorPublishProcess::GetProcessID 方法
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.GetProcessID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::GetProcessID
helpviewer_keywords:
- ICorPublishProcess::GetProcessID method [.NET Framework debugging]
- GetProcessID method [.NET Framework debugging]
ms.assetid: f31185e0-f01d-463a-b392-42163e39bfe9
topic_type:
- apiref
ms.openlocfilehash: 95a4ef3ab77b33c67c63be2c22647075f2f95ce8
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421107"
---
# <a name="icorpublishprocessgetprocessid-method"></a><span data-ttu-id="6bed8-102">ICorPublishProcess::GetProcessID 方法</span><span class="sxs-lookup"><span data-stu-id="6bed8-102">ICorPublishProcess::GetProcessID Method</span></span>
<span data-ttu-id="6bed8-103">取得此進程的作業系統識別碼。</span><span class="sxs-lookup"><span data-stu-id="6bed8-103">Gets the operating system identifier for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bed8-104">語法</span><span class="sxs-lookup"><span data-stu-id="6bed8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcessID (  
    [out] unsigned   *pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bed8-105">參數</span><span class="sxs-lookup"><span data-stu-id="6bed8-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="6bed8-106">脫銷這個[ICorPublishProcess](icorpublishprocess-interface.md)物件所表示之進程的識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="6bed8-106">[out] A pointer to the identifier of the process represented by this [ICorPublishProcess](icorpublishprocess-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bed8-107">需求</span><span class="sxs-lookup"><span data-stu-id="6bed8-107">Requirements</span></span>  
 <span data-ttu-id="6bed8-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6bed8-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bed8-109">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="6bed8-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="6bed8-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6bed8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bed8-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bed8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bed8-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6bed8-112">See also</span></span>

- [<span data-ttu-id="6bed8-113">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="6bed8-113">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
