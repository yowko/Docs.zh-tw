---
title: "ICeeGen::EmitString 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.EmitString
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::EmitString
helpviewer_keywords:
- EmitString method [.NET Framework metadata]
- ICeeGen::EmitString method [.NET Framework metadata]
ms.assetid: ad2710a7-edb8-4493-8619-3fce235e3334
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 89c53f41595416a6bb4b8d373c7d3dbcea4c4faa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iceegenemitstring-method"></a><span data-ttu-id="ccdbb-102">ICeeGen::EmitString 方法</span><span class="sxs-lookup"><span data-stu-id="ccdbb-102">ICeeGen::EmitString Method</span></span>
<span data-ttu-id="ccdbb-103">指定的字串發出到程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="ccdbb-103">Emits the specified string into the code base.</span></span>  
  
 <span data-ttu-id="ccdbb-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="ccdbb-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccdbb-105">語法</span><span class="sxs-lookup"><span data-stu-id="ccdbb-105">Syntax</span></span>  
  
```  
HRESULT EmitString (  
    [in]  LPWSTR    lpString,  
    [out] ULONG     *RVA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ccdbb-106">參數</span><span class="sxs-lookup"><span data-stu-id="ccdbb-106">Parameters</span></span>  
 `lpString`  
 <span data-ttu-id="ccdbb-107">[in]要發出的字串。</span><span class="sxs-lookup"><span data-stu-id="ccdbb-107">[in] The string to emit.</span></span>  
  
 `RVA`  
 <span data-ttu-id="ccdbb-108">[out]發出的字串相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="ccdbb-108">[out] The relative virtual address of the emitted string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccdbb-109">需求</span><span class="sxs-lookup"><span data-stu-id="ccdbb-109">Requirements</span></span>  
 <span data-ttu-id="ccdbb-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ccdbb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccdbb-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ccdbb-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ccdbb-112">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ccdbb-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ccdbb-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccdbb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccdbb-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="ccdbb-114">See Also</span></span>  
 [<span data-ttu-id="ccdbb-115">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="ccdbb-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
