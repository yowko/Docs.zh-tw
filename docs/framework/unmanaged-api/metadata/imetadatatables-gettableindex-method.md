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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eebef02babdca5305deaa4ae11e4bca3bf8bf504
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154397"
---
# <a name="imetadatatablesgettableindex-method"></a><span data-ttu-id="c0b03-102">IMetaDataTables::GetTableIndex 方法</span><span class="sxs-lookup"><span data-stu-id="c0b03-102">IMetaDataTables::GetTableIndex Method</span></span>
<span data-ttu-id="c0b03-103">取得指定語彙基元所參考之資料表的索引。</span><span class="sxs-lookup"><span data-stu-id="c0b03-103">Gets the index for the table referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0b03-104">語法</span><span class="sxs-lookup"><span data-stu-id="c0b03-104">Syntax</span></span>  
  
```  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0b03-105">參數</span><span class="sxs-lookup"><span data-stu-id="c0b03-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="c0b03-106">[in]參考資料表的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="c0b03-106">[in] The token that references the table.</span></span>  
  
 `pixTbl`  
 <span data-ttu-id="c0b03-107">[out]傳回的索引所參考之資料表的指標。</span><span class="sxs-lookup"><span data-stu-id="c0b03-107">[out] A pointer to the returned index for the referenced table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0b03-108">備註</span><span class="sxs-lookup"><span data-stu-id="c0b03-108">Remarks</span></span>  
 <span data-ttu-id="c0b03-109">我們不建議使用這個方法，因為它不會傳回一致的結果。</span><span class="sxs-lookup"><span data-stu-id="c0b03-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="c0b03-110">GUID 資料表的相關資訊，請參閱 Common Language Infrastructure (CLI) 文件，特別是 「 第二部分：中繼資料定義和語意 」。</span><span class="sxs-lookup"><span data-stu-id="c0b03-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="c0b03-111">您可以線上取得這份文件；請參閱 MSDN 上的 [ECMA C# 和通用語言基礎結構標準](https://go.microsoft.com/fwlink/?LinkID=99212)，以及 Ecma International 網站上的[標準 ECMA-335 - 通用語言基礎結構 (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552)。</span><span class="sxs-lookup"><span data-stu-id="c0b03-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0b03-112">需求</span><span class="sxs-lookup"><span data-stu-id="c0b03-112">Requirements</span></span>  
 <span data-ttu-id="c0b03-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c0b03-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0b03-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c0b03-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c0b03-115">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c0b03-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="c0b03-116">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="c0b03-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c0b03-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0b03-117">See also</span></span>

- [<span data-ttu-id="c0b03-118">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="c0b03-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="c0b03-119">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="c0b03-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
