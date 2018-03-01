---
title: "ICeeGen::GetString 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7365cb96021438d9c7e287463782e1cb112a66a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="59cf5-102">ICeeGen::GetString 方法</span><span class="sxs-lookup"><span data-stu-id="59cf5-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="59cf5-103">取得儲存在指定的相對虛擬位址的字串。</span><span class="sxs-lookup"><span data-stu-id="59cf5-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="59cf5-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="59cf5-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59cf5-105">語法</span><span class="sxs-lookup"><span data-stu-id="59cf5-105">Syntax</span></span>  
  
```  
HRESULT GetString (  
    [in]  ULONG      RVA,   
    [out] LPWSTR     *lpString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="59cf5-106">參數</span><span class="sxs-lookup"><span data-stu-id="59cf5-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="59cf5-107">[in]要傳回之字串的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="59cf5-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="59cf5-108">[out]傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="59cf5-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59cf5-109">需求</span><span class="sxs-lookup"><span data-stu-id="59cf5-109">Requirements</span></span>  
 <span data-ttu-id="59cf5-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="59cf5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59cf5-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="59cf5-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="59cf5-112">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="59cf5-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="59cf5-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59cf5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59cf5-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="59cf5-114">See Also</span></span>  
 [<span data-ttu-id="59cf5-115">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="59cf5-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
