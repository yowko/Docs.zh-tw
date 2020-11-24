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
ms.openlocfilehash: 369335deb67d74ee3cb9fa407533e40716aa3a3a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676854"
---
# <a name="imetadataimportgeteventprops-method"></a><span data-ttu-id="60d0c-102">IMetaDataImport::GetEventProps 方法</span><span class="sxs-lookup"><span data-stu-id="60d0c-102">IMetaDataImport::GetEventProps Method</span></span>

<span data-ttu-id="60d0c-103">取得指定之事件標記所代表事件的中繼資料資訊，包括宣告類型、委派的加入和移除方法，以及任何旗標和其他相關聯的資料。</span><span class="sxs-lookup"><span data-stu-id="60d0c-103">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60d0c-104">語法</span><span class="sxs-lookup"><span data-stu-id="60d0c-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="60d0c-105">參數</span><span class="sxs-lookup"><span data-stu-id="60d0c-105">Parameters</span></span>  

 `ev`  
 <span data-ttu-id="60d0c-106">在代表要取得中繼資料之事件的事件元資料標記。</span><span class="sxs-lookup"><span data-stu-id="60d0c-106">[in] The event metadata token representing the event to get metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="60d0c-107">擴展表示宣告事件之類別的 TypeDef token 指標。</span><span class="sxs-lookup"><span data-stu-id="60d0c-107">[out] A pointer to the TypeDef token representing the class that declares the event.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="60d0c-108">擴展所參考之事件的名稱 `ev` 。</span><span class="sxs-lookup"><span data-stu-id="60d0c-108">[out] The name of the event referenced by `ev`.</span></span>  
  
 `pchEvent`  
 <span data-ttu-id="60d0c-109">在要求的長度（以寬字元為單位） `szEvent` 。</span><span class="sxs-lookup"><span data-stu-id="60d0c-109">[in] The requested length in wide characters of `szEvent`.</span></span>  
  
 `pdwEventFlags`  
 <span data-ttu-id="60d0c-110">擴展傳回的長度（以寬字元為單位） `szEvent` 。</span><span class="sxs-lookup"><span data-stu-id="60d0c-110">[out] The returned length in wide characters of `szEvent`.</span></span>  
  
 `ptkEventType`  
 <span data-ttu-id="60d0c-111">擴展表示事件種類之 TypeRef 或 TypeDef 元資料標記的指標 <xref:System.Delegate> 。</span><span class="sxs-lookup"><span data-stu-id="60d0c-111">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span></span>  
  
 `pmdAddOn`  
 <span data-ttu-id="60d0c-112">擴展元資料標記的指標，表示新增事件處理常式的方法。</span><span class="sxs-lookup"><span data-stu-id="60d0c-112">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span></span>  
  
 `pmdRemoveOn`  
 <span data-ttu-id="60d0c-113">擴展代表移除事件處理常式之方法的元資料標記指標。</span><span class="sxs-lookup"><span data-stu-id="60d0c-113">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span></span>  
  
 `pmdFire`  
 <span data-ttu-id="60d0c-114">擴展代表引發事件之方法的元資料標記指標。</span><span class="sxs-lookup"><span data-stu-id="60d0c-114">[out] A pointer to the metadata token representing the method that raises the event.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="60d0c-115">擴展與事件相關聯之其他方法的 token 指標陣列。</span><span class="sxs-lookup"><span data-stu-id="60d0c-115">[out] An array of token pointers to other methods associated with the event.</span></span>  
  
 `cMax`  
 <span data-ttu-id="60d0c-116">[in] `rmdOtherMethod` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="60d0c-116">[in] The maximum size of the `rmdOtherMethod` array.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="60d0c-117">擴展傳回的權杖數目 `rmdOtherMethod` 。</span><span class="sxs-lookup"><span data-stu-id="60d0c-117">[out] The number of tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60d0c-118">需求</span><span class="sxs-lookup"><span data-stu-id="60d0c-118">Requirements</span></span>  

 <span data-ttu-id="60d0c-119">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="60d0c-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60d0c-120">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="60d0c-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="60d0c-121">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="60d0c-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="60d0c-122">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60d0c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60d0c-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60d0c-123">See also</span></span>

- [<span data-ttu-id="60d0c-124">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="60d0c-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="60d0c-125">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="60d0c-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
