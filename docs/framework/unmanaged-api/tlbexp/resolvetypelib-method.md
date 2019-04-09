---
title: ResolveTypeLib 方法
ms.date: 03/30/2017
api_name:
- ResolveTypeLib
api_location:
- tlbref.dll
f1_keywords:
- ResolveTypeLib
helpviewer_keywords:
- ITypeLibResolver::ResolveTypeLib method [.NET Framework]
- ResolveTypeLib method [.NET Framework]
ms.assetid: 95d2aa0d-8eeb-4a9f-a216-5249f7e2c167
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d734f35b5878ec39e4f2159c326283d168e3be2b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197889"
---
# <a name="resolvetypelib-method"></a><span data-ttu-id="7e911-102">ResolveTypeLib 方法</span><span class="sxs-lookup"><span data-stu-id="7e911-102">ResolveTypeLib Method</span></span>
<span data-ttu-id="7e911-103">藉由傳回它的完整的路徑來解析型別程式庫的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="7e911-103">Resolves the simple name of a type library by returning its fully qualified path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e911-104">語法</span><span class="sxs-lookup"><span data-stu-id="7e911-104">Syntax</span></span>  
  
```  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e911-105">參數</span><span class="sxs-lookup"><span data-stu-id="7e911-105">Parameters</span></span>  
 `bstrSimpleName`  
 <span data-ttu-id="7e911-106">[in]A [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) ，其中包含型別程式庫的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="7e911-106">[in] A [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the simple name of the type library.</span></span>  
  
 `tlbid`  
 <span data-ttu-id="7e911-107">[in]指派給類型程式庫在登錄中的 GUID。</span><span class="sxs-lookup"><span data-stu-id="7e911-107">[in] The GUID assigned to the type library in the registry.</span></span>  
  
 `lcid`  
 <span data-ttu-id="7e911-108">[in]當地語系化類型程式庫的識別碼。</span><span class="sxs-lookup"><span data-stu-id="7e911-108">[in] The localization ID of the type library.</span></span>  
  
 `wMajorVersion`  
 <span data-ttu-id="7e911-109">[in]型別程式庫主要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="7e911-109">[in] The major version number of the type library.</span></span> <span data-ttu-id="7e911-110">例如，針對版本*x.y*，主要版本號碼是*x*。</span><span class="sxs-lookup"><span data-stu-id="7e911-110">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `wMinorVersion`  
 <span data-ttu-id="7e911-111">[in]型別程式庫的次要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="7e911-111">[in] The minor version number of the type library.</span></span> <span data-ttu-id="7e911-112">例如，針對版本*x.y*，次要版本號碼是*y*。</span><span class="sxs-lookup"><span data-stu-id="7e911-112">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
 `syskind`  
 <span data-ttu-id="7e911-113">[in]A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind)旗標，以識別作業的環境。</span><span class="sxs-lookup"><span data-stu-id="7e911-113">[in] A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) flag that identifies the operating environment.</span></span> <span data-ttu-id="7e911-114">常見的值為 SYS_WIN32 和 SYS_WIN64。</span><span class="sxs-lookup"><span data-stu-id="7e911-114">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pbstrResolvedTlbName`  
 <span data-ttu-id="7e911-115">[out]指標[BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) ，其中包含在名為的型別程式庫的完整路徑`bstrSimpleName`參數。</span><span class="sxs-lookup"><span data-stu-id="7e911-115">[out] A pointer to a [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e911-116">備註</span><span class="sxs-lookup"><span data-stu-id="7e911-116">Remarks</span></span>  
 <span data-ttu-id="7e911-117">`ResolveTypeLib`方法會呼叫[LoadTypeLibWithResolver 函式](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md)期間[Tlbexp.exe （類型程式庫匯出工具）](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)處理。</span><span class="sxs-lookup"><span data-stu-id="7e911-117">The `ResolveTypeLib` method is called by the [LoadTypeLibWithResolver function](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) during [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) processing.</span></span>  
  
 <span data-ttu-id="7e911-118">這個介面的自訂實作必須傳回[BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) ，其中包含在名為的型別程式庫的完整路徑`bstrSimpleName`參數。</span><span class="sxs-lookup"><span data-stu-id="7e911-118">Custom implementations of this interface must return a [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e911-119">需求</span><span class="sxs-lookup"><span data-stu-id="7e911-119">Requirements</span></span>  
 <span data-ttu-id="7e911-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7e911-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e911-121">**標頭：** TlbRef.idl TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="7e911-121">**Header:** TlbRef.idl, TlbRef.h</span></span>  
  
 <span data-ttu-id="7e911-122">**LIBRARY:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="7e911-122">**Library:** TlbRef.lib</span></span>  
  
 **<span data-ttu-id="7e911-123">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="7e911-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7e911-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e911-124">See also</span></span>

- [<span data-ttu-id="7e911-125">Tlbexp Helper 函式</span><span class="sxs-lookup"><span data-stu-id="7e911-125">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [<span data-ttu-id="7e911-126">LoadTypeLibEx</span><span class="sxs-lookup"><span data-stu-id="7e911-126">LoadTypeLibEx</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
