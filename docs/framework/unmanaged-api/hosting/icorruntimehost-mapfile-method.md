---
title: ICorRuntimeHost::MapFile 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.MapFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::MapFile
helpviewer_keywords:
- ICorRuntimeHost::MapFile method [.NET Framework hosting]
- MapFile method [.NET Framework hosting]
ms.assetid: 45ae0502-0a31-4342-b7e3-f36e1cf738f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 956de98fca1caec0ac1b94afc7251f9741246f94
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494775"
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="d3165-102">ICorRuntimeHost::MapFile 方法</span><span class="sxs-lookup"><span data-stu-id="d3165-102">ICorRuntimeHost::MapFile Method</span></span>
<span data-ttu-id="d3165-103">將指定的檔案對應到記憶體中。</span><span class="sxs-lookup"><span data-stu-id="d3165-103">Maps the specified file into memory.</span></span> <span data-ttu-id="d3165-104">這個方法已過時。</span><span class="sxs-lookup"><span data-stu-id="d3165-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3165-105">語法</span><span class="sxs-lookup"><span data-stu-id="d3165-105">Syntax</span></span>  
  
```  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3165-106">參數</span><span class="sxs-lookup"><span data-stu-id="d3165-106">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="d3165-107">[in]要對應的檔案控制代碼。</span><span class="sxs-lookup"><span data-stu-id="d3165-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="d3165-108">[out]要開始對應檔案起始記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="d3165-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3165-109">需求</span><span class="sxs-lookup"><span data-stu-id="d3165-109">Requirements</span></span>  
 <span data-ttu-id="d3165-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d3165-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3165-111">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d3165-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d3165-112">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d3165-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3165-113">**.NET framework 版本：** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="d3165-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3165-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3165-114">See also</span></span>
- [<span data-ttu-id="d3165-115">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="d3165-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
