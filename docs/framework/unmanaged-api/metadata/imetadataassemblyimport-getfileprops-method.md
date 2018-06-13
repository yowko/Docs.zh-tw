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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f147fef90d7a9033bdfd07b75e5c33efd2c6881f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444512"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="634e2-102">IMetaDataAssemblyImport::GetFileProps 方法</span><span class="sxs-lookup"><span data-stu-id="634e2-102">IMetaDataAssemblyImport::GetFileProps Method</span></span>
<span data-ttu-id="634e2-103">取得與指定的中繼資料簽章檔案的屬性。</span><span class="sxs-lookup"><span data-stu-id="634e2-103">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="634e2-104">語法</span><span class="sxs-lookup"><span data-stu-id="634e2-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="634e2-105">參數</span><span class="sxs-lookup"><span data-stu-id="634e2-105">Parameters</span></span>  
 `mdf`  
 <span data-ttu-id="634e2-106">[in]`mdFile`中繼資料語彙基元，代表要取得屬性的檔案。</span><span class="sxs-lookup"><span data-stu-id="634e2-106">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="634e2-107">[out]檔案的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="634e2-107">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="634e2-108">[in]大小，以寬字元的`szName`。</span><span class="sxs-lookup"><span data-stu-id="634e2-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="634e2-109">[out]中實際傳回的寬字元數目`szName`。</span><span class="sxs-lookup"><span data-stu-id="634e2-109">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="634e2-110">[out]雜湊值的指標。</span><span class="sxs-lookup"><span data-stu-id="634e2-110">[out] A pointer to the hash value.</span></span> <span data-ttu-id="634e2-111">這是雜湊，並使用 sha-1 演算法的檔案。</span><span class="sxs-lookup"><span data-stu-id="634e2-111">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="634e2-112">[out]傳回雜湊值中的寬字元數目。</span><span class="sxs-lookup"><span data-stu-id="634e2-112">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="634e2-113">[out]描述套用至檔案的中繼資料的旗標指標。</span><span class="sxs-lookup"><span data-stu-id="634e2-113">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="634e2-114">旗標值是一或多個組合[CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md)值。</span><span class="sxs-lookup"><span data-stu-id="634e2-114">The flags value is a combination of one or more [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="634e2-115">需求</span><span class="sxs-lookup"><span data-stu-id="634e2-115">Requirements</span></span>  
 <span data-ttu-id="634e2-116">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="634e2-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="634e2-117">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="634e2-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="634e2-118">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="634e2-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="634e2-119">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="634e2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="634e2-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="634e2-120">See Also</span></span>  
 [<span data-ttu-id="634e2-121">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="634e2-121">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
