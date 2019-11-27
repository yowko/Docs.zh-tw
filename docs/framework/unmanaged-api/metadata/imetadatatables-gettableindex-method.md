---
title: IMetaDataTables::GetTableIndex 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetTableIndex
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetTableIndex
helpviewer_keywords:
- GetTableIndex method [.NET Framework metadata]
- IMetaDataTables::GetTableIndex method [.NET Framework metadata]
ms.assetid: c6ec3800-e0d9-4387-afb8-ddc0b818114c
topic_type:
- apiref
ms.openlocfilehash: 48c38288e960ff2e1fe21f30b6eceae8eeaac2da
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434849"
---
# <a name="imetadatatablesgettableindex-method"></a><span data-ttu-id="287be-102">IMetaDataTables::GetTableIndex 方法</span><span class="sxs-lookup"><span data-stu-id="287be-102">IMetaDataTables::GetTableIndex Method</span></span>
<span data-ttu-id="287be-103">取得指定之標記所參考之資料表的索引。</span><span class="sxs-lookup"><span data-stu-id="287be-103">Gets the index for the table referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="287be-104">語法</span><span class="sxs-lookup"><span data-stu-id="287be-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="287be-105">參數</span><span class="sxs-lookup"><span data-stu-id="287be-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="287be-106">在參考資料表的 token。</span><span class="sxs-lookup"><span data-stu-id="287be-106">[in] The token that references the table.</span></span>  
  
 `pixTbl`  
 <span data-ttu-id="287be-107">脫銷參考資料表之傳回索引的指標。</span><span class="sxs-lookup"><span data-stu-id="287be-107">[out] A pointer to the returned index for the referenced table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="287be-108">備註</span><span class="sxs-lookup"><span data-stu-id="287be-108">Remarks</span></span>  
 <span data-ttu-id="287be-109">我們不建議使用這個方法，因為它不會傳回一致的結果。</span><span class="sxs-lookup"><span data-stu-id="287be-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="287be-110">如需 GUID 資料表的詳細資訊，請參閱通用語言基礎結構（CLI）檔，特別是「分割區 II：元資料定義和語法」。</span><span class="sxs-lookup"><span data-stu-id="287be-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="287be-111">您可以線上取得這份文件；請參閱 MSDN 上的 [ECMA C# 和通用語言基礎結構標準](https://go.microsoft.com/fwlink/?LinkID=99212)，以及 Ecma International 網站上的[標準 ECMA-335 - 通用語言基礎結構 (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552)。</span><span class="sxs-lookup"><span data-stu-id="287be-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="287be-112">需求</span><span class="sxs-lookup"><span data-stu-id="287be-112">Requirements</span></span>  
 <span data-ttu-id="287be-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="287be-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="287be-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="287be-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="287be-115">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="287be-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="287be-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="287be-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="287be-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="287be-117">See also</span></span>

- [<span data-ttu-id="287be-118">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="287be-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="287be-119">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="287be-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
