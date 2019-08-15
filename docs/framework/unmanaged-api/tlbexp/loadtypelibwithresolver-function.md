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
ms.openlocfilehash: 6b9bec757071a98e085ccdeee3fc66bfc07f52bc
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040170"
---
# <a name="loadtypelibwithresolver-function"></a><span data-ttu-id="67272-102">LoadTypeLibWithResolver 函式</span><span class="sxs-lookup"><span data-stu-id="67272-102">LoadTypeLibWithResolver Function</span></span>
<span data-ttu-id="67272-103">載入類型程式庫, 並使用提供的[ITypeLibResolver 介面](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)來解析任何內部參考的類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="67272-103">Loads a type library and uses the supplied [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) to resolve any internally referenced type libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67272-104">語法</span><span class="sxs-lookup"><span data-stu-id="67272-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67272-105">參數</span><span class="sxs-lookup"><span data-stu-id="67272-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="67272-106">在類型程式庫的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="67272-106">[in] The file path of the type library.</span></span>  
  
 `regkind`  
 <span data-ttu-id="67272-107">在[REGKIND 列舉](https://docs.microsoft.com/windows/win32/api/oleauto/ne-oleauto-regkind)旗標, 可控制類型程式庫的註冊方式。</span><span class="sxs-lookup"><span data-stu-id="67272-107">[in] A [REGKIND enumeration](https://docs.microsoft.com/windows/win32/api/oleauto/ne-oleauto-regkind) flag that controls how the type library is registered.</span></span> <span data-ttu-id="67272-108">其可能的值為:</span><span class="sxs-lookup"><span data-stu-id="67272-108">Its possible values are:</span></span>  
  
- <span data-ttu-id="67272-109">`REGKIND_DEFAULT`：使用預設的註冊行為。</span><span class="sxs-lookup"><span data-stu-id="67272-109">`REGKIND_DEFAULT`: Use default registration behavior.</span></span>  
  
- <span data-ttu-id="67272-110">`REGKIND_REGISTER`：註冊此類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="67272-110">`REGKIND_REGISTER`: Register this type library.</span></span>  
  
- <span data-ttu-id="67272-111">`REGKIND_NONE`：不要註冊此類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="67272-111">`REGKIND_NONE`: Do not register this type library.</span></span>  
  
 `pTlbResolver`  
 <span data-ttu-id="67272-112">在[ITypeLibResolver 介面](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)之執行的指標。</span><span class="sxs-lookup"><span data-stu-id="67272-112">[in] A pointer to the implementation of the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).</span></span>  
  
 `pptlib`  
 <span data-ttu-id="67272-113">脫銷正在載入之類型程式庫的參考。</span><span class="sxs-lookup"><span data-stu-id="67272-113">[out] A reference to the type library that is being loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="67272-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="67272-114">Return Value</span></span>  
 <span data-ttu-id="67272-115">下表所列的其中一個 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="67272-115">One of the HRESULT values listed in the following table.</span></span>  
  
