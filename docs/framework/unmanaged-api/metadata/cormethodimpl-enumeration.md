---
title: CorMethodImpl 列舉
ms.date: 03/30/2017
api_name:
- CorMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodImpl
helpviewer_keywords:
- CorMethodImpl enumeration [.NET Framework metadata]
ms.assetid: ffbb3caf-20da-4a4b-8983-77376e72b990
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8ef293daea1a768c26adf05d14107a42889226e0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491281"
---
# <a name="cormethodimpl-enumeration"></a><span data-ttu-id="2c49d-102">CorMethodImpl 列舉</span><span class="sxs-lookup"><span data-stu-id="2c49d-102">CorMethodImpl Enumeration</span></span>
<span data-ttu-id="2c49d-103">包含值，這些值描述方法實作功能。</span><span class="sxs-lookup"><span data-stu-id="2c49d-103">Contains values that describe method implementation features.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c49d-104">語法</span><span class="sxs-lookup"><span data-stu-id="2c49d-104">Syntax</span></span>  
  
```  
typedef enum CorMethodImpl {  
  
    miCodeTypeMask      =   0x0003,  
    miIL                =   0x0000,  
    miNative            =   0x0001,  
    miOPTIL             =   0x0002,  
    miRuntime           =   0x0003,  
  
    miManagedMask       =   0x0004,  
    miUnmanaged         =   0x0004,  
    miManaged           =   0x0000,  
  
    miForwardRef        =   0x0010,  
    miPreserveSig       =   0x0080,  
  
    miInternalCall      =   0x1000,  
    miSynchronized      =   0x0020,  
    miNoInlining        =   0x0008,  
    miAggressiveInlining =  0x0100,  
    miNoOptimization     =  0x0040,  
    miMaxMethodImplVal  =   0xffff  
  
} CorMethodImpl;  
```  
  
## <a name="members"></a><span data-ttu-id="2c49d-105">成員</span><span class="sxs-lookup"><span data-stu-id="2c49d-105">Members</span></span>  
  
|<span data-ttu-id="2c49d-106">成員</span><span class="sxs-lookup"><span data-stu-id="2c49d-106">Member</span></span>|<span data-ttu-id="2c49d-107">描述</span><span class="sxs-lookup"><span data-stu-id="2c49d-107">Description</span></span>|  
|------------|-----------------|  
|`miCodeTypeMask`|<span data-ttu-id="2c49d-108">描述程式碼類型的旗標。</span><span class="sxs-lookup"><span data-stu-id="2c49d-108">Flags that describe code type.</span></span>|  
|`miIL`|<span data-ttu-id="2c49d-109">指定方法實作是 Microsoft intermediate language (MSIL)。</span><span class="sxs-lookup"><span data-stu-id="2c49d-109">Specifies that the method implementation is Microsoft intermediate language (MSIL).</span></span>|  
|`miNative`|<span data-ttu-id="2c49d-110">指定方法實作為原生。</span><span class="sxs-lookup"><span data-stu-id="2c49d-110">Specifies that the method implementation is native.</span></span>|  
|`miOPTIL`|<span data-ttu-id="2c49d-111">指定方法實作為 OPTIL。</span><span class="sxs-lookup"><span data-stu-id="2c49d-111">Specifies that the method implementation is OPTIL.</span></span>|  
|`miRuntime`|<span data-ttu-id="2c49d-112">指定方法實作由通用語言執行平台。</span><span class="sxs-lookup"><span data-stu-id="2c49d-112">Specifies that the method implementation is provided by the common language runtime.</span></span>|  
|`miManagedMask`|<span data-ttu-id="2c49d-113">表示程式碼是否為 managed 或 unmanaged 的旗標。</span><span class="sxs-lookup"><span data-stu-id="2c49d-113">Flags that indicate whether the code is managed or unmanaged.</span></span>|  
|`miUnmanaged`|<span data-ttu-id="2c49d-114">指定方法實作為非受控。</span><span class="sxs-lookup"><span data-stu-id="2c49d-114">Specifies that the method implementation is unmanaged.</span></span>|  
|`miManaged`|<span data-ttu-id="2c49d-115">指定方法實作管理。</span><span class="sxs-lookup"><span data-stu-id="2c49d-115">Specifies that the method implementation is managed.</span></span>|  
|`miForwardRef`|<span data-ttu-id="2c49d-116">指定已定義的方法。</span><span class="sxs-lookup"><span data-stu-id="2c49d-116">Specifies that the method is defined.</span></span> <span data-ttu-id="2c49d-117">這個旗標時，可使用主要合併。</span><span class="sxs-lookup"><span data-stu-id="2c49d-117">This flag is used primarily in merge scenarios.</span></span>|  
|`miPreserveSig`|<span data-ttu-id="2c49d-118">指定方法簽章不會受損 HRESULT 轉換。</span><span class="sxs-lookup"><span data-stu-id="2c49d-118">Specifies that the method signature cannot be mangled for an HRESULT conversion.</span></span>|  
|`miInternalCall`|<span data-ttu-id="2c49d-119">保留供內部使用的 common language runtime。</span><span class="sxs-lookup"><span data-stu-id="2c49d-119">Reserved for internal use by the common language runtime.</span></span>|  
|`miSynchronized`|<span data-ttu-id="2c49d-120">指定的方法是單一執行緒，透過其主體。</span><span class="sxs-lookup"><span data-stu-id="2c49d-120">Specifies that the method is single-threaded through its body.</span></span>|  
|`miNoInlining`|<span data-ttu-id="2c49d-121">指定方法無法內嵌。</span><span class="sxs-lookup"><span data-stu-id="2c49d-121">Specifies that the method cannot be inlined.</span></span>|  
|`miAggressiveInlining`|<span data-ttu-id="2c49d-122">指定方法應內嵌的話。</span><span class="sxs-lookup"><span data-stu-id="2c49d-122">Specifies that the method should be inlined if possible.</span></span>|  
|`miNoOptimization`|<span data-ttu-id="2c49d-123">指定未最佳化的方法。</span><span class="sxs-lookup"><span data-stu-id="2c49d-123">Specifies that the method should not be optimized.</span></span>|  
|`miMaxMethodImplVal`|<span data-ttu-id="2c49d-124">最大有效值`CorMethodImpl`。</span><span class="sxs-lookup"><span data-stu-id="2c49d-124">The maximum valid value for a `CorMethodImpl`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2c49d-125">需求</span><span class="sxs-lookup"><span data-stu-id="2c49d-125">Requirements</span></span>  
 <span data-ttu-id="2c49d-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2c49d-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c49d-127">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="2c49d-127">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="2c49d-128">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c49d-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c49d-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c49d-129">See also</span></span>
- [<span data-ttu-id="2c49d-130">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="2c49d-130">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
