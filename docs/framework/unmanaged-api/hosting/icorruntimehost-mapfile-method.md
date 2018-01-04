---
title: "ICorRuntimeHost::MapFile 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.MapFile
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::MapFile
helpviewer_keywords:
- ICorRuntimeHost::MapFile method [.NET Framework hosting]
- MapFile method [.NET Framework hosting]
ms.assetid: 45ae0502-0a31-4342-b7e3-f36e1cf738f3
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b3047a473f36762ec57ae4ea87067e941ac568c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="b54aa-102">ICorRuntimeHost::MapFile 方法</span><span class="sxs-lookup"><span data-stu-id="b54aa-102">ICorRuntimeHost::MapFile Method</span></span>
<span data-ttu-id="b54aa-103">將指定的檔案對應到記憶體中。</span><span class="sxs-lookup"><span data-stu-id="b54aa-103">Maps the specified file into memory.</span></span> <span data-ttu-id="b54aa-104">這個方法已過時。</span><span class="sxs-lookup"><span data-stu-id="b54aa-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b54aa-105">語法</span><span class="sxs-lookup"><span data-stu-id="b54aa-105">Syntax</span></span>  
  
```  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b54aa-106">參數</span><span class="sxs-lookup"><span data-stu-id="b54aa-106">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="b54aa-107">[in]要對應的檔案控制代碼。</span><span class="sxs-lookup"><span data-stu-id="b54aa-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="b54aa-108">[out]要開始進行對應的檔案開始的記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="b54aa-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b54aa-109">需求</span><span class="sxs-lookup"><span data-stu-id="b54aa-109">Requirements</span></span>  
 <span data-ttu-id="b54aa-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b54aa-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b54aa-111">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b54aa-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b54aa-112">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b54aa-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b54aa-113">**.NET framework 版本：** 1.0、 1.1</span><span class="sxs-lookup"><span data-stu-id="b54aa-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b54aa-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="b54aa-114">See Also</span></span>  
 [<span data-ttu-id="b54aa-115">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="b54aa-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
