---
title: IAssemblyName::GetVersion 方法
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetVersion
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetVersion
helpviewer_keywords:
- IAssemblyName::GetVersion method [.NET Framework fusion]
- GetVersion method, IAssemblyName interface [.NET Framework fusion]
ms.assetid: 42230928-2c33-41fd-9519-d96efef6c7af
topic_type:
- apiref
ms.openlocfilehash: c0a43dc1640bdaa0ae104832eb4d1f8eb15b0392
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134338"
---
# <a name="iassemblynamegetversion-method"></a><span data-ttu-id="87992-102">IAssemblyName::GetVersion 方法</span><span class="sxs-lookup"><span data-stu-id="87992-102">IAssemblyName::GetVersion Method</span></span>
<span data-ttu-id="87992-103">取得這個[IAssemblyName](iassemblyname-interface.md)物件所參考之元件的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="87992-103">Gets the version information for the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87992-104">語法</span><span class="sxs-lookup"><span data-stu-id="87992-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion (  
    [out] LPDWORD pdwVersionHi,  
    [out] LPDWORD pdwVersionLow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87992-105">參數</span><span class="sxs-lookup"><span data-stu-id="87992-105">Parameters</span></span>  
 `pdwVersionHi`  
 <span data-ttu-id="87992-106">脫銷版本的高32位。</span><span class="sxs-lookup"><span data-stu-id="87992-106">[out] The high 32 bits of the version.</span></span>  
  
 `pdwVersionLow`  
 <span data-ttu-id="87992-107">脫銷版本的低32位。</span><span class="sxs-lookup"><span data-stu-id="87992-107">[out] The low 32 bits of the version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87992-108">需求</span><span class="sxs-lookup"><span data-stu-id="87992-108">Requirements</span></span>  
 <span data-ttu-id="87992-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="87992-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87992-110">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="87992-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="87992-111">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87992-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87992-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="87992-112">See also</span></span>

- [<span data-ttu-id="87992-113">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="87992-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
