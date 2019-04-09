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
ms.openlocfilehash: ef22114b582ebfc9714dedc0cb6e66594d945ca1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083786"
---
# <a name="iceegengetstringsection-method"></a><span data-ttu-id="0228c-102">ICeeGen::GetStringSection 方法</span><span class="sxs-lookup"><span data-stu-id="0228c-102">ICeeGen::GetStringSection Method</span></span>
<span data-ttu-id="0228c-103">取得指定的控制代碼所參考的程式碼區段的字串表示。</span><span class="sxs-lookup"><span data-stu-id="0228c-103">Gets a string representation of the code section referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="0228c-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="0228c-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0228c-105">語法</span><span class="sxs-lookup"><span data-stu-id="0228c-105">Syntax</span></span>  
  
```  
HRESULT GetStringSection (  
    [in, out] HCEESECTION     *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0228c-106">參數</span><span class="sxs-lookup"><span data-stu-id="0228c-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="0228c-107">[in、 out]程式碼區段控制代碼。</span><span class="sxs-lookup"><span data-stu-id="0228c-107">[in, out] The handle to the code section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0228c-108">需求</span><span class="sxs-lookup"><span data-stu-id="0228c-108">Requirements</span></span>  
 <span data-ttu-id="0228c-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0228c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0228c-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0228c-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0228c-111">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0228c-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="0228c-112">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="0228c-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0228c-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0228c-113">See also</span></span>

- [<span data-ttu-id="0228c-114">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="0228c-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
