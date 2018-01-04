---
title: "IMetaDataImport2::GetPEKind 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.GetPEKind
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::GetPEKind
helpviewer_keywords:
- GetPEKind method [.NET Framework metadata]
- IMetaDataImport2::GetPEKind method [.NET Framework metadata]
ms.assetid: d91c3d89-8022-4a4c-a2a2-a8af2c387507
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e8dc31877ba3550fa8faf610b831dfd2e7b313ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimport2getpekind-method"></a><span data-ttu-id="4ad7d-102">IMetaDataImport2::GetPEKind 方法</span><span class="sxs-lookup"><span data-stu-id="4ad7d-102">IMetaDataImport2::GetPEKind Method</span></span>
<span data-ttu-id="4ad7d-103">取得值，識別可攜式執行檔 (PE) 中的程式碼的本質檔，通常是 DLL 或 EXE 檔案，定義目前的中繼資料範圍內。</span><span class="sxs-lookup"><span data-stu-id="4ad7d-103">Gets a value identifying the nature of the code in the portable executable (PE) file, typically a DLL or EXE file, that is defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ad7d-104">語法</span><span class="sxs-lookup"><span data-stu-id="4ad7d-104">Syntax</span></span>  
  
```  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4ad7d-105">參數</span><span class="sxs-lookup"><span data-stu-id="4ad7d-105">Parameters</span></span>  
 `pdwPEKind`  
 <span data-ttu-id="4ad7d-106">[out]值的指標[CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)描述的 PE 檔的列舉。</span><span class="sxs-lookup"><span data-stu-id="4ad7d-106">[out] A pointer to a value of the [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) enumeration that describes the PE file.</span></span>  
  
 `pdwMachine`  
 <span data-ttu-id="4ad7d-107">[out]指向的值，識別電腦的架構。</span><span class="sxs-lookup"><span data-stu-id="4ad7d-107">[out] A pointer to a value that identifies the architecture of the machine.</span></span> <span data-ttu-id="4ad7d-108">請參閱下一節提供可能的值。</span><span class="sxs-lookup"><span data-stu-id="4ad7d-108">See the next section for possible values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ad7d-109">備註</span><span class="sxs-lookup"><span data-stu-id="4ad7d-109">Remarks</span></span>  
 <span data-ttu-id="4ad7d-110">所參考的值`pdwMachine`參數可以是下列其中之一。</span><span class="sxs-lookup"><span data-stu-id="4ad7d-110">The value referenced by the `pdwMachine` parameter can be one of the following.</span></span>  
  
|<span data-ttu-id="4ad7d-111">值</span><span class="sxs-lookup"><span data-stu-id="4ad7d-111">Value</span></span>|<span data-ttu-id="4ad7d-112">電腦架構</span><span class="sxs-lookup"><span data-stu-id="4ad7d-112">Machine architecture</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="4ad7d-113">IMAGE_FILE_MACHINE_I386</span><span class="sxs-lookup"><span data-stu-id="4ad7d-113">IMAGE_FILE_MACHINE_I386</span></span><br /><br /> <span data-ttu-id="4ad7d-114">0x014C</span><span class="sxs-lookup"><span data-stu-id="4ad7d-114">0x014C</span></span>|<span data-ttu-id="4ad7d-115">x86</span><span class="sxs-lookup"><span data-stu-id="4ad7d-115">x86</span></span>|  
|<span data-ttu-id="4ad7d-116">IMAGE_FILE_MACHINE_IA64</span><span class="sxs-lookup"><span data-stu-id="4ad7d-116">IMAGE_FILE_MACHINE_IA64</span></span><br /><br /> <span data-ttu-id="4ad7d-117">0x0200</span><span class="sxs-lookup"><span data-stu-id="4ad7d-117">0x0200</span></span>|<span data-ttu-id="4ad7d-118">Intel IPF</span><span class="sxs-lookup"><span data-stu-id="4ad7d-118">Intel IPF</span></span>|  
|<span data-ttu-id="4ad7d-119">IMAGE_FILE_MACHINE_AMD64</span><span class="sxs-lookup"><span data-stu-id="4ad7d-119">IMAGE_FILE_MACHINE_AMD64</span></span><br /><br /> <span data-ttu-id="4ad7d-120">0x8664</span><span class="sxs-lookup"><span data-stu-id="4ad7d-120">0x8664</span></span>|<span data-ttu-id="4ad7d-121">X64</span><span class="sxs-lookup"><span data-stu-id="4ad7d-121">x64</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4ad7d-122">需求</span><span class="sxs-lookup"><span data-stu-id="4ad7d-122">Requirements</span></span>  
 <span data-ttu-id="4ad7d-123">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4ad7d-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ad7d-124">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4ad7d-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4ad7d-125">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4ad7d-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4ad7d-126">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ad7d-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ad7d-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="4ad7d-127">See Also</span></span>  
 [<span data-ttu-id="4ad7d-128">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="4ad7d-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="4ad7d-129">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="4ad7d-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="4ad7d-130">CorPEKind 列舉</span><span class="sxs-lookup"><span data-stu-id="4ad7d-130">CorPEKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)
