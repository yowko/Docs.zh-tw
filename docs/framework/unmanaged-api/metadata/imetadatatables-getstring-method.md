---
title: "IMetaDataTables::GetString 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetString
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetString
helpviewer_keywords:
- IMetaDataTables::GetString method [.NET Framework metadata]
- GetString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 895c35cf-b95d-4e3b-93b5-cfc1cf9044fc
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c2c0df58d1de7cc7c1eedfdea6c0e698cbd9cb48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="3450c-102">IMetaDataTables::GetString 方法</span><span class="sxs-lookup"><span data-stu-id="3450c-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="3450c-103">取得字串中指定索引處與資料表資料行目前參考的範圍內。</span><span class="sxs-lookup"><span data-stu-id="3450c-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3450c-104">語法</span><span class="sxs-lookup"><span data-stu-id="3450c-104">Syntax</span></span>  
  
```  
HRESULT GetString (   
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3450c-105">參數</span><span class="sxs-lookup"><span data-stu-id="3450c-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="3450c-106">[in]要開始搜尋下一個值索引。</span><span class="sxs-lookup"><span data-stu-id="3450c-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="3450c-107">[out]指標的指標，傳回的字串值。</span><span class="sxs-lookup"><span data-stu-id="3450c-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3450c-108">需求</span><span class="sxs-lookup"><span data-stu-id="3450c-108">Requirements</span></span>  
 <span data-ttu-id="3450c-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3450c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3450c-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3450c-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3450c-111">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3450c-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3450c-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3450c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3450c-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="3450c-113">See Also</span></span>  
 [<span data-ttu-id="3450c-114">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="3450c-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="3450c-115">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="3450c-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
