---
title: IMetaDataAssemblyImport::GetFileProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetFileProps
helpviewer_keywords:
- GetFileProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetFileProps method [.NET Framework metadata]
ms.assetid: c5e6216f-ae3d-4697-9688-66b69c1251ec
topic_type:
- apiref
ms.openlocfilehash: 78c192f10f629a0c1316ae7af7fc774819f4de8f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007477"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="6ab81-102">IMetaDataAssemblyImport::GetFileProps 方法</span><span class="sxs-lookup"><span data-stu-id="6ab81-102">IMetaDataAssemblyImport::GetFileProps Method</span></span>
<span data-ttu-id="6ab81-103">取得具有指定之中繼資料簽章之檔案的屬性。</span><span class="sxs-lookup"><span data-stu-id="6ab81-103">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ab81-104">語法</span><span class="sxs-lookup"><span data-stu-id="6ab81-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileProps (  
    [in]  mdFile      mdf,
    [out] LPWSTR      szName,
    [in]  ULONG       cchName,
    [out] ULONG       *pchName,
    [out] const void  **ppbHashValue,
    [out] ULONG       *pcbHashValue,
    [out] DWORD       *pdwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ab81-105">參數</span><span class="sxs-lookup"><span data-stu-id="6ab81-105">Parameters</span></span>  
 `mdf`  
 <span data-ttu-id="6ab81-106">在`mdFile`元資料標記，代表要取得其屬性的檔案。</span><span class="sxs-lookup"><span data-stu-id="6ab81-106">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="6ab81-107">脫銷檔案名的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="6ab81-107">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="6ab81-108">在的大小（以寬字元為單位） `szName` 。</span><span class="sxs-lookup"><span data-stu-id="6ab81-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="6ab81-109">脫銷中實際傳回的寬字元數 `szName` 。</span><span class="sxs-lookup"><span data-stu-id="6ab81-109">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="6ab81-110">脫銷雜湊值的指標。</span><span class="sxs-lookup"><span data-stu-id="6ab81-110">[out] A pointer to the hash value.</span></span> <span data-ttu-id="6ab81-111">這是檔案的雜湊，使用 SHA-1 演算法。</span><span class="sxs-lookup"><span data-stu-id="6ab81-111">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="6ab81-112">脫銷傳回的雜湊值中的寬字元數。</span><span class="sxs-lookup"><span data-stu-id="6ab81-112">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="6ab81-113">脫銷旗標的指標，描述套用至檔案的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="6ab81-113">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="6ab81-114">旗標值是一個或多個[CorFileFlags](corfileflags-enumeration.md)值的組合。</span><span class="sxs-lookup"><span data-stu-id="6ab81-114">The flags value is a combination of one or more [CorFileFlags](corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ab81-115">需求</span><span class="sxs-lookup"><span data-stu-id="6ab81-115">Requirements</span></span>  
 <span data-ttu-id="6ab81-116">**平臺：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6ab81-116">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ab81-117">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="6ab81-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6ab81-118">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="6ab81-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6ab81-119">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ab81-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ab81-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ab81-120">See also</span></span>

- [<span data-ttu-id="6ab81-121">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="6ab81-121">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
