---
title: ICeeGen::GetString 方法
ms.date: 03/30/2017
api_name:
- ICeeGen.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetString
helpviewer_keywords:
- ICeeGen::GetString method [.NET Framework metadata]
- GetString method, ICeeGen interface [.NET Framework metadata]
ms.assetid: 7cc22562-128c-440a-9147-55ff20f173d7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ce015713ca7ed26c97348aa39f8170a85c8aa93c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745927"
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="95304-102">ICeeGen::GetString 方法</span><span class="sxs-lookup"><span data-stu-id="95304-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="95304-103">取得儲存在指定的相對虛擬位址的字串。</span><span class="sxs-lookup"><span data-stu-id="95304-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="95304-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="95304-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95304-105">語法</span><span class="sxs-lookup"><span data-stu-id="95304-105">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in]  ULONG      RVA,   
    [out] LPWSTR     *lpString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95304-106">參數</span><span class="sxs-lookup"><span data-stu-id="95304-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="95304-107">[in]要傳回之字串的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="95304-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="95304-108">[out]傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="95304-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95304-109">需求</span><span class="sxs-lookup"><span data-stu-id="95304-109">Requirements</span></span>  
 <span data-ttu-id="95304-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="95304-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95304-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="95304-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="95304-112">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="95304-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="95304-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95304-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95304-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95304-114">See also</span></span>

- [<span data-ttu-id="95304-115">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="95304-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
