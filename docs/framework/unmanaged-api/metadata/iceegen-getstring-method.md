---
title: "ICeeGen::GetString 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetString
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetString
helpviewer_keywords:
- ICeeGen::GetString method [.NET Framework metadata]
- GetString method, ICeeGen interface [.NET Framework metadata]
ms.assetid: 7cc22562-128c-440a-9147-55ff20f173d7
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f7afe07309850a564ec75e69c07f63a3210f3810
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="ab986-102">ICeeGen::GetString 方法</span><span class="sxs-lookup"><span data-stu-id="ab986-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="ab986-103">取得儲存在指定的相對虛擬位址的字串。</span><span class="sxs-lookup"><span data-stu-id="ab986-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="ab986-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="ab986-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab986-105">語法</span><span class="sxs-lookup"><span data-stu-id="ab986-105">Syntax</span></span>  
  
```  
HRESULT GetString (  
    [in]  ULONG      RVA,   
    [out] LPWSTR     *lpString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab986-106">參數</span><span class="sxs-lookup"><span data-stu-id="ab986-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="ab986-107">[in]要傳回之字串的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="ab986-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="ab986-108">[out]傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="ab986-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab986-109">需求</span><span class="sxs-lookup"><span data-stu-id="ab986-109">Requirements</span></span>  
 <span data-ttu-id="ab986-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ab986-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab986-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ab986-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ab986-112">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ab986-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ab986-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab986-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab986-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab986-114">See Also</span></span>  
 [<span data-ttu-id="ab986-115">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="ab986-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
