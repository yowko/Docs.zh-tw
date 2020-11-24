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
ms.openlocfilehash: 6056a64b354f69ce39692173da01892870fba9e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682844"
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="c9dc4-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo 方法</span><span class="sxs-lookup"><span data-stu-id="c9dc4-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>

<span data-ttu-id="c9dc4-103">這個方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="c9dc4-103">This method is not implemented.</span></span> <span data-ttu-id="c9dc4-104">如果呼叫，則會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="c9dc4-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9dc4-105">語法</span><span class="sxs-lookup"><span data-stu-id="c9dc4-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9dc4-106">參數</span><span class="sxs-lookup"><span data-stu-id="c9dc4-106">Parameters</span></span>  

 `pITI`  
 <span data-ttu-id="c9dc4-107">在 [ITypeInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) 介面的指標，提供要在其上開啟範圍的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="c9dc4-107">[in] Pointer to an [ITypeInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="c9dc4-108">在開啟模式旗標。</span><span class="sxs-lookup"><span data-stu-id="c9dc4-108">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="c9dc4-109">在所需的介面。</span><span class="sxs-lookup"><span data-stu-id="c9dc4-109">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="c9dc4-110">擴展傳回之介面指標的指標。</span><span class="sxs-lookup"><span data-stu-id="c9dc4-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9dc4-111">需求</span><span class="sxs-lookup"><span data-stu-id="c9dc4-111">Requirements</span></span>  

 <span data-ttu-id="c9dc4-112">**平臺：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c9dc4-112">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9dc4-113">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="c9dc4-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c9dc4-114">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="c9dc4-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c9dc4-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9dc4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9dc4-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9dc4-116">See also</span></span>

- [<span data-ttu-id="c9dc4-117">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="c9dc4-117">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="c9dc4-118">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="c9dc4-118">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
