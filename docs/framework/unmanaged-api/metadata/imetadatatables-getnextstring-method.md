---
title: IMetaDataTables::GetNextString 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextString
helpviewer_keywords:
- IMetaDataTables::GetNextString method [.NET Framework metadata]
- GetNextString method [.NET Framework metadata]
ms.assetid: d9720428-c353-4f07-a7e8-899e106a1b37
topic_type:
- apiref
ms.openlocfilehash: a1cd932051a9ed90a29ff5eeaa818a67104192bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175248"
---
# <a name="imetadatatablesgetnextstring-method"></a><span data-ttu-id="37396-102">IMetaDataTables::GetNextString 方法</span><span class="sxs-lookup"><span data-stu-id="37396-102">IMetaDataTables::GetNextString Method</span></span>
<span data-ttu-id="37396-103">獲取當前表列中下一個字串的索引。</span><span class="sxs-lookup"><span data-stu-id="37396-103">Gets the index of the next string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37396-104">語法</span><span class="sxs-lookup"><span data-stu-id="37396-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextString (
    [in]  ULONG   ixString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37396-105">參數</span><span class="sxs-lookup"><span data-stu-id="37396-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="37396-106">[在]字串表列中的索引值。</span><span class="sxs-lookup"><span data-stu-id="37396-106">[in] The index value from a string table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="37396-107">[出]指向列中下一個字串的索引的指標。</span><span class="sxs-lookup"><span data-stu-id="37396-107">[out] A pointer to the index of the next string in the column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37396-108">需求</span><span class="sxs-lookup"><span data-stu-id="37396-108">Requirements</span></span>  
 <span data-ttu-id="37396-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="37396-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37396-110">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="37396-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="37396-111">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="37396-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="37396-112">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37396-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37396-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37396-113">See also</span></span>

- [<span data-ttu-id="37396-114">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="37396-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="37396-115">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="37396-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
