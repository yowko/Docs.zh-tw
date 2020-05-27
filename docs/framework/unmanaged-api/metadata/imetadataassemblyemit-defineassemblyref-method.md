---
title: IMetaDataAssemblyEmit::DefineAssemblyRef 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssemblyRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssemblyRef
helpviewer_keywords:
- DefineAssemblyRef method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineAssemblyRef method [.NET Framework metadata]
ms.assetid: 0b284b18-0084-4b3a-912a-5ebe9f29c88b
topic_type:
- apiref
ms.openlocfilehash: 612463bca18c23fac0b086adde2d208a0fbc5ae5
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008166"
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a><span data-ttu-id="5ab16-102">IMetaDataAssemblyEmit::DefineAssemblyRef 方法</span><span class="sxs-lookup"><span data-stu-id="5ab16-102">IMetaDataAssemblyEmit::DefineAssemblyRef Method</span></span>
<span data-ttu-id="5ab16-103">為這個組件所參考的組件，建立包含其中繼資料的 `AssemblyRef` 結構，並且傳回關聯的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="5ab16-103">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ab16-104">語法</span><span class="sxs-lookup"><span data-stu-id="5ab16-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineAssemblyRef (  
    [in]  void                *pbPublicKeyOrToken,  
    [in]  ULONG               cbPublicKeyOrToken,  
    [in]  LPCWSTR             szName,  
    [in]  ASSEMBLYMETADATA    pMetaData,  
    [in]  void                *pbHashValue,  
    [in]  ULONG               cbHashValue,  
    [in]  DWORD               dwAssemblyRefFlags,  
    [out] mdAssemblyRef       *pmdar  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ab16-105">參數</span><span class="sxs-lookup"><span data-stu-id="5ab16-105">Parameters</span></span>  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="5ab16-106">在所參考元件之發行者的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="5ab16-106">[in] The public key of the publisher of the referenced assembly.</span></span> <span data-ttu-id="5ab16-107">協助程式函式[StrongNameTokenFromAssembly](../strong-naming/strongnametokenfromassembly-function.md)可以用來取得要當做這個參數傳遞的公開金鑰雜湊。</span><span class="sxs-lookup"><span data-stu-id="5ab16-107">The helper function [StrongNameTokenFromAssembly](../strong-naming/strongnametokenfromassembly-function.md) can be used to get the hash of the public key to pass as this parameter.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="5ab16-108">在的大小（以位元組為單位） `pbPublicKeyOrToken` 。</span><span class="sxs-lookup"><span data-stu-id="5ab16-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="5ab16-109">在元件的人類看得懂的文字名稱。</span><span class="sxs-lookup"><span data-stu-id="5ab16-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="5ab16-110">此值不得超過1024個字元。</span><span class="sxs-lookup"><span data-stu-id="5ab16-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="5ab16-111">在ASSEMBLYMETADATA 實例，其中包含所參考元件的版本、平臺和地區設定資訊。</span><span class="sxs-lookup"><span data-stu-id="5ab16-111">[in] An ASSEMBLYMETADATA instance that contains the version, platform and locale information of the referenced assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="5ab16-112">在與參考元件相關聯的雜湊資料。</span><span class="sxs-lookup"><span data-stu-id="5ab16-112">[in] The hash data associated with the referenced assembly.</span></span> <span data-ttu-id="5ab16-113">選擇性。</span><span class="sxs-lookup"><span data-stu-id="5ab16-113">Optional.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="5ab16-114">在的大小（以位元組為單位） `pbHashValue` 。</span><span class="sxs-lookup"><span data-stu-id="5ab16-114">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="5ab16-115">在[CorAssemblyFlags](corassemblyflags-enumeration.md)值的位元組合，會影響執行引擎的行為。</span><span class="sxs-lookup"><span data-stu-id="5ab16-115">[in] A bitwise combination of [CorAssemblyFlags](corassemblyflags-enumeration.md) values that influence the behavior of the execution engine.</span></span>  
  
 `pmdar`  
 <span data-ttu-id="5ab16-116">脫銷傳回之 `AssemblyRef` 元資料標記的指標。</span><span class="sxs-lookup"><span data-stu-id="5ab16-116">[out] A pointer to the returned `AssemblyRef` metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ab16-117">備註</span><span class="sxs-lookup"><span data-stu-id="5ab16-117">Remarks</span></span>  
 <span data-ttu-id="5ab16-118">`AssemblyRef`這個元件所參考的每個元件都必須定義一個元資料結構。</span><span class="sxs-lookup"><span data-stu-id="5ab16-118">One `AssemblyRef` metadata structure must be defined for each assembly that this assembly references.</span></span>  
  
 <span data-ttu-id="5ab16-119">在執行時間，參考元件的詳細資料會傳遞至元件解析程式，並指出它們代表「為內建」資訊。</span><span class="sxs-lookup"><span data-stu-id="5ab16-119">At run time, the details of a referenced assembly are passed to the assembly resolver with an indication that they represent the "as built" information.</span></span> <span data-ttu-id="5ab16-120">然後，元件解析程式會套用原則。</span><span class="sxs-lookup"><span data-stu-id="5ab16-120">The assembly resolver then applies policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ab16-121">需求</span><span class="sxs-lookup"><span data-stu-id="5ab16-121">Requirements</span></span>  
 <span data-ttu-id="5ab16-122">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5ab16-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ab16-123">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="5ab16-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5ab16-124">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="5ab16-124">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5ab16-125">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ab16-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ab16-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ab16-126">See also</span></span>

- [<span data-ttu-id="5ab16-127">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="5ab16-127">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
