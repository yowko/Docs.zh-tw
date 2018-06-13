---
title: LoadTypeLibWithResolver 函式
ms.date: 03/30/2017
api_name:
- LoadTypeLibWithResolver
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- LoadTypeLibWithResolver
helpviewer_keywords:
- LoadTypeLibWithResolver function [.NET Framework]
ms.assetid: 7123a89b-eb9b-463a-a552-a081e33b0a3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 751794746e26bd8f0ec2cd6db2f62876e78674e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460271"
---
# <a name="loadtypelibwithresolver-function"></a><span data-ttu-id="78bfa-102">LoadTypeLibWithResolver 函式</span><span class="sxs-lookup"><span data-stu-id="78bfa-102">LoadTypeLibWithResolver Function</span></span>
<span data-ttu-id="78bfa-103">載入類型程式庫，並使用所提供[ITypeLibResolver 介面](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)來解決任何內部參考的類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="78bfa-103">Loads a type library and uses the supplied [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) to resolve any internally referenced type libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78bfa-104">語法</span><span class="sxs-lookup"><span data-stu-id="78bfa-104">Syntax</span></span>  
  
```  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78bfa-105">參數</span><span class="sxs-lookup"><span data-stu-id="78bfa-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="78bfa-106">[in]類型程式庫檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="78bfa-106">[in] The file path of the type library.</span></span>  
  
 `regkind`  
 <span data-ttu-id="78bfa-107">[in]A [REGKIND 列舉](https://msdn.microsoft.com/library/windows/desktop/ms221159.aspx)控制註冊類型程式庫的方式的旗標。</span><span class="sxs-lookup"><span data-stu-id="78bfa-107">[in] A [REGKIND enumeration](https://msdn.microsoft.com/library/windows/desktop/ms221159.aspx) flag that controls how the type library is registered.</span></span> <span data-ttu-id="78bfa-108">其可能的值為：</span><span class="sxs-lookup"><span data-stu-id="78bfa-108">Its possible values are:</span></span>  
  
-   <span data-ttu-id="78bfa-109">`REGKIND_DEFAULT`： 使用預設註冊行為。</span><span class="sxs-lookup"><span data-stu-id="78bfa-109">`REGKIND_DEFAULT`: Use default registration behavior.</span></span>  
  
-   <span data-ttu-id="78bfa-110">`REGKIND_REGISTER`： 註冊此型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="78bfa-110">`REGKIND_REGISTER`: Register this type library.</span></span>  
  
-   <span data-ttu-id="78bfa-111">`REGKIND_NONE`： 不要註冊此型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="78bfa-111">`REGKIND_NONE`: Do not register this type library.</span></span>  
  
 `pTlbResolver`  
 <span data-ttu-id="78bfa-112">[in]指標的實作[ITypeLibResolver 介面](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="78bfa-112">[in] A pointer to the implementation of the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).</span></span>  
  
 `pptlib`  
 <span data-ttu-id="78bfa-113">[out]正在載入類型程式庫的參考。</span><span class="sxs-lookup"><span data-stu-id="78bfa-113">[out] A reference to the type library that is being loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78bfa-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="78bfa-114">Return Value</span></span>  
 <span data-ttu-id="78bfa-115">下表所列的 HRESULT 值的其中一個。</span><span class="sxs-lookup"><span data-stu-id="78bfa-115">One of the HRESULT values listed in the following table.</span></span>  
  
|<span data-ttu-id="78bfa-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="78bfa-116">Return value</span></span>|<span data-ttu-id="78bfa-117">意義</span><span class="sxs-lookup"><span data-stu-id="78bfa-117">Meaning</span></span>|  
|------------------|-------------|  
|`S_OK`|<span data-ttu-id="78bfa-118">成功。</span><span class="sxs-lookup"><span data-stu-id="78bfa-118">Success.</span></span>|  
|`E_OUTOFMEMORY`|<span data-ttu-id="78bfa-119">記憶體不足。</span><span class="sxs-lookup"><span data-stu-id="78bfa-119">Out of memory.</span></span>|  
|`E_POINTER`|<span data-ttu-id="78bfa-120">有一或多個指標無效。</span><span class="sxs-lookup"><span data-stu-id="78bfa-120">One or more of the pointers are invalid.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="78bfa-121">有一或多個引數無效。</span><span class="sxs-lookup"><span data-stu-id="78bfa-121">One or more of the arguments are invalid.</span></span>|  
|`TYPE_E_IOERROR`|<span data-ttu-id="78bfa-122">此函式無法寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="78bfa-122">The function could not write to the file.</span></span>|  
|`TYPE_E_REGISTRYACCESS`|<span data-ttu-id="78bfa-123">無法開啟系統註冊資料庫。</span><span class="sxs-lookup"><span data-stu-id="78bfa-123">The system registration database could not be opened.</span></span>|  
|`TYPE_E_INVALIDSTATE`|<span data-ttu-id="78bfa-124">無法開啟類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="78bfa-124">The type library could not be opened.</span></span>|  
|`TYPE_E_CANTLOADLIBRARY`|<span data-ttu-id="78bfa-125">無法載入類型程式庫或 DLL。</span><span class="sxs-lookup"><span data-stu-id="78bfa-125">The type library or DLL could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78bfa-126">備註</span><span class="sxs-lookup"><span data-stu-id="78bfa-126">Remarks</span></span>  
 <span data-ttu-id="78bfa-127">[Tlbexp.exe （類型程式庫匯出工具）](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)呼叫`LoadTypeLibWithResolver`在組件至類型程式庫轉換過程中的函式。</span><span class="sxs-lookup"><span data-stu-id="78bfa-127">The [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) calls the `LoadTypeLibWithResolver` function during the assembly-to-type-library conversion process.</span></span>  
  
 <span data-ttu-id="78bfa-128">此函式會載入至登錄的最低存取指定的型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="78bfa-128">This function loads the specified type library with minimal access to the registry.</span></span> <span data-ttu-id="78bfa-129">然後，此函式會檢查內部參考的類型程式庫，其中每一個都必須載入並加入至父類型程式庫的類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="78bfa-129">The function then examines the type library for internally referenced type libraries, each of which must be loaded and added to the parent type library.</span></span>  
  
 <span data-ttu-id="78bfa-130">可以載入參考的類型程式庫之前，必須解析其參考檔案路徑的完整檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="78bfa-130">Before a referenced type library can be loaded, its reference file path must be resolved to a full file path.</span></span> <span data-ttu-id="78bfa-131">這是透過[ResolveTypeLib 方法](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md)所提供[ITypeLibResolver 介面](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)，這傳入`pTlbResolver`參數。</span><span class="sxs-lookup"><span data-stu-id="78bfa-131">This is accomplished through the [ResolveTypeLib method](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) that is provided by the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), which is passed in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="78bfa-132">當已知的參考的類型程式庫的完整檔案路徑時，`LoadTypeLibWithResolver`載入函式，並將參考的類型程式庫加入至父類型程式庫建立結合的主要類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="78bfa-132">When the full file path of the referenced type library is known, the `LoadTypeLibWithResolver` function loads and adds the referenced type library to the parent type library, creating a combined master type library.</span></span>  
  
 <span data-ttu-id="78bfa-133">此函式會解析並載入所有內部參考的類型程式庫之後，它會傳回 master 解析的型別程式庫中的參考`pptlib`參數。</span><span class="sxs-lookup"><span data-stu-id="78bfa-133">After the function resolves and loads all internally referenced type libraries, it returns a reference to the master resolved type library in the `pptlib` parameter.</span></span>  
  
 <span data-ttu-id="78bfa-134">`LoadTypeLibWithResolver`函式通常由呼叫[Tlbexp.exe （類型程式庫匯出工具）](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)，提供其自己內部[ITypeLibResolver 介面](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)中的實作`pTlbResolver`參數。</span><span class="sxs-lookup"><span data-stu-id="78bfa-134">The `LoadTypeLibWithResolver` function is generally called by the [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), which supplies its own internal [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementation in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="78bfa-135">如果您呼叫`LoadTypeLibWithResolver`直接管理，您必須提供您自己[ITypeLibResolver 介面](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)實作。</span><span class="sxs-lookup"><span data-stu-id="78bfa-135">If you call `LoadTypeLibWithResolver` directly, you must supply your own [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78bfa-136">需求</span><span class="sxs-lookup"><span data-stu-id="78bfa-136">Requirements</span></span>  
 <span data-ttu-id="78bfa-137">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="78bfa-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78bfa-138">**標頭：** TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="78bfa-138">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="78bfa-139">**程式庫：** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="78bfa-139">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="78bfa-140">**.NET framework 版本：** 3.5、 3.0、 2.0</span><span class="sxs-lookup"><span data-stu-id="78bfa-140">**.NET Framework Version:** 3.5, 3.0, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78bfa-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78bfa-141">See Also</span></span>  
 [<span data-ttu-id="78bfa-142">Tlbexp Helper 函式</span><span class="sxs-lookup"><span data-stu-id="78bfa-142">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 <span data-ttu-id="78bfa-143">[LoadTypeLibEx 函式](https://msdn.microsoft.com/library/windows/desktop/ms221249\(v=vs.85\).aspx)</span><span class="sxs-lookup"><span data-stu-id="78bfa-143">[LoadTypeLibEx Function](https://msdn.microsoft.com/library/windows/desktop/ms221249\(v=vs.85\).aspx)</span></span>
