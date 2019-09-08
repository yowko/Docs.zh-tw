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
ms.openlocfilehash: e471ee99af57ef980850c0a5d3e4f5f2973967ac
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796599"
---
# <a name="iassemblynamegetname-method"></a><span data-ttu-id="797b3-102">IAssemblyName::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="797b3-102">IAssemblyName::GetName Method</span></span>
<span data-ttu-id="797b3-103">取得這個[IAssemblyName](iassemblyname-interface.md)物件所參考的簡單、未加密的元件名稱。</span><span class="sxs-lookup"><span data-stu-id="797b3-103">Gets the simple, unencrypted name of the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="797b3-104">語法</span><span class="sxs-lookup"><span data-stu-id="797b3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in, out] LPDWORD lpcwBuffer,  
    [out]     WCHAR *pwzName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="797b3-105">參數</span><span class="sxs-lookup"><span data-stu-id="797b3-105">Parameters</span></span>  
 `lpcwBuffer`  
 <span data-ttu-id="797b3-106">[in、out]`pwzName`以寬字元為單位的大小，包括 null 結束字元字元。</span><span class="sxs-lookup"><span data-stu-id="797b3-106">[in, out] The size of `pwzName` in wide characters, including the null terminator character.</span></span>  
  
 `pwzName`  
 <span data-ttu-id="797b3-107">脫銷保存參考元件名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="797b3-107">[out] A buffer to hold the name of the referenced assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="797b3-108">需求</span><span class="sxs-lookup"><span data-stu-id="797b3-108">Requirements</span></span>  
 <span data-ttu-id="797b3-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="797b3-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="797b3-110">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="797b3-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="797b3-111">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="797b3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="797b3-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="797b3-112">See also</span></span>

- [<span data-ttu-id="797b3-113">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="797b3-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
