---
title: IAssemblyName::GetName 方法
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetName
helpviewer_keywords:
- GetName method, IAssemblyName interface [.NET Framework debugging]
- IAssemblyName::GetName method [.NET Framework fusion]
ms.assetid: 1dee9781-1cf3-48a9-a376-d18ea1f73280
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a2c5c3bbbcf3cf4b87a5f68006c1625666d13926
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753894"
---
# <a name="iassemblynamegetname-method"></a><span data-ttu-id="d4eba-102">IAssemblyName::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="d4eba-102">IAssemblyName::GetName Method</span></span>
<span data-ttu-id="d4eba-103">取得所參考的組件的簡單且未加密名稱[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="d4eba-103">Gets the simple, unencrypted name of the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4eba-104">語法</span><span class="sxs-lookup"><span data-stu-id="d4eba-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in, out] LPDWORD lpcwBuffer,  
    [out]     WCHAR *pwzName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4eba-105">參數</span><span class="sxs-lookup"><span data-stu-id="d4eba-105">Parameters</span></span>  
 `lpcwBuffer`  
 <span data-ttu-id="d4eba-106">[in、 out]大小`pwzName`寬字元，包括 null 結束字元。</span><span class="sxs-lookup"><span data-stu-id="d4eba-106">[in, out] The size of `pwzName` in wide characters, including the null terminator character.</span></span>  
  
 `pwzName`  
 <span data-ttu-id="d4eba-107">[out]緩衝區來保留參考組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="d4eba-107">[out] A buffer to hold the name of the referenced assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4eba-108">需求</span><span class="sxs-lookup"><span data-stu-id="d4eba-108">Requirements</span></span>  
 <span data-ttu-id="d4eba-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d4eba-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4eba-110">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="d4eba-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d4eba-111">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4eba-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4eba-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4eba-112">See also</span></span>

- [<span data-ttu-id="d4eba-113">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="d4eba-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
