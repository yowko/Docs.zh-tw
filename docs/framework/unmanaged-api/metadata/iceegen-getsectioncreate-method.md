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
ms.openlocfilehash: 03de69d51b520ae2d8be6c7f450f0541c52c36a2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472430"
---
# <a name="iceegengetsectioncreate-method"></a><span data-ttu-id="b0033-102">ICeeGen::GetSectionCreate 方法</span><span class="sxs-lookup"><span data-stu-id="b0033-102">ICeeGen::GetSectionCreate Method</span></span>
<span data-ttu-id="b0033-103">產生並取得使用指定的名稱和旗標值的程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="b0033-103">Generates and gets a code section using the specified name and flag values.</span></span>  
  
 <span data-ttu-id="b0033-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="b0033-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0033-105">語法</span><span class="sxs-lookup"><span data-stu-id="b0033-105">Syntax</span></span>  
  
```  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0033-106">參數</span><span class="sxs-lookup"><span data-stu-id="b0033-106">Parameters</span></span>  
 `name`  
 <span data-ttu-id="b0033-107">[in]指定要建立的區段名稱的字串指標。</span><span class="sxs-lookup"><span data-stu-id="b0033-107">[in] A pointer to a string that specifies the name of the section to be created.</span></span>  
  
 `flags`  
 <span data-ttu-id="b0033-108">[in]指定選項的旗標。</span><span class="sxs-lookup"><span data-stu-id="b0033-108">[in] Flags that specify options.</span></span>  
  
 `section`  
 <span data-ttu-id="b0033-109">[out]新建立的程式碼區段指標。</span><span class="sxs-lookup"><span data-stu-id="b0033-109">[out] A pointer to the newly created code section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0033-110">備註</span><span class="sxs-lookup"><span data-stu-id="b0033-110">Remarks</span></span>  
 <span data-ttu-id="b0033-111">呼叫`GetSectionCreate`只有當您有未處理的其他方法的特殊區段需求。</span><span class="sxs-lookup"><span data-stu-id="b0033-111">Call `GetSectionCreate` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0033-112">需求</span><span class="sxs-lookup"><span data-stu-id="b0033-112">Requirements</span></span>  
 <span data-ttu-id="b0033-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b0033-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0033-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b0033-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b0033-115">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b0033-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b0033-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0033-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0033-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0033-117">See also</span></span>
- [<span data-ttu-id="b0033-118">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="b0033-118">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
