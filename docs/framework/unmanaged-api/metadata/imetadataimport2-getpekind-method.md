---
title: IMetaDataImport2::GetPEKind 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetPEKind
helpviewer_keywords:
- GetPEKind method [.NET Framework metadata]
- IMetaDataImport2::GetPEKind method [.NET Framework metadata]
ms.assetid: d91c3d89-8022-4a4c-a2a2-a8af2c387507
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a3d0ee533ec0ece308f87c170846ef102bd3a3b9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478853"
---
# <a name="imetadataimport2getpekind-method"></a><span data-ttu-id="80731-102">IMetaDataImport2::GetPEKind 方法</span><span class="sxs-lookup"><span data-stu-id="80731-102">IMetaDataImport2::GetPEKind Method</span></span>
<span data-ttu-id="80731-103">取得值，識別性質之可攜式執行檔 (PE) 中的程式碼檔，通常是 DLL 或 EXE 檔案，定義目前的中繼資料範圍內。</span><span class="sxs-lookup"><span data-stu-id="80731-103">Gets a value identifying the nature of the code in the portable executable (PE) file, typically a DLL or EXE file, that is defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80731-104">語法</span><span class="sxs-lookup"><span data-stu-id="80731-104">Syntax</span></span>  
  
```  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80731-105">參數</span><span class="sxs-lookup"><span data-stu-id="80731-105">Parameters</span></span>  
 `pdwPEKind`  
 <span data-ttu-id="80731-106">[out]值的指標[CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)描述的 PE 檔的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="80731-106">[out] A pointer to a value of the [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) enumeration that describes the PE file.</span></span>  
  
 `pdwMachine`  
 <span data-ttu-id="80731-107">[out]識別電腦架構值的指標。</span><span class="sxs-lookup"><span data-stu-id="80731-107">[out] A pointer to a value that identifies the architecture of the machine.</span></span> <span data-ttu-id="80731-108">請參閱下一節，如需可能值。</span><span class="sxs-lookup"><span data-stu-id="80731-108">See the next section for possible values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80731-109">備註</span><span class="sxs-lookup"><span data-stu-id="80731-109">Remarks</span></span>  
 <span data-ttu-id="80731-110">所參考的值`pdwMachine`參數可以是下列其中之一。</span><span class="sxs-lookup"><span data-stu-id="80731-110">The value referenced by the `pdwMachine` parameter can be one of the following.</span></span>  
  
|<span data-ttu-id="80731-111">值</span><span class="sxs-lookup"><span data-stu-id="80731-111">Value</span></span>|<span data-ttu-id="80731-112">電腦架構</span><span class="sxs-lookup"><span data-stu-id="80731-112">Machine architecture</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="80731-113">IMAGE_FILE_MACHINE_I386</span><span class="sxs-lookup"><span data-stu-id="80731-113">IMAGE_FILE_MACHINE_I386</span></span><br /><br /> <span data-ttu-id="80731-114">0x014C</span><span class="sxs-lookup"><span data-stu-id="80731-114">0x014C</span></span>|<span data-ttu-id="80731-115">x86</span><span class="sxs-lookup"><span data-stu-id="80731-115">x86</span></span>|  
|<span data-ttu-id="80731-116">IMAGE_FILE_MACHINE_IA64</span><span class="sxs-lookup"><span data-stu-id="80731-116">IMAGE_FILE_MACHINE_IA64</span></span><br /><br /> <span data-ttu-id="80731-117">0x0200</span><span class="sxs-lookup"><span data-stu-id="80731-117">0x0200</span></span>|<span data-ttu-id="80731-118">Intel IPF</span><span class="sxs-lookup"><span data-stu-id="80731-118">Intel IPF</span></span>|  
|<span data-ttu-id="80731-119">IMAGE_FILE_MACHINE_AMD64</span><span class="sxs-lookup"><span data-stu-id="80731-119">IMAGE_FILE_MACHINE_AMD64</span></span><br /><br /> <span data-ttu-id="80731-120">0x8664</span><span class="sxs-lookup"><span data-stu-id="80731-120">0x8664</span></span>|<span data-ttu-id="80731-121">X64</span><span class="sxs-lookup"><span data-stu-id="80731-121">x64</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="80731-122">需求</span><span class="sxs-lookup"><span data-stu-id="80731-122">Requirements</span></span>  
 <span data-ttu-id="80731-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="80731-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80731-124">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="80731-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="80731-125">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="80731-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="80731-126">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80731-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80731-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80731-127">See also</span></span>
- [<span data-ttu-id="80731-128">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="80731-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="80731-129">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="80731-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="80731-130">CorPEKind 列舉</span><span class="sxs-lookup"><span data-stu-id="80731-130">CorPEKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)
