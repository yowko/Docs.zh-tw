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
ms.openlocfilehash: 52d70a76bdf8380d320edb6e8188443070a36b1b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672548"
---
# <a name="imetadatatablesgettableindex-method"></a><span data-ttu-id="37e56-102">IMetaDataTables::GetTableIndex 方法</span><span class="sxs-lookup"><span data-stu-id="37e56-102">IMetaDataTables::GetTableIndex Method</span></span>

<span data-ttu-id="37e56-103">取得指定之標記所參考之資料表的索引。</span><span class="sxs-lookup"><span data-stu-id="37e56-103">Gets the index for the table referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37e56-104">語法</span><span class="sxs-lookup"><span data-stu-id="37e56-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37e56-105">參數</span><span class="sxs-lookup"><span data-stu-id="37e56-105">Parameters</span></span>  

 `token`  
 <span data-ttu-id="37e56-106">在參考資料表的 token。</span><span class="sxs-lookup"><span data-stu-id="37e56-106">[in] The token that references the table.</span></span>  
  
 `pixTbl`  
 <span data-ttu-id="37e56-107">擴展參考資料表之傳回索引的指標。</span><span class="sxs-lookup"><span data-stu-id="37e56-107">[out] A pointer to the returned index for the referenced table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37e56-108">備註</span><span class="sxs-lookup"><span data-stu-id="37e56-108">Remarks</span></span>  

 <span data-ttu-id="37e56-109">我們不建議使用此方法，因為它不會傳回一致的結果。</span><span class="sxs-lookup"><span data-stu-id="37e56-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="37e56-110">如需有關 GUID 資料表的詳細資訊，請參閱通用語言基礎結構 (CLI) 檔，特別是「資料分割 II：元資料定義和語義」。</span><span class="sxs-lookup"><span data-stu-id="37e56-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="37e56-111">檔可在線上取得;請參閱 [ECMA c # 和通用語言基礎結構標準](../../../standard/components.md#applicable-standards) 以及 [標準 ECMA-335-通用語言基礎結構 (CLI) ](http://www.ecma-international.org/publications/standards/Ecma-335.htm)。</span><span class="sxs-lookup"><span data-stu-id="37e56-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37e56-112">需求</span><span class="sxs-lookup"><span data-stu-id="37e56-112">Requirements</span></span>  

 <span data-ttu-id="37e56-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="37e56-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37e56-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="37e56-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="37e56-115">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="37e56-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="37e56-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37e56-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37e56-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37e56-117">See also</span></span>

- [<span data-ttu-id="37e56-118">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="37e56-118">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="37e56-119">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="37e56-119">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
