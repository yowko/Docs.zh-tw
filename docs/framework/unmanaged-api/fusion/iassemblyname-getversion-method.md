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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58919936bdc62d52437f429146f04c66d49294b2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796577"
---
# <a name="iassemblynamegetversion-method"></a><span data-ttu-id="a9b7c-102">IAssemblyName::GetVersion 方法</span><span class="sxs-lookup"><span data-stu-id="a9b7c-102">IAssemblyName::GetVersion Method</span></span>
<span data-ttu-id="a9b7c-103">取得這個[IAssemblyName](iassemblyname-interface.md)物件所參考之元件的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="a9b7c-103">Gets the version information for the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9b7c-104">語法</span><span class="sxs-lookup"><span data-stu-id="a9b7c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion (  
    [out] LPDWORD pdwVersionHi,  
    [out] LPDWORD pdwVersionLow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9b7c-105">參數</span><span class="sxs-lookup"><span data-stu-id="a9b7c-105">Parameters</span></span>  
 `pdwVersionHi`  
 <span data-ttu-id="a9b7c-106">脫銷版本的高32位。</span><span class="sxs-lookup"><span data-stu-id="a9b7c-106">[out] The high 32 bits of the version.</span></span>  
  
 `pdwVersionLow`  
 <span data-ttu-id="a9b7c-107">脫銷版本的低32位。</span><span class="sxs-lookup"><span data-stu-id="a9b7c-107">[out] The low 32 bits of the version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9b7c-108">需求</span><span class="sxs-lookup"><span data-stu-id="a9b7c-108">Requirements</span></span>  
 <span data-ttu-id="a9b7c-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a9b7c-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9b7c-110">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="a9b7c-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a9b7c-111">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9b7c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9b7c-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9b7c-112">See also</span></span>

- [<span data-ttu-id="a9b7c-113">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="a9b7c-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
