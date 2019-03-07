---
title: ICeeGen::EmitString 方法
ms.date: 03/30/2017
api_name:
- ICeeGen.EmitString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::EmitString
helpviewer_keywords:
- EmitString method [.NET Framework metadata]
- ICeeGen::EmitString method [.NET Framework metadata]
ms.assetid: ad2710a7-edb8-4493-8619-3fce235e3334
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 63ddd3b5cc79cedba6d6acc6a9b6b70c00d917fc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476226"
---
# <a name="iceegenemitstring-method"></a><span data-ttu-id="70d9c-102">ICeeGen::EmitString 方法</span><span class="sxs-lookup"><span data-stu-id="70d9c-102">ICeeGen::EmitString Method</span></span>
<span data-ttu-id="70d9c-103">程式碼基底到發出指定的字串。</span><span class="sxs-lookup"><span data-stu-id="70d9c-103">Emits the specified string into the code base.</span></span>  
  
 <span data-ttu-id="70d9c-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="70d9c-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70d9c-105">語法</span><span class="sxs-lookup"><span data-stu-id="70d9c-105">Syntax</span></span>  
  
```  
HRESULT EmitString (  
    [in]  LPWSTR    lpString,  
    [out] ULONG     *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70d9c-106">參數</span><span class="sxs-lookup"><span data-stu-id="70d9c-106">Parameters</span></span>  
 `lpString`  
 <span data-ttu-id="70d9c-107">[in]要發出的字串。</span><span class="sxs-lookup"><span data-stu-id="70d9c-107">[in] The string to emit.</span></span>  
  
 `RVA`  
 <span data-ttu-id="70d9c-108">[out]發出的字串相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="70d9c-108">[out] The relative virtual address of the emitted string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70d9c-109">需求</span><span class="sxs-lookup"><span data-stu-id="70d9c-109">Requirements</span></span>  
 <span data-ttu-id="70d9c-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="70d9c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70d9c-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="70d9c-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="70d9c-112">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="70d9c-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="70d9c-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70d9c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70d9c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70d9c-114">See also</span></span>
- [<span data-ttu-id="70d9c-115">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="70d9c-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
