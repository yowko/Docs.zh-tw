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
ms.openlocfilehash: ca528bdbd9662db373d1beeece803d6c43728f2d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698607"
---
# <a name="iassemblynameclone-method"></a><span data-ttu-id="9b288-102">IAssemblyName::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="9b288-102">IAssemblyName::Clone Method</span></span>

<span data-ttu-id="9b288-103">建立這個 [IAssemblyName](iassemblyname-interface.md) 物件的淺層複本。</span><span class="sxs-lookup"><span data-stu-id="9b288-103">Creates a shallow copy of this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b288-104">語法</span><span class="sxs-lookup"><span data-stu-id="9b288-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] IAssemblyName **pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b288-105">參數</span><span class="sxs-lookup"><span data-stu-id="9b288-105">Parameters</span></span>  

 `pName`  
 <span data-ttu-id="9b288-106">擴展這個物件的傳回復本 `IAssemblyName` 。</span><span class="sxs-lookup"><span data-stu-id="9b288-106">[out] The returned copy of this `IAssemblyName` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b288-107">需求</span><span class="sxs-lookup"><span data-stu-id="9b288-107">Requirements</span></span>  

 <span data-ttu-id="9b288-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9b288-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b288-109">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="9b288-109">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="9b288-110">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b288-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b288-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b288-111">See also</span></span>

- [<span data-ttu-id="9b288-112">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="9b288-112">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
