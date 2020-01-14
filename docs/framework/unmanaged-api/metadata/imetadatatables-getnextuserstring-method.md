---
title: IMetaDataTables::GetNextUserString 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextUserString
helpviewer_keywords:
- GetNextUserString method [.NET Framework metadata]
- IMetaDataTables::GetNextUserString method [.NET Framework metadata]
ms.assetid: b7cb40ee-67b7-4f4e-8dcc-ee7ac8bc986b
topic_type:
- apiref
ms.openlocfilehash: 6522dbc8e49d612fc4c0d9597a9b5f12edb2cfe1
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937779"
---
# <a name="imetadatatablesgetnextuserstring-method"></a><span data-ttu-id="4f454-102">IMetaDataTables::GetNextUserString 方法</span><span class="sxs-lookup"><span data-stu-id="4f454-102">IMetaDataTables::GetNextUserString Method</span></span>
<span data-ttu-id="4f454-103">取得包含目前資料表資料行中下一個硬式編碼字串的資料列索引。</span><span class="sxs-lookup"><span data-stu-id="4f454-103">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f454-104">語法</span><span class="sxs-lookup"><span data-stu-id="4f454-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextUserString (  
    [in]  ULONG   ixUserString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f454-105">參數</span><span class="sxs-lookup"><span data-stu-id="4f454-105">Parameters</span></span>  
 `ixUserString`  
 <span data-ttu-id="4f454-106">在目前字串資料行中的索引值。</span><span class="sxs-lookup"><span data-stu-id="4f454-106">[in] An index value from the current string column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="4f454-107">脫銷資料行中下一個字串之資料列索引的指標。</span><span class="sxs-lookup"><span data-stu-id="4f454-107">[out] A pointer to the row index of the next string in the column.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f454-108">備註</span><span class="sxs-lookup"><span data-stu-id="4f454-108">Remarks</span></span>  
 <span data-ttu-id="4f454-109">我們不建議使用這個方法，因為它不會傳回一致的結果。</span><span class="sxs-lookup"><span data-stu-id="4f454-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="4f454-110">如需 GUID 資料表的詳細資訊，請參閱通用語言基礎結構（CLI）檔，特別是「分割區 II：元資料定義和語法」。</span><span class="sxs-lookup"><span data-stu-id="4f454-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="4f454-111">檔可從線上取得;請[參閱C# ECMA 和通用語言基礎結構標準](../../../standard/components.md#applicable-standards)和[標準 Ecma-335-通用語言基礎結構（CLI）](http://www.ecma-international.org/publications/standards/Ecma-335.htm)。</span><span class="sxs-lookup"><span data-stu-id="4f454-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f454-112">需求</span><span class="sxs-lookup"><span data-stu-id="4f454-112">Requirements</span></span>  
 <span data-ttu-id="4f454-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4f454-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f454-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="4f454-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4f454-115">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="4f454-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4f454-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f454-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f454-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="4f454-117">See also</span></span>

- [<span data-ttu-id="4f454-118">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="4f454-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="4f454-119">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="4f454-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
