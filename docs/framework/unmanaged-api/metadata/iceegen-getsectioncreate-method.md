---
title: ICeeGen::GetSectionCreate 方法
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionCreate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionCreate
helpviewer_keywords:
- ICeeGen::GetSectionCreate method [.NET Framework metadata]
- GetSectionCreate method [.NET Framework metadata]
ms.assetid: 154b2460-59ce-4874-a9f2-1b3353486ac5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9768dfd43b6b60df1660c48cb6d6f498b049e256
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59103307"
---
# <a name="iceegengetsectioncreate-method"></a><span data-ttu-id="76c52-102">ICeeGen::GetSectionCreate 方法</span><span class="sxs-lookup"><span data-stu-id="76c52-102">ICeeGen::GetSectionCreate Method</span></span>
<span data-ttu-id="76c52-103">產生並取得使用指定的名稱和旗標值的程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="76c52-103">Generates and gets a code section using the specified name and flag values.</span></span>  
  
 <span data-ttu-id="76c52-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="76c52-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76c52-105">語法</span><span class="sxs-lookup"><span data-stu-id="76c52-105">Syntax</span></span>  
  
```  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76c52-106">參數</span><span class="sxs-lookup"><span data-stu-id="76c52-106">Parameters</span></span>  
 `name`  
 <span data-ttu-id="76c52-107">[in]指定要建立的區段名稱的字串指標。</span><span class="sxs-lookup"><span data-stu-id="76c52-107">[in] A pointer to a string that specifies the name of the section to be created.</span></span>  
  
 `flags`  
 <span data-ttu-id="76c52-108">[in]指定選項的旗標。</span><span class="sxs-lookup"><span data-stu-id="76c52-108">[in] Flags that specify options.</span></span>  
  
 `section`  
 <span data-ttu-id="76c52-109">[out]新建立的程式碼區段指標。</span><span class="sxs-lookup"><span data-stu-id="76c52-109">[out] A pointer to the newly created code section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76c52-110">備註</span><span class="sxs-lookup"><span data-stu-id="76c52-110">Remarks</span></span>  
 <span data-ttu-id="76c52-111">呼叫`GetSectionCreate`只有當您有未處理的其他方法的特殊區段需求。</span><span class="sxs-lookup"><span data-stu-id="76c52-111">Call `GetSectionCreate` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76c52-112">需求</span><span class="sxs-lookup"><span data-stu-id="76c52-112">Requirements</span></span>  
 <span data-ttu-id="76c52-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="76c52-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76c52-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="76c52-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="76c52-115">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="76c52-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="76c52-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76c52-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76c52-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76c52-117">See also</span></span>

- [<span data-ttu-id="76c52-118">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="76c52-118">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
