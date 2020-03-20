---
title: IMetaDataAssemblyEmit::DefineFile 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineFile
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineFile method [.NET Framework metadata]
- DefineFile method [.NET Framework metadata]
ms.assetid: c065aadf-c1ca-4981-bde6-597042cb29c4
topic_type:
- apiref
ms.openlocfilehash: cabd6a47e5d6fc2a4cea87b16d349d9c778b3507
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176054"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="fea76-102">IMetaDataAssemblyEmit::DefineFile 方法</span><span class="sxs-lookup"><span data-stu-id="fea76-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="fea76-103">為這個組件所參考的組件，建立包含其中繼資料的 `File` 中繼資料結構，並且傳回關聯的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="fea76-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fea76-104">語法</span><span class="sxs-lookup"><span data-stu-id="fea76-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,
    [in]  const void     *pbHashValue,
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fea76-105">參數</span><span class="sxs-lookup"><span data-stu-id="fea76-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="fea76-106">[在]要使用的檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="fea76-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="fea76-107">[在]指向與程式集關聯的雜湊資料的指標。</span><span class="sxs-lookup"><span data-stu-id="fea76-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="fea76-108">[在]的大小（以位元組為單位）。 `pbHashValue`</span><span class="sxs-lookup"><span data-stu-id="fea76-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="fea76-109">[在]指定屬性設置的值的`FileFlags`位組合。</span><span class="sxs-lookup"><span data-stu-id="fea76-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="fea76-110">[出]指向返回`File`的權杖的指標。</span><span class="sxs-lookup"><span data-stu-id="fea76-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fea76-111">備註</span><span class="sxs-lookup"><span data-stu-id="fea76-111">Remarks</span></span>  
 <span data-ttu-id="fea76-112">必須`File`為生成此程式集時屬於此程式集的每個檔定義一個元資料結構，不包括包含中繼資料的檔。</span><span class="sxs-lookup"><span data-stu-id="fea76-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fea76-113">需求</span><span class="sxs-lookup"><span data-stu-id="fea76-113">Requirements</span></span>  
 <span data-ttu-id="fea76-114">**平臺：** 請參閱[系統要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fea76-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fea76-115">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="fea76-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fea76-116">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fea76-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fea76-117">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fea76-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fea76-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fea76-118">See also</span></span>

- [<span data-ttu-id="fea76-119">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="fea76-119">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
