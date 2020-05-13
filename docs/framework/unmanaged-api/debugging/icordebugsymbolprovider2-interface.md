---
title: ICorDebugSymbolProvider2 介面
ms.date: 03/30/2017
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
ms.openlocfilehash: e6712dca776bf4c20ce7fc8568e94399a81beecb
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379292"
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="430eb-102">ICorDebugSymbolProvider2 介面</span><span class="sxs-lookup"><span data-stu-id="430eb-102">ICorDebugSymbolProvider2 Interface</span></span>
<span data-ttu-id="430eb-103">以邏輯方式擴充[ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md)介面，以取得其他的 debug 符號資訊。</span><span class="sxs-lookup"><span data-stu-id="430eb-103">Logically extends the [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="430eb-104">方法</span><span class="sxs-lookup"><span data-stu-id="430eb-104">Methods</span></span>  
  
|<span data-ttu-id="430eb-105">方法</span><span class="sxs-lookup"><span data-stu-id="430eb-105">Method</span></span>|<span data-ttu-id="430eb-106">描述</span><span class="sxs-lookup"><span data-stu-id="430eb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="430eb-107">GetFrameProps 方法</span><span class="sxs-lookup"><span data-stu-id="430eb-107">GetFrameProps Method</span></span>](icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="430eb-108">傳回某方法啟動相關的虛擬位址，以及被指定程式碼相關的虛擬位址的之父框架。</span><span class="sxs-lookup"><span data-stu-id="430eb-108">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="430eb-109">GetGenericDictionaryInfo 方法</span><span class="sxs-lookup"><span data-stu-id="430eb-109">GetGenericDictionaryInfo Method</span></span>](icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="430eb-110">擷取泛型字典對應。</span><span class="sxs-lookup"><span data-stu-id="430eb-110">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="430eb-111">備註</span><span class="sxs-lookup"><span data-stu-id="430eb-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="430eb-112">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="430eb-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="430eb-113">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="430eb-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="430eb-114">需求</span><span class="sxs-lookup"><span data-stu-id="430eb-114">Requirements</span></span>  
 <span data-ttu-id="430eb-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="430eb-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="430eb-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="430eb-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="430eb-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="430eb-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="430eb-118">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="430eb-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="430eb-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="430eb-119">See also</span></span>

- [<span data-ttu-id="430eb-120">ICorDebugSymbolProvider 介面</span><span class="sxs-lookup"><span data-stu-id="430eb-120">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="430eb-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="430eb-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="430eb-122">偵錯</span><span class="sxs-lookup"><span data-stu-id="430eb-122">Debugging</span></span>](index.md)
