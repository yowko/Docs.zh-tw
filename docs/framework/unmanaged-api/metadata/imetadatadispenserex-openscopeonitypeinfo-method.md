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
ms.openlocfilehash: 8deefe026e32a56d853e173e6a8fa3be942ccd9c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431138"
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="b9d67-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo 方法</span><span class="sxs-lookup"><span data-stu-id="b9d67-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>
<span data-ttu-id="b9d67-103">這個方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="b9d67-103">This method is not implemented.</span></span> <span data-ttu-id="b9d67-104">If called, it returns E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="b9d67-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9d67-105">語法</span><span class="sxs-lookup"><span data-stu-id="b9d67-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9d67-106">參數</span><span class="sxs-lookup"><span data-stu-id="b9d67-106">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="b9d67-107">[in] Pointer to an [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface that provides the type information on which to open the scope.</span><span class="sxs-lookup"><span data-stu-id="b9d67-107">[in] Pointer to an [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="b9d67-108">[in] The open mode flags.</span><span class="sxs-lookup"><span data-stu-id="b9d67-108">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="b9d67-109">[in] The desired interface.</span><span class="sxs-lookup"><span data-stu-id="b9d67-109">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="b9d67-110">[out] Pointer to a pointer to the returned interface.</span><span class="sxs-lookup"><span data-stu-id="b9d67-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9d67-111">需求</span><span class="sxs-lookup"><span data-stu-id="b9d67-111">Requirements</span></span>  
 <span data-ttu-id="b9d67-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9d67-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9d67-113">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b9d67-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b9d67-114">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b9d67-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b9d67-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9d67-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9d67-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="b9d67-116">See also</span></span>

- [<span data-ttu-id="b9d67-117">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="b9d67-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="b9d67-118">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="b9d67-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
