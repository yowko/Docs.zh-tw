---
title: ICorDebugILCode2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugILCode2
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: f9dc2afd-df8a-464d-bdbf-5af0a1d4bf85
topic_type:
- apiref
ms.openlocfilehash: 65995e8386b3bc686178b79d4fbb21a7c71bed3e
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210328"
---
# <a name="icordebugilcode2-interface"></a><span data-ttu-id="a2b89-102">ICorDebugILCode2 介面</span><span class="sxs-lookup"><span data-stu-id="a2b89-102">ICorDebugILCode2 Interface</span></span>
<span data-ttu-id="a2b89-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="a2b89-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="a2b89-104">以邏輯方式擴充[ICorDebugILCode](icordebugilcode-interface.md)介面，以提供方法來傳回函式的區域變數簽章的 token，並將分析工具的檢測中繼語言（IL）位移對應至原始方法 IL 位移。</span><span class="sxs-lookup"><span data-stu-id="a2b89-104">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a2b89-105">方法</span><span class="sxs-lookup"><span data-stu-id="a2b89-105">Methods</span></span>  
  
|<span data-ttu-id="a2b89-106">方法</span><span class="sxs-lookup"><span data-stu-id="a2b89-106">Method</span></span>|<span data-ttu-id="a2b89-107">描述</span><span class="sxs-lookup"><span data-stu-id="a2b89-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a2b89-108">GetInstrumentedILMap 方法</span><span class="sxs-lookup"><span data-stu-id="a2b89-108">GetInstrumentedILMap Method</span></span>](icordebugilcode2-getinstrumentedilmap-method.md)|<span data-ttu-id="a2b89-109">將分析工具中的已檢測 IL 位移對應傳回至此執行個體的原始方法 IL 位移。</span><span class="sxs-lookup"><span data-stu-id="a2b89-109">Returns a map from profiler instrumented IL offsets to original method IL offsets for this instance.</span></span>|  
|[<span data-ttu-id="a2b89-110">GetLocalVarSigToken 方法</span><span class="sxs-lookup"><span data-stu-id="a2b89-110">GetLocalVarSigToken Method</span></span>](icordebugilcode2-getlocalvarsigtoken-method.md)|<span data-ttu-id="a2b89-111">針對此執行個體表示的函式，取得區域變數簽章的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a2b89-111">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a2b89-112">需求</span><span class="sxs-lookup"><span data-stu-id="a2b89-112">Requirements</span></span>  
 <span data-ttu-id="a2b89-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a2b89-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2b89-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2b89-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2b89-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2b89-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2b89-116">**.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2b89-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2b89-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="a2b89-117">See also</span></span>

- [<span data-ttu-id="a2b89-118">ICorDebugILCode 介面</span><span class="sxs-lookup"><span data-stu-id="a2b89-118">ICorDebugILCode Interface</span></span>](icordebugilcode-interface.md)
- [<span data-ttu-id="a2b89-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a2b89-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a2b89-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="a2b89-120">Debugging</span></span>](index.md)
