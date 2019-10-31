---
title: IAssemblyName::Clone 方法
ms.date: 03/30/2017
api_name:
- IAssemblyName.Clone
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::Clone
helpviewer_keywords:
- Clone method, IAssemblyName interface [.NET Framework fusion]
- IAssemblyName::Clone method [.NET Framework fusion]
ms.assetid: 7b345e08-5e16-4e3d-a044-4e19d0892943
topic_type:
- apiref
ms.openlocfilehash: 1236a574a85c01e3e1be5df9644bd04bbf0753ea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134412"
---
# <a name="iassemblynameclone-method"></a><span data-ttu-id="d9ed0-102">IAssemblyName::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="d9ed0-102">IAssemblyName::Clone Method</span></span>
<span data-ttu-id="d9ed0-103">建立這個[IAssemblyName](iassemblyname-interface.md)物件的淺層複本。</span><span class="sxs-lookup"><span data-stu-id="d9ed0-103">Creates a shallow copy of this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9ed0-104">語法</span><span class="sxs-lookup"><span data-stu-id="d9ed0-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] IAssemblyName **pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9ed0-105">參數</span><span class="sxs-lookup"><span data-stu-id="d9ed0-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="d9ed0-106">脫銷這個 `IAssemblyName` 物件的傳回復本。</span><span class="sxs-lookup"><span data-stu-id="d9ed0-106">[out] The returned copy of this `IAssemblyName` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9ed0-107">需求</span><span class="sxs-lookup"><span data-stu-id="d9ed0-107">Requirements</span></span>  
 <span data-ttu-id="d9ed0-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d9ed0-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9ed0-109">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="d9ed0-109">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d9ed0-110">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9ed0-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9ed0-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="d9ed0-111">See also</span></span>

- [<span data-ttu-id="d9ed0-112">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="d9ed0-112">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
