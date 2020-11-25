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
ms.openlocfilehash: b79dbdd64ac171d1bc4cd30b96ee76b4a853afb6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727246"
---
# <a name="imetadatatablesgetnextstring-method"></a><span data-ttu-id="bb37f-102">IMetaDataTables::GetNextString 方法</span><span class="sxs-lookup"><span data-stu-id="bb37f-102">IMetaDataTables::GetNextString Method</span></span>

<span data-ttu-id="bb37f-103">取得目前資料表資料行中下一個字串的索引。</span><span class="sxs-lookup"><span data-stu-id="bb37f-103">Gets the index of the next string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb37f-104">語法</span><span class="sxs-lookup"><span data-stu-id="bb37f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextString (
    [in]  ULONG   ixString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb37f-105">參數</span><span class="sxs-lookup"><span data-stu-id="bb37f-105">Parameters</span></span>  

 `ixString`  
 <span data-ttu-id="bb37f-106">在字串資料表資料行中的索引值。</span><span class="sxs-lookup"><span data-stu-id="bb37f-106">[in] The index value from a string table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="bb37f-107">擴展資料行中下一個字串的索引指標。</span><span class="sxs-lookup"><span data-stu-id="bb37f-107">[out] A pointer to the index of the next string in the column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb37f-108">需求</span><span class="sxs-lookup"><span data-stu-id="bb37f-108">Requirements</span></span>  

 <span data-ttu-id="bb37f-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bb37f-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb37f-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="bb37f-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bb37f-111">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="bb37f-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bb37f-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb37f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb37f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb37f-113">See also</span></span>

- [<span data-ttu-id="bb37f-114">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="bb37f-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="bb37f-115">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="bb37f-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
