---
title: "IMetaDataDispenserEx::GetCORSystemDirectory 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.GetCORSystemDirectory
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::GetCORSystemDirectory
helpviewer_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory method [.NET Framework metadata]
- GetCORSystemDirectory method [.NET Framework metadata]
ms.assetid: d9e0f3b6-e106-4820-bada-5bfba34ce360
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a876d6ffb8331ee52789d5c146db7615d352dc1b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="6b39b-102">IMetaDataDispenserEx::GetCORSystemDirectory 方法</span><span class="sxs-lookup"><span data-stu-id="6b39b-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>
<span data-ttu-id="6b39b-103">取得儲存目前的 common language runtime (CLR) 的目錄。</span><span class="sxs-lookup"><span data-stu-id="6b39b-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="6b39b-104">這個方法是僅支援使用由跨處理序偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="6b39b-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="6b39b-105">如果已從另一個元件呼叫，它會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="6b39b-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b39b-106">語法</span><span class="sxs-lookup"><span data-stu-id="6b39b-106">Syntax</span></span>  
  
```  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,   
    [in]  DWORD       cchBuffer,   
    [out] DWORD*      pchBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b39b-107">參數</span><span class="sxs-lookup"><span data-stu-id="6b39b-107">Parameters</span></span>  
 `szBuffer`  
 <span data-ttu-id="6b39b-108">[out]要接收的目錄名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="6b39b-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="6b39b-109">[in]大小，以位元組為單位的`szBuffer`。</span><span class="sxs-lookup"><span data-stu-id="6b39b-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="6b39b-110">[out]中實際傳回的位元組數目`szBuffer`。</span><span class="sxs-lookup"><span data-stu-id="6b39b-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b39b-111">需求</span><span class="sxs-lookup"><span data-stu-id="6b39b-111">Requirements</span></span>  
 <span data-ttu-id="6b39b-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6b39b-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b39b-113">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6b39b-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6b39b-114">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6b39b-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6b39b-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b39b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b39b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b39b-116">See Also</span></span>  
 [<span data-ttu-id="6b39b-117">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="6b39b-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="6b39b-118">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="6b39b-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
