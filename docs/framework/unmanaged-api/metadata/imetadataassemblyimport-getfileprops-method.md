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
ms.openlocfilehash: 0b9ff2716cc0bc32c81fe6fcdd4e6c367d4d835f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718172"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="0d25f-102">IMetaDataAssemblyImport::GetFileProps 方法</span><span class="sxs-lookup"><span data-stu-id="0d25f-102">IMetaDataAssemblyImport::GetFileProps Method</span></span>

<span data-ttu-id="0d25f-103">取得具有指定之中繼資料簽章之檔案的屬性。</span><span class="sxs-lookup"><span data-stu-id="0d25f-103">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d25f-104">語法</span><span class="sxs-lookup"><span data-stu-id="0d25f-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="0d25f-105">參數</span><span class="sxs-lookup"><span data-stu-id="0d25f-105">Parameters</span></span>  

 `mdf`  
 <span data-ttu-id="0d25f-106">在 `mdFile` 元資料標記，代表要取得其屬性的檔案。</span><span class="sxs-lookup"><span data-stu-id="0d25f-106">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="0d25f-107">擴展檔案名的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="0d25f-107">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="0d25f-108">在的大小（以寬字元為單位） `szName` 。</span><span class="sxs-lookup"><span data-stu-id="0d25f-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="0d25f-109">擴展實際傳回的寬字元數 `szName` 。</span><span class="sxs-lookup"><span data-stu-id="0d25f-109">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="0d25f-110">擴展雜湊值的指標。</span><span class="sxs-lookup"><span data-stu-id="0d25f-110">[out] A pointer to the hash value.</span></span> <span data-ttu-id="0d25f-111">這是使用 SHA-1 演算法的檔案雜湊。</span><span class="sxs-lookup"><span data-stu-id="0d25f-111">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="0d25f-112">擴展傳回的雜湊值中的寬字元數。</span><span class="sxs-lookup"><span data-stu-id="0d25f-112">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="0d25f-113">擴展旗標的指標，描述套用至檔案的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="0d25f-113">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="0d25f-114">旗標值是一或多個 [CorFileFlags](corfileflags-enumeration.md) 值的組合。</span><span class="sxs-lookup"><span data-stu-id="0d25f-114">The flags value is a combination of one or more [CorFileFlags](corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d25f-115">需求</span><span class="sxs-lookup"><span data-stu-id="0d25f-115">Requirements</span></span>  

 <span data-ttu-id="0d25f-116">**平臺：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0d25f-116">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d25f-117">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="0d25f-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0d25f-118">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="0d25f-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0d25f-119">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d25f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d25f-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d25f-120">See also</span></span>

- [<span data-ttu-id="0d25f-121">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="0d25f-121">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
