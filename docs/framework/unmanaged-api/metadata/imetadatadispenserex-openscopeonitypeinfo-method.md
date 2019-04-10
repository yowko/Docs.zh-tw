---
title: IMetaDataDispenserEx::OpenScopeOnITypeInfo 方法
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.OpenScopeOnITypeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::OpenScopeOnITypeInfo
helpviewer_keywords:
- OpenScopeOnITypeInfo method [.NET Framework metadata]
- IMetaDataDispenserEx::OpenScopeOnITypeInfo method [.NET Framework metadata]
ms.assetid: 3480bbdb-c442-44a0-b7c6-333354503c52
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: deecd9ed4161bbd72e97a6320188961ae76d1e7c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218780"
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="61a11-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo 方法</span><span class="sxs-lookup"><span data-stu-id="61a11-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>
<span data-ttu-id="61a11-103">這個方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="61a11-103">This method is not implemented.</span></span> <span data-ttu-id="61a11-104">如果呼叫，它會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="61a11-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61a11-105">語法</span><span class="sxs-lookup"><span data-stu-id="61a11-105">Syntax</span></span>  
  
```  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61a11-106">參數</span><span class="sxs-lookup"><span data-stu-id="61a11-106">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="61a11-107">[in]指標[ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo)提供要開啟範圍的類型資訊的介面。</span><span class="sxs-lookup"><span data-stu-id="61a11-107">[in] Pointer to an [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="61a11-108">[in]開啟模式的旗標。</span><span class="sxs-lookup"><span data-stu-id="61a11-108">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="61a11-109">[in]所需的介面。</span><span class="sxs-lookup"><span data-stu-id="61a11-109">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="61a11-110">[out]傳回的介面指標的指標。</span><span class="sxs-lookup"><span data-stu-id="61a11-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61a11-111">需求</span><span class="sxs-lookup"><span data-stu-id="61a11-111">Requirements</span></span>  
 <span data-ttu-id="61a11-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="61a11-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61a11-113">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="61a11-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="61a11-114">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="61a11-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="61a11-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="61a11-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="61a11-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61a11-116">See also</span></span>

- [<span data-ttu-id="61a11-117">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="61a11-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="61a11-118">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="61a11-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
