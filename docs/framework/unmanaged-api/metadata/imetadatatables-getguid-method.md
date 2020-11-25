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
ms.openlocfilehash: f776ac59ff9bd665dc3bfde74e8a8bb0f8acc89e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702455"
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="eb646-102">IMetaDataTables::GetGuid 方法</span><span class="sxs-lookup"><span data-stu-id="eb646-102">IMetaDataTables::GetGuid Method</span></span>

<span data-ttu-id="eb646-103">從位於指定索引處的資料列取得 GUID。</span><span class="sxs-lookup"><span data-stu-id="eb646-103">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb646-104">語法</span><span class="sxs-lookup"><span data-stu-id="eb646-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuid (
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb646-105">參數</span><span class="sxs-lookup"><span data-stu-id="eb646-105">Parameters</span></span>  

 `ixGuid`  
 <span data-ttu-id="eb646-106">在要從中取得 GUID 之資料列的索引。</span><span class="sxs-lookup"><span data-stu-id="eb646-106">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="eb646-107">擴展GUID 指標的指標。</span><span class="sxs-lookup"><span data-stu-id="eb646-107">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb646-108">備註</span><span class="sxs-lookup"><span data-stu-id="eb646-108">Remarks</span></span>  

  <span data-ttu-id="eb646-109">我們不建議使用此方法，因為它不會傳回一致的結果。</span><span class="sxs-lookup"><span data-stu-id="eb646-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="eb646-110">如需有關 GUID 資料表的詳細資訊，請參閱通用語言基礎結構 (CLI) 檔，特別是「資料分割 II：元資料定義和語義」。</span><span class="sxs-lookup"><span data-stu-id="eb646-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="eb646-111">檔可在線上取得;請參閱 [ECMA c # 和通用語言基礎結構標準](../../../standard/components.md#applicable-standards) 以及 [標準 ECMA-335-通用語言基礎結構 (CLI) ](http://www.ecma-international.org/publications/standards/Ecma-335.htm)。</span><span class="sxs-lookup"><span data-stu-id="eb646-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb646-112">需求</span><span class="sxs-lookup"><span data-stu-id="eb646-112">Requirements</span></span>  

 <span data-ttu-id="eb646-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eb646-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb646-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="eb646-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="eb646-115">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="eb646-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="eb646-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb646-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb646-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb646-117">See also</span></span>

- [<span data-ttu-id="eb646-118">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="eb646-118">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="eb646-119">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="eb646-119">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
