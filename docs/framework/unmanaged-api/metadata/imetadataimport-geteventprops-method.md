---
title: "IMetaDataImport::GetEventProps 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetEventProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetEventProps
helpviewer_keywords:
- IMetaDataImport::GetEventProps method [.NET Framework metadata]
- GetEventProps method [.NET Framework metadata]
ms.assetid: 5eaf3b4a-92b7-4d5b-97e0-1e83721e0052
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9f616e00d79aec864bbb50b168a17e3f131a1aa1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgeteventprops-method"></a><span data-ttu-id="cd52a-102">IMetaDataImport::GetEventProps 方法</span><span class="sxs-lookup"><span data-stu-id="cd52a-102">IMetaDataImport::GetEventProps Method</span></span>
<span data-ttu-id="cd52a-103">取得指定的事件語彙基元，包括宣告類型、 新增和移除方法的委派，以及任何旗標和其他相關聯的資料所代表事件的中繼資料資訊。</span><span class="sxs-lookup"><span data-stu-id="cd52a-103">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd52a-104">語法</span><span class="sxs-lookup"><span data-stu-id="cd52a-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="cd52a-105">參數</span><span class="sxs-lookup"><span data-stu-id="cd52a-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="cd52a-106">[in]事件中繼資料語彙基元，代表要取得的中繼資料的事件。</span><span class="sxs-lookup"><span data-stu-id="cd52a-106">[in] The event metadata token representing the event to get metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="cd52a-107">[out]代表宣告的事件類別的 TypeDef 語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="cd52a-107">[out] A pointer to the TypeDef token representing the class that declares the event.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="cd52a-108">[out]事件所參考的名稱`ev`。</span><span class="sxs-lookup"><span data-stu-id="cd52a-108">[out] The name of the event referenced by `ev`.</span></span>  
  
 `pchEvent`  
 <span data-ttu-id="cd52a-109">[in]所要求的長度，以寬字元`szEvent`。</span><span class="sxs-lookup"><span data-stu-id="cd52a-109">[in] The requested length in wide characters of `szEvent`.</span></span>  
  
 `pdwEventFlags`  
 <span data-ttu-id="cd52a-110">[out]傳回的寬字元的長度`szEvent`。</span><span class="sxs-lookup"><span data-stu-id="cd52a-110">[out] The returned length in wide characters of `szEvent`.</span></span>  
  
 `ptkEventType`  
 <span data-ttu-id="cd52a-111">[out]TypeRef 或 TypeDef 中繼資料語彙基元，代表的指標<xref:System.Delegate>事件型別。</span><span class="sxs-lookup"><span data-stu-id="cd52a-111">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span></span>  
  
 `pmdAddOn`  
 <span data-ttu-id="cd52a-112">[out]代表加入事件處理常式的方法中繼資料語彙基元的指標。</span><span class="sxs-lookup"><span data-stu-id="cd52a-112">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span></span>  
  
 `pmdRemoveOn`  
 <span data-ttu-id="cd52a-113">[out]代表移除事件處理常式的方法中繼資料語彙基元的指標。</span><span class="sxs-lookup"><span data-stu-id="cd52a-113">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span></span>  
  
 `pmdFire`  
 <span data-ttu-id="cd52a-114">[out]代表引發事件的方法中繼資料語彙基元的指標。</span><span class="sxs-lookup"><span data-stu-id="cd52a-114">[out] A pointer to the metadata token representing the method that raises the event.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="cd52a-115">[out]陣列的其他方法與事件相關聯的語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="cd52a-115">[out] An array of token pointers to other methods associated with the event.</span></span>  
  
 `cMax`  
 <span data-ttu-id="cd52a-116">[in] `rmdOtherMethod` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="cd52a-116">[in] The maximum size of the `rmdOtherMethod` array.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="cd52a-117">[out]傳回的 token 數目`rmdOtherMethod`。</span><span class="sxs-lookup"><span data-stu-id="cd52a-117">[out] The number of tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd52a-118">需求</span><span class="sxs-lookup"><span data-stu-id="cd52a-118">Requirements</span></span>  
 <span data-ttu-id="cd52a-119">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cd52a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd52a-120">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cd52a-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cd52a-121">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="cd52a-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cd52a-122">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd52a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd52a-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd52a-123">See Also</span></span>  
 [<span data-ttu-id="cd52a-124">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="cd52a-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="cd52a-125">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="cd52a-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
