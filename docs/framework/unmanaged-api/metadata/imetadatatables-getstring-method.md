---
title: IMetaDataTables::GetString 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetString
helpviewer_keywords:
- IMetaDataTables::GetString method [.NET Framework metadata]
- GetString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 895c35cf-b95d-4e3b-93b5-cfc1cf9044fc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8fed98521c0609ebd8b5f65885d69c77814e9e85
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119336"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="ea030-102">IMetaDataTables::GetString 方法</span><span class="sxs-lookup"><span data-stu-id="ea030-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="ea030-103">取得字串的指定索引處與資料表資料行中目前參考的範圍。</span><span class="sxs-lookup"><span data-stu-id="ea030-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea030-104">語法</span><span class="sxs-lookup"><span data-stu-id="ea030-104">Syntax</span></span>  
  
```  
HRESULT GetString (   
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea030-105">參數</span><span class="sxs-lookup"><span data-stu-id="ea030-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="ea030-106">[in]要開始搜尋下一個值的索引。</span><span class="sxs-lookup"><span data-stu-id="ea030-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="ea030-107">[out]要傳回的字串值的指標的指標。</span><span class="sxs-lookup"><span data-stu-id="ea030-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea030-108">需求</span><span class="sxs-lookup"><span data-stu-id="ea030-108">Requirements</span></span>  
 <span data-ttu-id="ea030-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ea030-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea030-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ea030-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ea030-111">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ea030-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="ea030-112">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="ea030-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ea030-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea030-113">See also</span></span>

- [<span data-ttu-id="ea030-114">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="ea030-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="ea030-115">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="ea030-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
