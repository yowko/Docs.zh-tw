---
title: IMetaDataDispenser::OpenScope 方法
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type:
- apiref
ms.openlocfilehash: f2a85bafc3e2f25b2ed6116a46a9938d869dbaae
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726076"
---
# <a name="imetadatadispenseropenscope-method"></a><span data-ttu-id="95b62-102">IMetaDataDispenser::OpenScope 方法</span><span class="sxs-lookup"><span data-stu-id="95b62-102">IMetaDataDispenser::OpenScope Method</span></span>

<span data-ttu-id="95b62-103">開啟現有的磁片上的檔案，並將其中繼資料對應到記憶體。</span><span class="sxs-lookup"><span data-stu-id="95b62-103">Opens an existing, on-disk file and maps its metadata into memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95b62-104">語法</span><span class="sxs-lookup"><span data-stu-id="95b62-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95b62-105">參數</span><span class="sxs-lookup"><span data-stu-id="95b62-105">Parameters</span></span>  

 `szScope`  
 <span data-ttu-id="95b62-106">在要開啟的檔案名。</span><span class="sxs-lookup"><span data-stu-id="95b62-106">[in] The name of the file to be opened.</span></span> <span data-ttu-id="95b62-107">檔案必須包含 common language runtime (CLR) 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="95b62-107">The file must contain common language runtime (CLR) metadata.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="95b62-108">在 [CorOpenFlags](coropenflags-enumeration.md) 列舉的值，用來指定要開啟之)  (讀取、寫入等的模式。</span><span class="sxs-lookup"><span data-stu-id="95b62-108">[in] A value of the [CorOpenFlags](coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="95b62-109">在要傳回之所需中繼資料介面的 IID;呼叫端會使用介面來匯入 (讀取) 或發出 (寫入) 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="95b62-109">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="95b62-110">的值 `riid` 必須指定其中一個「匯入」或「發出」介面。</span><span class="sxs-lookup"><span data-stu-id="95b62-110">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="95b62-111">有效的值為 IID_IMetaDataEmit、IID_IMetaDataImport、IID_IMetaDataAssemblyEmit、IID_IMetaDataAssemblyImport、IID_IMetaDataEmit2 或 IID_IMetaDataImport2。</span><span class="sxs-lookup"><span data-stu-id="95b62-111">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="95b62-112">擴展傳回之介面的指標。</span><span class="sxs-lookup"><span data-stu-id="95b62-112">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95b62-113">備註</span><span class="sxs-lookup"><span data-stu-id="95b62-113">Remarks</span></span>  

 <span data-ttu-id="95b62-114">您可以使用其中一個「匯入」介面的方法來查詢中繼資料的記憶體中複本，或使用其中一個「發出」介面中的方法新增。</span><span class="sxs-lookup"><span data-stu-id="95b62-114">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="95b62-115">如果目標檔案不包含 CLR 中繼資料， `OpenScope` 方法將會失敗。</span><span class="sxs-lookup"><span data-stu-id="95b62-115">If the target file does not contain CLR metadata, the `OpenScope` method will fail.</span></span>  
  
 <span data-ttu-id="95b62-116">在 .NET Framework 版本1.0 和1.1 版中，如果開啟的範圍 `dwOpenFlags` 設為 ofRead，則可以共用。</span><span class="sxs-lookup"><span data-stu-id="95b62-116">In the .NET Framework version 1.0 and version 1.1, if a scope is opened with `dwOpenFlags` set to ofRead, it is eligible for sharing.</span></span> <span data-ttu-id="95b62-117">也就是說，如果後續呼叫 `OpenScope` 傳入先前開啟的檔案名，則會重複使用現有的範圍，並不會建立一組新的資料結構。</span><span class="sxs-lookup"><span data-stu-id="95b62-117">That is, if subsequent calls to `OpenScope` pass in the name of a file that was previously opened, the existing scope is reused and a new set of data structures is not created.</span></span> <span data-ttu-id="95b62-118">不過，這種共用可能會造成問題。</span><span class="sxs-lookup"><span data-stu-id="95b62-118">However, problems can arise due to this sharing.</span></span>  
  
 <span data-ttu-id="95b62-119">在 .NET Framework 2.0 版中， `dwOpenFlags` 已不會再共用以 set To ofRead 開啟的範圍。</span><span class="sxs-lookup"><span data-stu-id="95b62-119">In the .NET Framework version 2.0, scopes opened with `dwOpenFlags` set to ofRead are no longer shared.</span></span> <span data-ttu-id="95b62-120">您可以使用 ofReadOnly 值來允許共用範圍。</span><span class="sxs-lookup"><span data-stu-id="95b62-120">Use the ofReadOnly value to allow the scope to be shared.</span></span> <span data-ttu-id="95b62-121">共用範圍時，使用「讀取/寫入」中繼資料介面的查詢將會失敗。</span><span class="sxs-lookup"><span data-stu-id="95b62-121">When a scope is shared, queries that use "read/write" metadata interfaces will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95b62-122">需求</span><span class="sxs-lookup"><span data-stu-id="95b62-122">Requirements</span></span>  

 <span data-ttu-id="95b62-123">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="95b62-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95b62-124">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="95b62-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="95b62-125">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="95b62-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="95b62-126">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95b62-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95b62-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95b62-127">See also</span></span>

- [<span data-ttu-id="95b62-128">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="95b62-128">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="95b62-129">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="95b62-129">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="95b62-130">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="95b62-130">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="95b62-131">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="95b62-131">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="95b62-132">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="95b62-132">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="95b62-133">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="95b62-133">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="95b62-134">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="95b62-134">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="95b62-135">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="95b62-135">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
