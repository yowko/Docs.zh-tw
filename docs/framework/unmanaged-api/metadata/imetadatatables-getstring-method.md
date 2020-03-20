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
ms.openlocfilehash: 216a1f7bd2ff5a596fa7abf7874b5e603d5a9f7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175235"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="d86d7-102">IMetaDataTables::GetString 方法</span><span class="sxs-lookup"><span data-stu-id="d86d7-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="d86d7-103">從當前引用作用域中的表列獲取指定索引處的字串。</span><span class="sxs-lookup"><span data-stu-id="d86d7-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d86d7-104">語法</span><span class="sxs-lookup"><span data-stu-id="d86d7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetString (
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d86d7-105">參數</span><span class="sxs-lookup"><span data-stu-id="d86d7-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="d86d7-106">[在]開始搜索下一個值的索引。</span><span class="sxs-lookup"><span data-stu-id="d86d7-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="d86d7-107">[出]指向返回的字串值的指標。</span><span class="sxs-lookup"><span data-stu-id="d86d7-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d86d7-108">需求</span><span class="sxs-lookup"><span data-stu-id="d86d7-108">Requirements</span></span>  
 <span data-ttu-id="d86d7-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d86d7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d86d7-110">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="d86d7-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d86d7-111">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d86d7-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d86d7-112">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d86d7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d86d7-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d86d7-113">See also</span></span>

- [<span data-ttu-id="d86d7-114">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="d86d7-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="d86d7-115">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="d86d7-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
