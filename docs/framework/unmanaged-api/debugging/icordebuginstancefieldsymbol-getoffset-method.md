---
title: ICorDebugInstanceFieldSymbol::GetOffset 方法
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
ms.openlocfilehash: 2d73de46bbb1023f20dd9023076630611c74be5d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724919"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="cc534-102">ICorDebugInstanceFieldSymbol::GetOffset 方法</span><span class="sxs-lookup"><span data-stu-id="cc534-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>

<span data-ttu-id="cc534-103">取得在父類別中此執行個體欄位之位元組的位移。</span><span class="sxs-lookup"><span data-stu-id="cc534-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc534-104">語法</span><span class="sxs-lookup"><span data-stu-id="cc534-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc534-105">參數</span><span class="sxs-lookup"><span data-stu-id="cc534-105">Parameters</span></span>  

 `pcbOffset`  
 <span data-ttu-id="cc534-106">此執行個體欄位在其父類別中的位移位元組數目。</span><span class="sxs-lookup"><span data-stu-id="cc534-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc534-107">備註</span><span class="sxs-lookup"><span data-stu-id="cc534-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cc534-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="cc534-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc534-109">需求</span><span class="sxs-lookup"><span data-stu-id="cc534-109">Requirements</span></span>  

 <span data-ttu-id="cc534-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cc534-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc534-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc534-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc534-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc534-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc534-113">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc534-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc534-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc534-114">See also</span></span>

- [<span data-ttu-id="cc534-115">ICorDebugInstanceFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="cc534-115">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="cc534-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="cc534-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