|<span data-ttu-id="67272-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="67272-116">Return value</span></span>|<span data-ttu-id="67272-117">意義</span><span class="sxs-lookup"><span data-stu-id="67272-117">Meaning</span></span>|  
|------------------|-------------|  
|`S_OK`|<span data-ttu-id="67272-118">成功。</span><span class="sxs-lookup"><span data-stu-id="67272-118">Success.</span></span>|  
|`E_OUTOFMEMORY`|<span data-ttu-id="67272-119">記憶體不足。</span><span class="sxs-lookup"><span data-stu-id="67272-119">Out of memory.</span></span>|  
|`E_POINTER`|<span data-ttu-id="67272-120">一或多個指標無效。</span><span class="sxs-lookup"><span data-stu-id="67272-120">One or more of the pointers are invalid.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="67272-121">一或多個引數無效。</span><span class="sxs-lookup"><span data-stu-id="67272-121">One or more of the arguments are invalid.</span></span>|  
|`TYPE_E_IOERROR`|<span data-ttu-id="67272-122">函數無法寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="67272-122">The function could not write to the file.</span></span>|  
|`TYPE_E_REGISTRYACCESS`|<span data-ttu-id="67272-123">無法開啟系統註冊資料庫。</span><span class="sxs-lookup"><span data-stu-id="67272-123">The system registration database could not be opened.</span></span>|  
|`TYPE_E_INVALIDSTATE`|<span data-ttu-id="67272-124">無法開啟類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="67272-124">The type library could not be opened.</span></span>|  
|`TYPE_E_CANTLOADLIBRARY`|<span data-ttu-id="67272-125">無法載入類型程式庫或 DLL。</span><span class="sxs-lookup"><span data-stu-id="67272-125">The type library or DLL could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67272-126">備註</span><span class="sxs-lookup"><span data-stu-id="67272-126">Remarks</span></span>  
 <span data-ttu-id="67272-127">[Tlbexp.exe (類型程式庫匯出工具)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)會在元件`LoadTypeLibWithResolver`對類型程式庫轉換過程中呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="67272-127">The [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) calls the `LoadTypeLibWithResolver` function during the assembly-to-type-library conversion process.</span></span>  
  
 <span data-ttu-id="67272-128">此函式會以最少的登錄存取權來載入指定的類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="67272-128">This function loads the specified type library with minimal access to the registry.</span></span> <span data-ttu-id="67272-129">接著, 函式會檢查類型程式庫中是否有內部參考的類型程式庫, 其中每一個都必須載入並加入至父類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="67272-129">The function then examines the type library for internally referenced type libraries, each of which must be loaded and added to the parent type library.</span></span>  
  
 <span data-ttu-id="67272-130">在可以載入參考的類型程式庫之前, 必須先將其參考檔案路徑解析成完整的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="67272-130">Before a referenced type library can be loaded, its reference file path must be resolved to a full file path.</span></span> <span data-ttu-id="67272-131">這項作業是透過[ITypeLibResolver 介面](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)所提供的`pTlbResolver` [ResolveTypeLib 方法](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md)來完成, 它會傳入參數。</span><span class="sxs-lookup"><span data-stu-id="67272-131">This is accomplished through the [ResolveTypeLib method](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) that is provided by the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), which is passed in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="67272-132">已知參考類型程式庫的完整檔案路徑時, `LoadTypeLibWithResolver`函式會載入參考的類型程式庫, 並將其加入至父類型程式庫, 並建立組合的主要類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="67272-132">When the full file path of the referenced type library is known, the `LoadTypeLibWithResolver` function loads and adds the referenced type library to the parent type library, creating a combined master type library.</span></span>  
  
 <span data-ttu-id="67272-133">在函式解析並載入所有內部參考的類型程式庫之後, 它會傳回`pptlib`參數中主要已解析之類型程式庫的參考。</span><span class="sxs-lookup"><span data-stu-id="67272-133">After the function resolves and loads all internally referenced type libraries, it returns a reference to the master resolved type library in the `pptlib` parameter.</span></span>  
  
 <span data-ttu-id="67272-134">函式通常是由[tlbexp.exe (類型程式庫匯出工具)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)所呼叫, 它會在`pTlbResolver`參數中提供自己的內部[ITypeLibResolver 介面](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)實作為。 `LoadTypeLibWithResolver`</span><span class="sxs-lookup"><span data-stu-id="67272-134">The `LoadTypeLibWithResolver` function is generally called by the [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), which supplies its own internal [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementation in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="67272-135">如果您直接`LoadTypeLibWithResolver`呼叫, 就必須提供自己的[ITypeLibResolver 介面](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)執行。</span><span class="sxs-lookup"><span data-stu-id="67272-135">If you call `LoadTypeLibWithResolver` directly, you must supply your own [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67272-136">需求</span><span class="sxs-lookup"><span data-stu-id="67272-136">Requirements</span></span>  
 <span data-ttu-id="67272-137">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="67272-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67272-138">**標頭：** TlbRef。h</span><span class="sxs-lookup"><span data-stu-id="67272-138">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="67272-139">**LIBRARY:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="67272-139">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="67272-140">**.NET Framework 版本:** 3.5、3.0、2。0</span><span class="sxs-lookup"><span data-stu-id="67272-140">**.NET Framework Version:** 3.5, 3.0, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67272-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67272-141">See also</span></span>

- [<span data-ttu-id="67272-142">Tlbexp Helper 函式</span><span class="sxs-lookup"><span data-stu-id="67272-142">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [<span data-ttu-id="67272-143">LoadTypeLibEx 函式</span><span class="sxs-lookup"><span data-stu-id="67272-143">LoadTypeLibEx Function</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
