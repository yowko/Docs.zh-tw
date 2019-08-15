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
ms.openlocfilehash: 0f274befe78e45be3e53335572fd9c1e0b401fd3
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040179"
---
# <a name="resolvetypelib-method"></a><span data-ttu-id="83e65-102">ResolveTypeLib 方法</span><span class="sxs-lookup"><span data-stu-id="83e65-102">ResolveTypeLib Method</span></span>
<span data-ttu-id="83e65-103">藉由傳回完整的路徑, 解析類型程式庫的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="83e65-103">Resolves the simple name of a type library by returning its fully qualified path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83e65-104">語法</span><span class="sxs-lookup"><span data-stu-id="83e65-104">Syntax</span></span>  
  
```cpp  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83e65-105">參數</span><span class="sxs-lookup"><span data-stu-id="83e65-105">Parameters</span></span>  
 `bstrSimpleName`  
 <span data-ttu-id="83e65-106">在包含類型程式庫之簡單名稱的[BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) 。</span><span class="sxs-lookup"><span data-stu-id="83e65-106">[in] A [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the simple name of the type library.</span></span>  
  
 `tlbid`  
 <span data-ttu-id="83e65-107">在指派給登錄中類型程式庫的 GUID。</span><span class="sxs-lookup"><span data-stu-id="83e65-107">[in] The GUID assigned to the type library in the registry.</span></span>  
  
 `lcid`  
 <span data-ttu-id="83e65-108">在類型程式庫的當地語系化識別碼。</span><span class="sxs-lookup"><span data-stu-id="83e65-108">[in] The localization ID of the type library.</span></span>  
  
 `wMajorVersion`  
 <span data-ttu-id="83e65-109">在類型程式庫的主要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="83e65-109">[in] The major version number of the type library.</span></span> <span data-ttu-id="83e65-110">例如, 針對版本*x. y*, 主要版本號碼為*x*。</span><span class="sxs-lookup"><span data-stu-id="83e65-110">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `wMinorVersion`  
 <span data-ttu-id="83e65-111">在類型程式庫的次要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="83e65-111">[in] The minor version number of the type library.</span></span> <span data-ttu-id="83e65-112">例如, 針對版本*x. y*, 次要版本號碼為*y*。</span><span class="sxs-lookup"><span data-stu-id="83e65-112">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
 `syskind`  
 <span data-ttu-id="83e65-113">在識別操作環境的[SYSKIND](https://docs.microsoft.com/windows/win32/api/oaidl/ne-oaidl-syskind)旗標。</span><span class="sxs-lookup"><span data-stu-id="83e65-113">[in] A [SYSKIND](https://docs.microsoft.com/windows/win32/api/oaidl/ne-oaidl-syskind) flag that identifies the operating environment.</span></span> <span data-ttu-id="83e65-114">常見的值為 SYS_WIN32 和 SYS_WIN64。</span><span class="sxs-lookup"><span data-stu-id="83e65-114">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pbstrResolvedTlbName`  
 <span data-ttu-id="83e65-115">脫銷[BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr)的指標, 其中包含`bstrSimpleName`參數中所命名之類型程式庫的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="83e65-115">[out] A pointer to a [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83e65-116">備註</span><span class="sxs-lookup"><span data-stu-id="83e65-116">Remarks</span></span>  
 <span data-ttu-id="83e65-117">在[tlbexp.exe (類型程式庫匯出工具)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)處理期間, [LoadTypeLibWithResolver](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md)函式會呼叫方法。`ResolveTypeLib`</span><span class="sxs-lookup"><span data-stu-id="83e65-117">The `ResolveTypeLib` method is called by the [LoadTypeLibWithResolver function](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) during [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) processing.</span></span>  
  
 <span data-ttu-id="83e65-118">此介面的自訂執行必須傳回一個[BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) , 其中包含`bstrSimpleName`參數中所命名之類型程式庫的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="83e65-118">Custom implementations of this interface must return a [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83e65-119">需求</span><span class="sxs-lookup"><span data-stu-id="83e65-119">Requirements</span></span>  
 <span data-ttu-id="83e65-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="83e65-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83e65-121">**標頭：** TlbRef .idl, TlbRef。h</span><span class="sxs-lookup"><span data-stu-id="83e65-121">**Header:** TlbRef.idl, TlbRef.h</span></span>  
  
 <span data-ttu-id="83e65-122">**LIBRARY:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="83e65-122">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="83e65-123">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83e65-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83e65-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83e65-124">See also</span></span>

- [<span data-ttu-id="83e65-125">Tlbexp Helper 函式</span><span class="sxs-lookup"><span data-stu-id="83e65-125">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [<span data-ttu-id="83e65-126">LoadTypeLibEx</span><span class="sxs-lookup"><span data-stu-id="83e65-126">LoadTypeLibEx</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
