---
title: "ICeeGen::GetIlSection 方法"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4805e9421a80954c01ba1ffb6e04332c07e5d84e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iceegengetilsection-method"></a><span data-ttu-id="97f67-102">ICeeGen::GetIlSection 方法</span><span class="sxs-lookup"><span data-stu-id="97f67-102">ICeeGen::GetIlSection Method</span></span>
<span data-ttu-id="97f67-103">取得指定的控制代碼所參考的基底中繼語言程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="97f67-103">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="97f67-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="97f67-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97f67-105">語法</span><span class="sxs-lookup"><span data-stu-id="97f67-105">Syntax</span></span>  
  
```  
HRESULT GetIlSection (  
    [in] HCEESECTION  *section  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="97f67-106">參數</span><span class="sxs-lookup"><span data-stu-id="97f67-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="97f67-107">[in]若要取得的區段控制代碼。</span><span class="sxs-lookup"><span data-stu-id="97f67-107">[in] The handle to the section to get.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97f67-108">需求</span><span class="sxs-lookup"><span data-stu-id="97f67-108">Requirements</span></span>  
 <span data-ttu-id="97f67-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="97f67-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97f67-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="97f67-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="97f67-111">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="97f67-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="97f67-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97f67-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97f67-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="97f67-113">See Also</span></span>  
 [<span data-ttu-id="97f67-114">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="97f67-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
