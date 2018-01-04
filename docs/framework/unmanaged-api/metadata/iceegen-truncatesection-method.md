---
title: "ICeeGen::TruncateSection 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.TruncateSection
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::TruncateSection
helpviewer_keywords:
- TruncateSection method [.NET Framework metadata]
- ICeeGen::TruncateSection method [.NET Framework metadata]
ms.assetid: 0451d752-1e5c-4c9a-8bad-6cd35b7ba3df
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8e7deaaab58f1ee51bd3675faec892db5228c787
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iceegentruncatesection-method"></a><span data-ttu-id="83981-102">ICeeGen::TruncateSection 方法</span><span class="sxs-lookup"><span data-stu-id="83981-102">ICeeGen::TruncateSection Method</span></span>
<span data-ttu-id="83981-103">指定的長度來截斷指定的程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="83981-103">Truncates the specified code section by the specified length.</span></span>  
  
 <span data-ttu-id="83981-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="83981-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83981-105">語法</span><span class="sxs-lookup"><span data-stu-id="83981-105">Syntax</span></span>  
  
```  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83981-106">參數</span><span class="sxs-lookup"><span data-stu-id="83981-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="83981-107">[in]要截斷的區段。</span><span class="sxs-lookup"><span data-stu-id="83981-107">[in] The section to truncate.</span></span>  
  
 `len`  
 <span data-ttu-id="83981-108">[in]長度 （以位元組為單位，所要截斷一節）。</span><span class="sxs-lookup"><span data-stu-id="83981-108">[in] The length, in bytes, by which to truncate the section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83981-109">備註</span><span class="sxs-lookup"><span data-stu-id="83981-109">Remarks</span></span>  
 <span data-ttu-id="83981-110">呼叫`TruncateSection`只有當您有不由其他方法處理的特殊區段需求。</span><span class="sxs-lookup"><span data-stu-id="83981-110">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83981-111">需求</span><span class="sxs-lookup"><span data-stu-id="83981-111">Requirements</span></span>  
 <span data-ttu-id="83981-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="83981-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83981-113">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="83981-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="83981-114">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="83981-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="83981-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83981-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83981-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="83981-116">See Also</span></span>  
 [<span data-ttu-id="83981-117">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="83981-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
