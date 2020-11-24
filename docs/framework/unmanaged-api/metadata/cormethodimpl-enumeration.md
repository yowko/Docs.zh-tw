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
ms.openlocfilehash: 40e82997e58292a10f5e960cc9d9785d9ea8946a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676968"
---
# <a name="cormethodimpl-enumeration"></a><span data-ttu-id="0b97b-102">CorMethodImpl 列舉</span><span class="sxs-lookup"><span data-stu-id="0b97b-102">CorMethodImpl Enumeration</span></span>

<span data-ttu-id="0b97b-103">包含值，這些值描述方法實作功能。</span><span class="sxs-lookup"><span data-stu-id="0b97b-103">Contains values that describe method implementation features.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b97b-104">語法</span><span class="sxs-lookup"><span data-stu-id="0b97b-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="0b97b-105">成員</span><span class="sxs-lookup"><span data-stu-id="0b97b-105">Members</span></span>  
  
|<span data-ttu-id="0b97b-106">member</span><span class="sxs-lookup"><span data-stu-id="0b97b-106">Member</span></span>|<span data-ttu-id="0b97b-107">描述</span><span class="sxs-lookup"><span data-stu-id="0b97b-107">Description</span></span>|  
|------------|-----------------|  
|`miCodeTypeMask`|<span data-ttu-id="0b97b-108">描述程式碼類型的旗標。</span><span class="sxs-lookup"><span data-stu-id="0b97b-108">Flags that describe code type.</span></span>|  
|`miIL`|<span data-ttu-id="0b97b-109">指定方法執行是 Microsoft 中繼語言 (MSIL) 。</span><span class="sxs-lookup"><span data-stu-id="0b97b-109">Specifies that the method implementation is Microsoft intermediate language (MSIL).</span></span>|  
|`miNative`|<span data-ttu-id="0b97b-110">指定方法實作為原生。</span><span class="sxs-lookup"><span data-stu-id="0b97b-110">Specifies that the method implementation is native.</span></span>|  
|`miOPTIL`|<span data-ttu-id="0b97b-111">指定方法實 OPTIL。</span><span class="sxs-lookup"><span data-stu-id="0b97b-111">Specifies that the method implementation is OPTIL.</span></span>|  
|`miRuntime`|<span data-ttu-id="0b97b-112">指定方法實作為 common language runtime 所提供。</span><span class="sxs-lookup"><span data-stu-id="0b97b-112">Specifies that the method implementation is provided by the common language runtime.</span></span>|  
|`miManagedMask`|<span data-ttu-id="0b97b-113">旗標，指出程式碼是否為 managed 或非受控。</span><span class="sxs-lookup"><span data-stu-id="0b97b-113">Flags that indicate whether the code is managed or unmanaged.</span></span>|  
|`miUnmanaged`|<span data-ttu-id="0b97b-114">指定方法執行未受管理。</span><span class="sxs-lookup"><span data-stu-id="0b97b-114">Specifies that the method implementation is unmanaged.</span></span>|  
|`miManaged`|<span data-ttu-id="0b97b-115">指定方法執行為 managed。</span><span class="sxs-lookup"><span data-stu-id="0b97b-115">Specifies that the method implementation is managed.</span></span>|  
|`miForwardRef`|<span data-ttu-id="0b97b-116">指定定義方法。</span><span class="sxs-lookup"><span data-stu-id="0b97b-116">Specifies that the method is defined.</span></span> <span data-ttu-id="0b97b-117">此旗標主要用於合併案例中。</span><span class="sxs-lookup"><span data-stu-id="0b97b-117">This flag is used primarily in merge scenarios.</span></span>|  
|`miPreserveSig`|<span data-ttu-id="0b97b-118">指定方法簽章不能因 HRESULT 轉換而改變。</span><span class="sxs-lookup"><span data-stu-id="0b97b-118">Specifies that the method signature cannot be mangled for an HRESULT conversion.</span></span>|  
|`miInternalCall`|<span data-ttu-id="0b97b-119">保留給 common language runtime 內部使用。</span><span class="sxs-lookup"><span data-stu-id="0b97b-119">Reserved for internal use by the common language runtime.</span></span>|  
|`miSynchronized`|<span data-ttu-id="0b97b-120">指定方法透過其主體為單一執行緒。</span><span class="sxs-lookup"><span data-stu-id="0b97b-120">Specifies that the method is single-threaded through its body.</span></span>|  
|`miNoInlining`|<span data-ttu-id="0b97b-121">指定方法無法內嵌。</span><span class="sxs-lookup"><span data-stu-id="0b97b-121">Specifies that the method cannot be inlined.</span></span>|  
|`miAggressiveInlining`|<span data-ttu-id="0b97b-122">指定應該盡可能內嵌方法。</span><span class="sxs-lookup"><span data-stu-id="0b97b-122">Specifies that the method should be inlined if possible.</span></span>|  
|`miNoOptimization`|<span data-ttu-id="0b97b-123">指定不應優化方法。</span><span class="sxs-lookup"><span data-stu-id="0b97b-123">Specifies that the method should not be optimized.</span></span>|  
|`miMaxMethodImplVal`|<span data-ttu-id="0b97b-124">的最大有效值 `CorMethodImpl` 。</span><span class="sxs-lookup"><span data-stu-id="0b97b-124">The maximum valid value for a `CorMethodImpl`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0b97b-125">需求</span><span class="sxs-lookup"><span data-stu-id="0b97b-125">Requirements</span></span>  

 <span data-ttu-id="0b97b-126">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0b97b-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b97b-127">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="0b97b-127">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="0b97b-128">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b97b-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b97b-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b97b-129">See also</span></span>

- [<span data-ttu-id="0b97b-130">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="0b97b-130">Metadata Enumerations</span></span>](metadata-enumerations.md)
