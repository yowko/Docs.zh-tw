---
title: IMetaDataTables::GetGuid 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type:
- apiref
ms.openlocfilehash: 1f0c52efd4b55d19cbd7b2407c4b2d7c893b1009
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436081"
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="01e50-102">IMetaDataTables::GetGuid 方法</span><span class="sxs-lookup"><span data-stu-id="01e50-102">IMetaDataTables::GetGuid Method</span></span>
<span data-ttu-id="01e50-103">從指定索引處的資料列取得 GUID。</span><span class="sxs-lookup"><span data-stu-id="01e50-103">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01e50-104">語法</span><span class="sxs-lookup"><span data-stu-id="01e50-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuid (   
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01e50-105">參數</span><span class="sxs-lookup"><span data-stu-id="01e50-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="01e50-106">在要從中取得 GUID 的資料列索引。</span><span class="sxs-lookup"><span data-stu-id="01e50-106">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="01e50-107">脫銷GUID 指標的指標。</span><span class="sxs-lookup"><span data-stu-id="01e50-107">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01e50-108">備註</span><span class="sxs-lookup"><span data-stu-id="01e50-108">Remarks</span></span>  
 <span data-ttu-id="01e50-109">我們不建議使用這個方法，因為它不會傳回一致的結果。</span><span class="sxs-lookup"><span data-stu-id="01e50-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="01e50-110">如需 GUID 資料表的詳細資訊，請參閱通用語言基礎結構（CLI）檔，特別是「分割區 II：元資料定義和語法」。</span><span class="sxs-lookup"><span data-stu-id="01e50-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="01e50-111">您可以線上取得這份文件；請參閱 MSDN 上的 [ECMA C# 和通用語言基礎結構標準](https://go.microsoft.com/fwlink/?LinkID=99212)，以及 Ecma International 網站上的[標準 ECMA-335 - 通用語言基礎結構 (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552)。</span><span class="sxs-lookup"><span data-stu-id="01e50-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01e50-112">需求</span><span class="sxs-lookup"><span data-stu-id="01e50-112">Requirements</span></span>  
 <span data-ttu-id="01e50-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="01e50-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01e50-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="01e50-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="01e50-115">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="01e50-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="01e50-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01e50-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01e50-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="01e50-117">See also</span></span>

- [<span data-ttu-id="01e50-118">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="01e50-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="01e50-119">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="01e50-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
