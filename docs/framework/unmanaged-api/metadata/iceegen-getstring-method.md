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
ms.openlocfilehash: 3d8d6a0ebecb4fbb9ba277844710c775d80648e5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716813"
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="5f0eb-102">ICeeGen::GetString 方法</span><span class="sxs-lookup"><span data-stu-id="5f0eb-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="5f0eb-103">取得儲存在指定的相對虛擬位址的字串。</span><span class="sxs-lookup"><span data-stu-id="5f0eb-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="5f0eb-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="5f0eb-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f0eb-105">語法</span><span class="sxs-lookup"><span data-stu-id="5f0eb-105">Syntax</span></span>  
  
```  
HRESULT GetString (  
    [in]  ULONG      RVA,   
    [out] LPWSTR     *lpString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5f0eb-106">參數</span><span class="sxs-lookup"><span data-stu-id="5f0eb-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="5f0eb-107">[in]要傳回之字串的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="5f0eb-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="5f0eb-108">[out]傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="5f0eb-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f0eb-109">需求</span><span class="sxs-lookup"><span data-stu-id="5f0eb-109">Requirements</span></span>  
 <span data-ttu-id="5f0eb-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5f0eb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f0eb-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5f0eb-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5f0eb-112">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5f0eb-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5f0eb-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f0eb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f0eb-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f0eb-114">See also</span></span>
- [<span data-ttu-id="5f0eb-115">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="5f0eb-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
