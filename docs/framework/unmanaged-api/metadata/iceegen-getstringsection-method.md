---
title: ICeeGen::GetStringSection 方法
ms.date: 03/30/2017
api_name:
- ICeeGen.GetStringSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetStringSection
helpviewer_keywords:
- ICeeGen::GetStringSection method [.NET Framework metadata]
- GetStringSection method [.NET Framework metadata]
ms.assetid: a2267d39-69d1-4de1-bf37-f752cafacc71
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a8617c9e818ec514c912a85373c916559d89df3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443033"
---
# <a name="iceegengetstringsection-method"></a><span data-ttu-id="5188b-102">ICeeGen::GetStringSection 方法</span><span class="sxs-lookup"><span data-stu-id="5188b-102">ICeeGen::GetStringSection Method</span></span>
<span data-ttu-id="5188b-103">取得指定的控制代碼所參考的程式碼區段的字串表示。</span><span class="sxs-lookup"><span data-stu-id="5188b-103">Gets a string representation of the code section referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="5188b-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="5188b-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5188b-105">語法</span><span class="sxs-lookup"><span data-stu-id="5188b-105">Syntax</span></span>  
  
```  
HRESULT GetStringSection (  
    [in, out] HCEESECTION     *section  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5188b-106">參數</span><span class="sxs-lookup"><span data-stu-id="5188b-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="5188b-107">[in、 out]程式碼區段之控制代碼。</span><span class="sxs-lookup"><span data-stu-id="5188b-107">[in, out] The handle to the code section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5188b-108">需求</span><span class="sxs-lookup"><span data-stu-id="5188b-108">Requirements</span></span>  
 <span data-ttu-id="5188b-109">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5188b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5188b-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5188b-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5188b-111">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5188b-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5188b-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5188b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5188b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5188b-113">See Also</span></span>  
 [<span data-ttu-id="5188b-114">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="5188b-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
