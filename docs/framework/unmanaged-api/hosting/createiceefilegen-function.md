---
title: "CreateICeeFileGen 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type: COM
f1_keywords: CreateICeeFileGen
helpviewer_keywords: CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9162da1b48348da745f8616b5cc643bf3dee97fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="e7257-102">CreateICeeFileGen 函式</span><span class="sxs-lookup"><span data-stu-id="e7257-102">CreateICeeFileGen Function</span></span>
<span data-ttu-id="e7257-103">建立[ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md)物件。</span><span class="sxs-lookup"><span data-stu-id="e7257-103">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="e7257-104">此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e7257-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7257-105">語法</span><span class="sxs-lookup"><span data-stu-id="e7257-105">Syntax</span></span>  
  
```  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e7257-106">參數</span><span class="sxs-lookup"><span data-stu-id="e7257-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="e7257-107">[out]新的位址指標`ICeeFileGen`物件。</span><span class="sxs-lookup"><span data-stu-id="e7257-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e7257-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="e7257-108">Return Value</span></span>  
 <span data-ttu-id="e7257-109">這個方法會傳回標準的 COM 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="e7257-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7257-110">備註</span><span class="sxs-lookup"><span data-stu-id="e7257-110">Remarks</span></span>  
 <span data-ttu-id="e7257-111">`ICeeFileGen`物件用來建立 common language runtime (CLR) 的可攜式執行檔 (PE) 檔案。</span><span class="sxs-lookup"><span data-stu-id="e7257-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="e7257-112">呼叫[DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md)函式終結`ICeeFileGen`物件時完成。</span><span class="sxs-lookup"><span data-stu-id="e7257-112">Call the [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7257-113">需求</span><span class="sxs-lookup"><span data-stu-id="e7257-113">Requirements</span></span>  
 <span data-ttu-id="e7257-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e7257-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7257-115">**標頭：** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="e7257-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="e7257-116">**程式庫：** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="e7257-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="e7257-117">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7257-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7257-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7257-118">See Also</span></span>  
 [<span data-ttu-id="e7257-119">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="e7257-119">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
