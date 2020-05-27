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
ms.openlocfilehash: 61d81c94e3a9c092b5d45791962635c761e8da8a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008140"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="1172c-102">IMetaDataAssemblyEmit::DefineFile 方法</span><span class="sxs-lookup"><span data-stu-id="1172c-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="1172c-103">為這個組件所參考的組件，建立包含其中繼資料的 `File` 中繼資料結構，並且傳回關聯的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="1172c-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1172c-104">語法</span><span class="sxs-lookup"><span data-stu-id="1172c-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,
    [in]  const void     *pbHashValue,
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1172c-105">參數</span><span class="sxs-lookup"><span data-stu-id="1172c-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="1172c-106">在要使用的檔案名。</span><span class="sxs-lookup"><span data-stu-id="1172c-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="1172c-107">在與元件相關聯之雜湊資料的指標。</span><span class="sxs-lookup"><span data-stu-id="1172c-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="1172c-108">在的大小（以位元組為單位） `pbHashValue` 。</span><span class="sxs-lookup"><span data-stu-id="1172c-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="1172c-109">在值的位元組合 `FileFlags` ，這個組合會指定屬性設定。</span><span class="sxs-lookup"><span data-stu-id="1172c-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="1172c-110">脫銷傳回之標記的指標 `File` 。</span><span class="sxs-lookup"><span data-stu-id="1172c-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1172c-111">備註</span><span class="sxs-lookup"><span data-stu-id="1172c-111">Remarks</span></span>  
 <span data-ttu-id="1172c-112">`File`在建立此元件時，必須針對屬於此元件的每個檔案定義一個元資料結構，但不包括包含中繼資料的檔案。</span><span class="sxs-lookup"><span data-stu-id="1172c-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1172c-113">需求</span><span class="sxs-lookup"><span data-stu-id="1172c-113">Requirements</span></span>  
 <span data-ttu-id="1172c-114">**平臺：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1172c-114">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1172c-115">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="1172c-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1172c-116">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="1172c-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1172c-117">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1172c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1172c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1172c-118">See also</span></span>

- [<span data-ttu-id="1172c-119">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="1172c-119">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
