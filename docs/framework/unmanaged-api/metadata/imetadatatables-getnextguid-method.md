---
title: IMetaDataTables::GetNextGuid 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextGuid
helpviewer_keywords:
- GetNextGuid method [.NET Framework metadata]
- IMetaDataTables::GetNextGuid method [.NET Framework metadata]
ms.assetid: 68f6ea4d-9112-4d6b-93d9-e34f1e2f2496
topic_type:
- apiref
ms.openlocfilehash: d4055975287267d08d2c2224ff6ddaa39fca548d
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937791"
---
# <a name="imetadatatablesgetnextguid-method"></a><span data-ttu-id="135b2-102">IMetaDataTables::GetNextGuid 方法</span><span class="sxs-lookup"><span data-stu-id="135b2-102">IMetaDataTables::GetNextGuid Method</span></span>
<span data-ttu-id="135b2-103">取得目前資料表資料行中下一個 GUID 值的索引。</span><span class="sxs-lookup"><span data-stu-id="135b2-103">Gets the index of the next GUID value in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="135b2-104">語法</span><span class="sxs-lookup"><span data-stu-id="135b2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextGuid (  
    [in]  ULONG   ixGuid,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="135b2-105">參數</span><span class="sxs-lookup"><span data-stu-id="135b2-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="135b2-106">在GUID 資料表資料行的索引值。</span><span class="sxs-lookup"><span data-stu-id="135b2-106">[in] The index value from a GUID table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="135b2-107">脫銷下一個 GUID 值之索引的指標。</span><span class="sxs-lookup"><span data-stu-id="135b2-107">[out] A pointer to the index of the next GUID value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="135b2-108">備註</span><span class="sxs-lookup"><span data-stu-id="135b2-108">Remarks</span></span>  

  <span data-ttu-id="135b2-109">我們不建議使用這個方法，因為它不會傳回一致的結果。</span><span class="sxs-lookup"><span data-stu-id="135b2-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="135b2-110">如需 GUID 資料表的詳細資訊，請參閱通用語言基礎結構（CLI）檔，特別是「分割區 II：元資料定義和語法」。</span><span class="sxs-lookup"><span data-stu-id="135b2-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="135b2-111">檔可從線上取得;請[參閱C# ECMA 和通用語言基礎結構標準](../../../standard/components.md#applicable-standards)和[標準 Ecma-335-通用語言基礎結構（CLI）](http://www.ecma-international.org/publications/standards/Ecma-335.htm)。</span><span class="sxs-lookup"><span data-stu-id="135b2-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="135b2-112">需求</span><span class="sxs-lookup"><span data-stu-id="135b2-112">Requirements</span></span>  
 <span data-ttu-id="135b2-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="135b2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="135b2-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="135b2-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="135b2-115">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="135b2-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="135b2-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="135b2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="135b2-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="135b2-117">See also</span></span>

- [<span data-ttu-id="135b2-118">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="135b2-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="135b2-119">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="135b2-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
