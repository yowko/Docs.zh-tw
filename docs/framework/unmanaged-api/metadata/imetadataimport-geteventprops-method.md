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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c87f2212c761dc31a75addabca6970c5497aa2a0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782421"
---
# <a name="imetadataimportgeteventprops-method"></a><span data-ttu-id="80eda-102">IMetaDataImport::GetEventProps 方法</span><span class="sxs-lookup"><span data-stu-id="80eda-102">IMetaDataImport::GetEventProps Method</span></span>
<span data-ttu-id="80eda-103">取得指定的事件語彙基元，包括宣告的型別、 新增和移除方法委派，和任何旗標和其他相關聯的資料所代表的事件的中繼資料資訊。</span><span class="sxs-lookup"><span data-stu-id="80eda-103">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80eda-104">語法</span><span class="sxs-lookup"><span data-stu-id="80eda-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="80eda-105">參數</span><span class="sxs-lookup"><span data-stu-id="80eda-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="80eda-106">[in]事件中繼資料語彙基元，表示要取得中繼資料的事件。</span><span class="sxs-lookup"><span data-stu-id="80eda-106">[in] The event metadata token representing the event to get metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="80eda-107">[out]表示宣告該事件之類別的 TypeDef 語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="80eda-107">[out] A pointer to the TypeDef token representing the class that declares the event.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="80eda-108">[out]所參考的事件名稱`ev`。</span><span class="sxs-lookup"><span data-stu-id="80eda-108">[out] The name of the event referenced by `ev`.</span></span>  
  
 `pchEvent`  
 <span data-ttu-id="80eda-109">[in]所要求的長度，寬字元`szEvent`。</span><span class="sxs-lookup"><span data-stu-id="80eda-109">[in] The requested length in wide characters of `szEvent`.</span></span>  
  
 `pdwEventFlags`  
 <span data-ttu-id="80eda-110">[out]傳回寬字元的長度`szEvent`。</span><span class="sxs-lookup"><span data-stu-id="80eda-110">[out] The returned length in wide characters of `szEvent`.</span></span>  
  
 `ptkEventType`  
 <span data-ttu-id="80eda-111">[out]TypeRef 或 TypeDef 中繼資料語彙基元，代表指標<xref:System.Delegate>事件型別。</span><span class="sxs-lookup"><span data-stu-id="80eda-111">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span></span>  
  
 `pmdAddOn`  
 <span data-ttu-id="80eda-112">[out]表示將事件處理常式方法的中繼資料語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="80eda-112">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span></span>  
  
 `pmdRemoveOn`  
 <span data-ttu-id="80eda-113">[out]表示移除事件處理常式方法的中繼資料語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="80eda-113">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span></span>  
  
 `pmdFire`  
 <span data-ttu-id="80eda-114">[out]表示引發事件的方法中繼資料語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="80eda-114">[out] A pointer to the metadata token representing the method that raises the event.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="80eda-115">[out]與事件相關聯的其他方法的語彙基元指標的陣列。</span><span class="sxs-lookup"><span data-stu-id="80eda-115">[out] An array of token pointers to other methods associated with the event.</span></span>  
  
 `cMax`  
 <span data-ttu-id="80eda-116">[in] `rmdOtherMethod` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="80eda-116">[in] The maximum size of the `rmdOtherMethod` array.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="80eda-117">[out]權杖中傳回的數目`rmdOtherMethod`。</span><span class="sxs-lookup"><span data-stu-id="80eda-117">[out] The number of tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80eda-118">需求</span><span class="sxs-lookup"><span data-stu-id="80eda-118">Requirements</span></span>  
 <span data-ttu-id="80eda-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="80eda-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80eda-120">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="80eda-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="80eda-121">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="80eda-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="80eda-122">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80eda-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80eda-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80eda-123">See also</span></span>

- [<span data-ttu-id="80eda-124">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="80eda-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="80eda-125">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="80eda-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
