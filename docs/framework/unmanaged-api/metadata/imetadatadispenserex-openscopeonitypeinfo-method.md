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
ms.openlocfilehash: 8e119093800ea0a0119ba25ba38cf2eaf9afe96b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540840"
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="4ad27-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo 方法</span><span class="sxs-lookup"><span data-stu-id="4ad27-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>
<span data-ttu-id="4ad27-103">這個方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="4ad27-103">This method is not implemented.</span></span> <span data-ttu-id="4ad27-104">如果呼叫，則會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="4ad27-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ad27-105">語法</span><span class="sxs-lookup"><span data-stu-id="4ad27-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ad27-106">參數</span><span class="sxs-lookup"><span data-stu-id="4ad27-106">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="4ad27-107">在 [ITypeInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) 介面的指標，提供要在其上開啟範圍的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="4ad27-107">[in] Pointer to an [ITypeInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="4ad27-108">在開啟模式旗標。</span><span class="sxs-lookup"><span data-stu-id="4ad27-108">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="4ad27-109">在所需的介面。</span><span class="sxs-lookup"><span data-stu-id="4ad27-109">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="4ad27-110">擴展傳回之介面指標的指標。</span><span class="sxs-lookup"><span data-stu-id="4ad27-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ad27-111">需求</span><span class="sxs-lookup"><span data-stu-id="4ad27-111">Requirements</span></span>  
 <span data-ttu-id="4ad27-112">**平臺：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4ad27-112">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ad27-113">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="4ad27-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4ad27-114">連結**庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="4ad27-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4ad27-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ad27-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ad27-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ad27-116">See also</span></span>

- [<span data-ttu-id="4ad27-117">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="4ad27-117">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="4ad27-118">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="4ad27-118">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
