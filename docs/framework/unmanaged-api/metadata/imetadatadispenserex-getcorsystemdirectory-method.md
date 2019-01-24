---
title: IMetaDataDispenserEx::GetCORSystemDirectory 方法
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.GetCORSystemDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory
helpviewer_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory method [.NET Framework metadata]
- GetCORSystemDirectory method [.NET Framework metadata]
ms.assetid: d9e0f3b6-e106-4820-bada-5bfba34ce360
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3eccb42caa6fdc62b090cd60ff86ad102511883c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629159"
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="36b9f-102">IMetaDataDispenserEx::GetCORSystemDirectory 方法</span><span class="sxs-lookup"><span data-stu-id="36b9f-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>
<span data-ttu-id="36b9f-103">取得儲存目前的 common language runtime (CLR) 的目錄。</span><span class="sxs-lookup"><span data-stu-id="36b9f-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="36b9f-104">這個方法是僅支援使用由跨處理序偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="36b9f-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="36b9f-105">如果從另一個元件呼叫，它會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="36b9f-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36b9f-106">語法</span><span class="sxs-lookup"><span data-stu-id="36b9f-106">Syntax</span></span>  
  
```  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,   
    [in]  DWORD       cchBuffer,   
    [out] DWORD*      pchBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="36b9f-107">參數</span><span class="sxs-lookup"><span data-stu-id="36b9f-107">Parameters</span></span>  
 `szBuffer`  
 <span data-ttu-id="36b9f-108">[out]要接收的目錄名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="36b9f-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="36b9f-109">[in]大小，以位元組為單位的`szBuffer`。</span><span class="sxs-lookup"><span data-stu-id="36b9f-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="36b9f-110">[out]中實際傳回的位元組數目`szBuffer`。</span><span class="sxs-lookup"><span data-stu-id="36b9f-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36b9f-111">需求</span><span class="sxs-lookup"><span data-stu-id="36b9f-111">Requirements</span></span>  
 <span data-ttu-id="36b9f-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="36b9f-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36b9f-113">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="36b9f-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="36b9f-114">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="36b9f-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="36b9f-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36b9f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36b9f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36b9f-116">See also</span></span>
- [<span data-ttu-id="36b9f-117">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="36b9f-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="36b9f-118">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="36b9f-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
