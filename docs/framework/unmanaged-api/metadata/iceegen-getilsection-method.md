---
title: "ICeeGen::GetIlSection 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetIlSection
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetIlSection
helpviewer_keywords:
- GetIlSection method [.NET Framework metadata]
- ICeeGen::GetIlSection method [.NET Framework metadata]
ms.assetid: 6f2db2ca-203f-4ac3-9530-208642ca385e
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b87936fb099d6e58281162d0a9a75291b0ac0767
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="iceegengetilsection-method"></a><span data-ttu-id="d6a89-102">ICeeGen::GetIlSection 方法</span><span class="sxs-lookup"><span data-stu-id="d6a89-102">ICeeGen::GetIlSection Method</span></span>
<span data-ttu-id="d6a89-103">取得指定的控制代碼所參考的基底中繼語言程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="d6a89-103">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="d6a89-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="d6a89-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6a89-105">語法</span><span class="sxs-lookup"><span data-stu-id="d6a89-105">Syntax</span></span>  
  
```  
HRESULT GetIlSection (  
    [in] HCEESECTION  *section  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6a89-106">參數</span><span class="sxs-lookup"><span data-stu-id="d6a89-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="d6a89-107">[in]若要取得的區段控制代碼。</span><span class="sxs-lookup"><span data-stu-id="d6a89-107">[in] The handle to the section to get.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6a89-108">需求</span><span class="sxs-lookup"><span data-stu-id="d6a89-108">Requirements</span></span>  
 <span data-ttu-id="d6a89-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d6a89-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6a89-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d6a89-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d6a89-111">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d6a89-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d6a89-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6a89-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6a89-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6a89-113">See Also</span></span>  
 [<span data-ttu-id="d6a89-114">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="d6a89-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
