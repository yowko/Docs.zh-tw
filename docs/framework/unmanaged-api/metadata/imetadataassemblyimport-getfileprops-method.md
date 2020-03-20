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
ms.openlocfilehash: dae4a36537eeac58ffb17ebc1b78d935ec807cd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175976"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="9731f-102">IMetaDataAssemblyImport::GetFileProps 方法</span><span class="sxs-lookup"><span data-stu-id="9731f-102">IMetaDataAssemblyImport::GetFileProps Method</span></span>
<span data-ttu-id="9731f-103">使用指定的中繼資料簽名獲取檔的屬性。</span><span class="sxs-lookup"><span data-stu-id="9731f-103">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9731f-104">語法</span><span class="sxs-lookup"><span data-stu-id="9731f-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="9731f-105">參數</span><span class="sxs-lookup"><span data-stu-id="9731f-105">Parameters</span></span>  
 `mdf`  
 <span data-ttu-id="9731f-106">[在]表示`mdFile`要為其獲取屬性的檔的中繼資料權杖。</span><span class="sxs-lookup"><span data-stu-id="9731f-106">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="9731f-107">[出]檔的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="9731f-107">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="9731f-108">[在]大字元的大小`szName`。</span><span class="sxs-lookup"><span data-stu-id="9731f-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="9731f-109">[出]中實際返回的寬字元數`szName`。</span><span class="sxs-lookup"><span data-stu-id="9731f-109">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="9731f-110">[出]指向雜湊值的指標。</span><span class="sxs-lookup"><span data-stu-id="9731f-110">[out] A pointer to the hash value.</span></span> <span data-ttu-id="9731f-111">這是使用 SHA-1 演算法的檔雜湊。</span><span class="sxs-lookup"><span data-stu-id="9731f-111">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="9731f-112">[出]返回的雜湊值中的寬字元數。</span><span class="sxs-lookup"><span data-stu-id="9731f-112">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="9731f-113">[出]指向描述應用於檔的中繼資料的標誌的指標。</span><span class="sxs-lookup"><span data-stu-id="9731f-113">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="9731f-114">標誌值是一個或多個[CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md)值的組合。</span><span class="sxs-lookup"><span data-stu-id="9731f-114">The flags value is a combination of one or more [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9731f-115">需求</span><span class="sxs-lookup"><span data-stu-id="9731f-115">Requirements</span></span>  
 <span data-ttu-id="9731f-116">**平臺：** 請參閱[系統要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9731f-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9731f-117">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="9731f-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9731f-118">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9731f-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9731f-119">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9731f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9731f-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9731f-120">See also</span></span>

- [<span data-ttu-id="9731f-121">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="9731f-121">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
