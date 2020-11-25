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
ms.openlocfilehash: 84eea78b9c2e73e24238a5ecbc9442f3d63dbd4e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719784"
---
# <a name="resolvetypelib-method"></a><span data-ttu-id="d96b9-102">ResolveTypeLib 方法</span><span class="sxs-lookup"><span data-stu-id="d96b9-102">ResolveTypeLib Method</span></span>

<span data-ttu-id="d96b9-103">傳回類型程式庫的完整路徑，以解析其簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="d96b9-103">Resolves the simple name of a type library by returning its fully qualified path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d96b9-104">語法</span><span class="sxs-lookup"><span data-stu-id="d96b9-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d96b9-105">參數</span><span class="sxs-lookup"><span data-stu-id="d96b9-105">Parameters</span></span>  

 `bstrSimpleName`  
 <span data-ttu-id="d96b9-106">在包含類型程式庫之簡單名稱的 [BSTR](/previous-versions/windows/desktop/automat/bstr) 。</span><span class="sxs-lookup"><span data-stu-id="d96b9-106">[in] A [BSTR](/previous-versions/windows/desktop/automat/bstr) that contains the simple name of the type library.</span></span>  
  
 `tlbid`  
 <span data-ttu-id="d96b9-107">在指派給登錄中類型程式庫的 GUID。</span><span class="sxs-lookup"><span data-stu-id="d96b9-107">[in] The GUID assigned to the type library in the registry.</span></span>  
  
 `lcid`  
 <span data-ttu-id="d96b9-108">在類型程式庫的當地語系化識別碼。</span><span class="sxs-lookup"><span data-stu-id="d96b9-108">[in] The localization ID of the type library.</span></span>  
  
 `wMajorVersion`  
 <span data-ttu-id="d96b9-109">在類型程式庫的主要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="d96b9-109">[in] The major version number of the type library.</span></span> <span data-ttu-id="d96b9-110">例如，針對版本 *x. y*，主要版本號碼為 *x*。</span><span class="sxs-lookup"><span data-stu-id="d96b9-110">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `wMinorVersion`  
 <span data-ttu-id="d96b9-111">在類型程式庫的次要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="d96b9-111">[in] The minor version number of the type library.</span></span> <span data-ttu-id="d96b9-112">例如，針對版本 *x. y*，次要版本號碼是 *y*。</span><span class="sxs-lookup"><span data-stu-id="d96b9-112">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
 `syskind`  
 <span data-ttu-id="d96b9-113">在識別作業環境的 [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) 旗標。</span><span class="sxs-lookup"><span data-stu-id="d96b9-113">[in] A [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) flag that identifies the operating environment.</span></span> <span data-ttu-id="d96b9-114">一般值為 SYS_WIN32 和 SYS_WIN64。</span><span class="sxs-lookup"><span data-stu-id="d96b9-114">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pbstrResolvedTlbName`  
 <span data-ttu-id="d96b9-115">擴展 [BSTR](/previous-versions/windows/desktop/automat/bstr) 的指標，其中包含參數中所命名類型程式庫的完整路徑 `bstrSimpleName` 。</span><span class="sxs-lookup"><span data-stu-id="d96b9-115">[out] A pointer to a [BSTR](/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d96b9-116">備註</span><span class="sxs-lookup"><span data-stu-id="d96b9-116">Remarks</span></span>  

 <span data-ttu-id="d96b9-117">在 `ResolveTypeLib` [Tlbexp.exe (型別程式庫匯出工具) ](../../tools/tlbexp-exe-type-library-exporter.md)處理期間， [LoadTypeLibWithResolver](loadtypelibwithresolver-function.md)函式會呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="d96b9-117">The `ResolveTypeLib` method is called by the [LoadTypeLibWithResolver function](loadtypelibwithresolver-function.md) during [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md) processing.</span></span>  
  
 <span data-ttu-id="d96b9-118">此介面的自訂實作為必須傳回 [BSTR](/previous-versions/windows/desktop/automat/bstr) ，其中包含參數中所命名類型程式庫的完整路徑 `bstrSimpleName` 。</span><span class="sxs-lookup"><span data-stu-id="d96b9-118">Custom implementations of this interface must return a [BSTR](/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d96b9-119">需求</span><span class="sxs-lookup"><span data-stu-id="d96b9-119">Requirements</span></span>  

 <span data-ttu-id="d96b9-120">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d96b9-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d96b9-121">**標頭：** TlbRef .idl、TlbRef。h</span><span class="sxs-lookup"><span data-stu-id="d96b9-121">**Header:** TlbRef.idl, TlbRef.h</span></span>  
  
 <span data-ttu-id="d96b9-122">連結 **庫：** TlbRef .lib</span><span class="sxs-lookup"><span data-stu-id="d96b9-122">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="d96b9-123">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d96b9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d96b9-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d96b9-124">See also</span></span>

- [<span data-ttu-id="d96b9-125">Tlbexp Helper 函式</span><span class="sxs-lookup"><span data-stu-id="d96b9-125">Tlbexp Helper Functions</span></span>](index.md)
- [<span data-ttu-id="d96b9-126">LoadTypeLibEx</span><span class="sxs-lookup"><span data-stu-id="d96b9-126">LoadTypeLibEx</span></span>](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
