---
title: ICeeGen::GetIlSection 方法
ms.date: 03/30/2017
api_name:
- ICeeGen.GetIlSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetIlSection
helpviewer_keywords:
- GetIlSection method [.NET Framework metadata]
- ICeeGen::GetIlSection method [.NET Framework metadata]
ms.assetid: 6f2db2ca-203f-4ac3-9530-208642ca385e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1cff5b7fadf4345b7a1d09911dc7061adc925e7a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992611"
---
# <a name="iceegengetilsection-method"></a><span data-ttu-id="d4ab5-102">ICeeGen::GetIlSection 方法</span><span class="sxs-lookup"><span data-stu-id="d4ab5-102">ICeeGen::GetIlSection Method</span></span>
<span data-ttu-id="d4ab5-103">取得指定的控制代碼所參考的基底中繼語言程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="d4ab5-103">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="d4ab5-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="d4ab5-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4ab5-105">語法</span><span class="sxs-lookup"><span data-stu-id="d4ab5-105">Syntax</span></span>  
  
```  
HRESULT GetIlSection (  
    [in] HCEESECTION  *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4ab5-106">參數</span><span class="sxs-lookup"><span data-stu-id="d4ab5-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="d4ab5-107">[in]一節，以控制代碼。</span><span class="sxs-lookup"><span data-stu-id="d4ab5-107">[in] The handle to the section to get.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4ab5-108">需求</span><span class="sxs-lookup"><span data-stu-id="d4ab5-108">Requirements</span></span>  
 <span data-ttu-id="d4ab5-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d4ab5-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4ab5-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d4ab5-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d4ab5-111">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d4ab5-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d4ab5-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4ab5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4ab5-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4ab5-113">See also</span></span>

- [<span data-ttu-id="d4ab5-114">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="d4ab5-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
