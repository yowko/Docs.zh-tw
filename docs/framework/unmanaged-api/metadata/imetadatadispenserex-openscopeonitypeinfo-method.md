---
title: "IMetaDataDispenserEx::OpenScopeOnITypeInfo 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.OpenScopeOnITypeInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::OpenScopeOnITypeInfo
helpviewer_keywords:
- OpenScopeOnITypeInfo method [.NET Framework metadata]
- IMetaDataDispenserEx::OpenScopeOnITypeInfo method [.NET Framework metadata]
ms.assetid: 3480bbdb-c442-44a0-b7c6-333354503c52
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e13211a43c42d66fccd88473c8f881b9edd071d5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="5a1a8-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo 方法</span><span class="sxs-lookup"><span data-stu-id="5a1a8-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>
<span data-ttu-id="5a1a8-103">這個方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="5a1a8-103">This method is not implemented.</span></span> <span data-ttu-id="5a1a8-104">如果呼叫，它會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="5a1a8-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a1a8-105">語法</span><span class="sxs-lookup"><span data-stu-id="5a1a8-105">Syntax</span></span>  
  
```  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a1a8-106">參數</span><span class="sxs-lookup"><span data-stu-id="5a1a8-106">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="5a1a8-107">[in]指標[ITypeInfo](http://msdn.microsoft.com/en-us/f3356463-3373-4279-bae1-953378aa2680)提供要開啟範圍的類型資訊的介面。</span><span class="sxs-lookup"><span data-stu-id="5a1a8-107">[in] Pointer to an [ITypeInfo](http://msdn.microsoft.com/en-us/f3356463-3373-4279-bae1-953378aa2680) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="5a1a8-108">[in]開啟模式的旗標。</span><span class="sxs-lookup"><span data-stu-id="5a1a8-108">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="5a1a8-109">[in]所需的介面。</span><span class="sxs-lookup"><span data-stu-id="5a1a8-109">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="5a1a8-110">[out]傳回的介面指標的指標。</span><span class="sxs-lookup"><span data-stu-id="5a1a8-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a1a8-111">需求</span><span class="sxs-lookup"><span data-stu-id="5a1a8-111">Requirements</span></span>  
 <span data-ttu-id="5a1a8-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5a1a8-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a1a8-113">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5a1a8-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5a1a8-114">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5a1a8-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5a1a8-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a1a8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a1a8-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="5a1a8-116">See Also</span></span>  
 [<span data-ttu-id="5a1a8-117">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="5a1a8-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="5a1a8-118">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="5a1a8-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
