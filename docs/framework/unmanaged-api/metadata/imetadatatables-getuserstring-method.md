---
title: IMetaDataTables::GetUserString 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserString
helpviewer_keywords:
- IMetaDataTables::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 35b8f0d6-9aba-4714-adb2-62020a38fb7e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0d7dee3da1967f8a958ea95ab4555f279c962f51
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451791"
---
# <a name="imetadatatablesgetuserstring-method"></a><span data-ttu-id="cb0da-102">IMetaDataTables::GetUserString 方法</span><span class="sxs-lookup"><span data-stu-id="cb0da-102">IMetaDataTables::GetUserString Method</span></span>
<span data-ttu-id="cb0da-103">取得目前範圍中的字串資料行中指定索引處的硬式編碼的字串。</span><span class="sxs-lookup"><span data-stu-id="cb0da-103">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb0da-104">語法</span><span class="sxs-lookup"><span data-stu-id="cb0da-104">Syntax</span></span>  
  
```  
HRESULT GetUserString (  
    [in]  ULONG       ixUserString,  
    [out] ULONG       *pcbData,  
    [out] const void  **ppData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cb0da-105">參數</span><span class="sxs-lookup"><span data-stu-id="cb0da-105">Parameters</span></span>  
 `ixUserString`  
 <span data-ttu-id="cb0da-106">[in]硬式編碼的字串擷取的索引值。</span><span class="sxs-lookup"><span data-stu-id="cb0da-106">[in] The index value from which the hard-coded string will be retrieved.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="cb0da-107">[out]P; 的大小 ointer `ppData`。</span><span class="sxs-lookup"><span data-stu-id="cb0da-107">[out] A p;ointer to the size of `ppData`.</span></span>  
  
 `ppData`  
 <span data-ttu-id="cb0da-108">[out]傳回的字串指標的指標。</span><span class="sxs-lookup"><span data-stu-id="cb0da-108">[out] A pointer to a pointer to the returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb0da-109">需求</span><span class="sxs-lookup"><span data-stu-id="cb0da-109">Requirements</span></span>  
 <span data-ttu-id="cb0da-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cb0da-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb0da-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cb0da-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cb0da-112">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="cb0da-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cb0da-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb0da-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb0da-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb0da-114">See Also</span></span>  
 [<span data-ttu-id="cb0da-115">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="cb0da-115">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="cb0da-116">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="cb0da-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
