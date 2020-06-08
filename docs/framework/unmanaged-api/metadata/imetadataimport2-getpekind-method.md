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
ms.openlocfilehash: 3626998c456e23fb922ae45a68bedb0e45a7ccba
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490428"
---
# <a name="imetadataimport2getpekind-method"></a><span data-ttu-id="c1891-102">IMetaDataImport2::GetPEKind 方法</span><span class="sxs-lookup"><span data-stu-id="c1891-102">IMetaDataImport2::GetPEKind Method</span></span>
<span data-ttu-id="c1891-103">取得值，識別在目前中繼資料範圍中定義的可移植執行檔（PE）（通常是 DLL 或 EXE 檔案）中的程式碼本質。</span><span class="sxs-lookup"><span data-stu-id="c1891-103">Gets a value identifying the nature of the code in the portable executable (PE) file, typically a DLL or EXE file, that is defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1891-104">語法</span><span class="sxs-lookup"><span data-stu-id="c1891-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1891-105">參數</span><span class="sxs-lookup"><span data-stu-id="c1891-105">Parameters</span></span>  
 `pdwPEKind`  
 <span data-ttu-id="c1891-106">脫銷描述 PE 檔案之[CorPEKind](corpekind-enumeration.md)列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="c1891-106">[out] A pointer to a value of the [CorPEKind](corpekind-enumeration.md) enumeration that describes the PE file.</span></span>  
  
 `pdwMachine`  
 <span data-ttu-id="c1891-107">脫銷識別機器架構的值指標。</span><span class="sxs-lookup"><span data-stu-id="c1891-107">[out] A pointer to a value that identifies the architecture of the machine.</span></span> <span data-ttu-id="c1891-108">如需可能的值，請參閱下一節。</span><span class="sxs-lookup"><span data-stu-id="c1891-108">See the next section for possible values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1891-109">備註</span><span class="sxs-lookup"><span data-stu-id="c1891-109">Remarks</span></span>  
 <span data-ttu-id="c1891-110">參數所參考的值 `pdwMachine` 可以是下列其中一項。</span><span class="sxs-lookup"><span data-stu-id="c1891-110">The value referenced by the `pdwMachine` parameter can be one of the following.</span></span>  
  
|<span data-ttu-id="c1891-111">值</span><span class="sxs-lookup"><span data-stu-id="c1891-111">Value</span></span>|<span data-ttu-id="c1891-112">電腦架構</span><span class="sxs-lookup"><span data-stu-id="c1891-112">Machine architecture</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="c1891-113">IMAGE_FILE_MACHINE_I386</span><span class="sxs-lookup"><span data-stu-id="c1891-113">IMAGE_FILE_MACHINE_I386</span></span><br /><br /> <span data-ttu-id="c1891-114">0x014C</span><span class="sxs-lookup"><span data-stu-id="c1891-114">0x014C</span></span>|<span data-ttu-id="c1891-115">x86</span><span class="sxs-lookup"><span data-stu-id="c1891-115">x86</span></span>|  
|<span data-ttu-id="c1891-116">IMAGE_FILE_MACHINE_IA64</span><span class="sxs-lookup"><span data-stu-id="c1891-116">IMAGE_FILE_MACHINE_IA64</span></span><br /><br /> <span data-ttu-id="c1891-117">0x0200</span><span class="sxs-lookup"><span data-stu-id="c1891-117">0x0200</span></span>|<span data-ttu-id="c1891-118">Intel IPF</span><span class="sxs-lookup"><span data-stu-id="c1891-118">Intel IPF</span></span>|  
|<span data-ttu-id="c1891-119">IMAGE_FILE_MACHINE_AMD64</span><span class="sxs-lookup"><span data-stu-id="c1891-119">IMAGE_FILE_MACHINE_AMD64</span></span><br /><br /> <span data-ttu-id="c1891-120">0x8664</span><span class="sxs-lookup"><span data-stu-id="c1891-120">0x8664</span></span>|<span data-ttu-id="c1891-121">x64</span><span class="sxs-lookup"><span data-stu-id="c1891-121">x64</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c1891-122">規格需求</span><span class="sxs-lookup"><span data-stu-id="c1891-122">Requirements</span></span>  
 <span data-ttu-id="c1891-123">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c1891-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1891-124">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="c1891-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c1891-125">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="c1891-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c1891-126">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1891-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1891-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1891-127">See also</span></span>

- [<span data-ttu-id="c1891-128">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="c1891-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="c1891-129">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="c1891-129">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="c1891-130">CorPEKind 列舉</span><span class="sxs-lookup"><span data-stu-id="c1891-130">CorPEKind Enumeration</span></span>](corpekind-enumeration.md)
