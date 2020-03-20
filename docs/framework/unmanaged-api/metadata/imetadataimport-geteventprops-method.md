---
title: IMetaDataImport::GetEventProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetEventProps
helpviewer_keywords:
- IMetaDataImport::GetEventProps method [.NET Framework metadata]
- GetEventProps method [.NET Framework metadata]
ms.assetid: 5eaf3b4a-92b7-4d5b-97e0-1e83721e0052
topic_type:
- apiref
ms.openlocfilehash: 306c1748b4997309ee15fb7751bc818b0287aaf0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177262"
---
# <a name="imetadataimportgeteventprops-method"></a><span data-ttu-id="91f25-102">IMetaDataImport::GetEventProps 方法</span><span class="sxs-lookup"><span data-stu-id="91f25-102">IMetaDataImport::GetEventProps Method</span></span>
<span data-ttu-id="91f25-103">獲取由指定事件權杖表示的事件的中繼資料資訊，包括聲明類型、代理的添加和刪除方法以及任何標誌和其他關聯資料。</span><span class="sxs-lookup"><span data-stu-id="91f25-103">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91f25-104">語法</span><span class="sxs-lookup"><span data-stu-id="91f25-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventProps (  
   [in]  mdEvent       ev,  
   [out] mdTypeDef     *pClass,
   [out] LPCWSTR       szEvent,
   [in]  ULONG         cchEvent,
   [out] ULONG         *pchEvent,
   [out] DWORD         *pdwEventFlags,  
   [out] mdToken       *ptkEventType,  
   [out] mdMethodDef   *pmdAddOn,
   [out] mdMethodDef   *pmdRemoveOn,
   [out] mdMethodDef   *pmdFire,
   [out] mdMethodDef   rmdOtherMethod[],
   [in]  ULONG         cMax,  
   [out] ULONG         *pcOtherMethod  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91f25-105">參數</span><span class="sxs-lookup"><span data-stu-id="91f25-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="91f25-106">[在]表示要獲取其中繼資料的事件中繼資料權杖。</span><span class="sxs-lookup"><span data-stu-id="91f25-106">[in] The event metadata token representing the event to get metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="91f25-107">[出]指向表示聲明事件的類的 TypeDef 權杖的指標。</span><span class="sxs-lookup"><span data-stu-id="91f25-107">[out] A pointer to the TypeDef token representing the class that declares the event.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="91f25-108">[出]引用`ev`的事件的名稱。</span><span class="sxs-lookup"><span data-stu-id="91f25-108">[out] The name of the event referenced by `ev`.</span></span>  
  
 `pchEvent`  
 <span data-ttu-id="91f25-109">[在]請求的長度以寬字元。 `szEvent`</span><span class="sxs-lookup"><span data-stu-id="91f25-109">[in] The requested length in wide characters of `szEvent`.</span></span>  
  
 `pdwEventFlags`  
 <span data-ttu-id="91f25-110">[出]返回的長度以寬字元。 `szEvent`</span><span class="sxs-lookup"><span data-stu-id="91f25-110">[out] The returned length in wide characters of `szEvent`.</span></span>  
  
 `ptkEventType`  
 <span data-ttu-id="91f25-111">[出]指向表示事件<xref:System.Delegate>類型的 TypeRef 或 TypeDef 中繼資料權杖的指標。</span><span class="sxs-lookup"><span data-stu-id="91f25-111">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span></span>  
  
 `pmdAddOn`  
 <span data-ttu-id="91f25-112">[出]指向中繼資料權杖的指標，表示為事件添加處理常式的方法。</span><span class="sxs-lookup"><span data-stu-id="91f25-112">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span></span>  
  
 `pmdRemoveOn`  
 <span data-ttu-id="91f25-113">[出]指向表示刪除事件處理常式的方法的中繼資料權杖的指標。</span><span class="sxs-lookup"><span data-stu-id="91f25-113">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span></span>  
  
 `pmdFire`  
 <span data-ttu-id="91f25-114">[出]指向表示引發事件的方法的中繼資料權杖的指標。</span><span class="sxs-lookup"><span data-stu-id="91f25-114">[out] A pointer to the metadata token representing the method that raises the event.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="91f25-115">[出]指向與事件關聯的其他方法的權杖指標陣列。</span><span class="sxs-lookup"><span data-stu-id="91f25-115">[out] An array of token pointers to other methods associated with the event.</span></span>  
  
 `cMax`  
 <span data-ttu-id="91f25-116">[in] `rmdOtherMethod` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="91f25-116">[in] The maximum size of the `rmdOtherMethod` array.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="91f25-117">[出]在 中`rmdOtherMethod`返回的權杖數。</span><span class="sxs-lookup"><span data-stu-id="91f25-117">[out] The number of tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91f25-118">需求</span><span class="sxs-lookup"><span data-stu-id="91f25-118">Requirements</span></span>  
 <span data-ttu-id="91f25-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="91f25-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91f25-120">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="91f25-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="91f25-121">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="91f25-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="91f25-122">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91f25-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91f25-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91f25-123">See also</span></span>

- [<span data-ttu-id="91f25-124">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="91f25-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="91f25-125">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="91f25-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
