---
title: ICorDebugSymbolProvider2::GetFrameProps 方法
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
ms.openlocfilehash: ba1fd104c35b6e6dfdfd771f71eb19f8d532a1d6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672007"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="6fd6b-102">ICorDebugSymbolProvider2::GetFrameProps 方法</span><span class="sxs-lookup"><span data-stu-id="6fd6b-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>

<span data-ttu-id="6fd6b-103">傳回某方法啟動相關的虛擬位址，以及被指定程式碼相關的虛擬位址的之父框架。</span><span class="sxs-lookup"><span data-stu-id="6fd6b-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fd6b-104">語法</span><span class="sxs-lookup"><span data-stu-id="6fd6b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6fd6b-105">參數</span><span class="sxs-lookup"><span data-stu-id="6fd6b-105">Parameters</span></span>  

 `codeRva`  
 <span data-ttu-id="6fd6b-106">[in] 與程式碼相關的虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="6fd6b-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="6fd6b-107">[out] 指向該方法的啟動相關虛擬位址之指標。</span><span class="sxs-lookup"><span data-stu-id="6fd6b-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="6fd6b-108">[out] 指向該框架的啟動相關虛擬位址之指標。</span><span class="sxs-lookup"><span data-stu-id="6fd6b-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6fd6b-109">備註</span><span class="sxs-lookup"><span data-stu-id="6fd6b-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6fd6b-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="6fd6b-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fd6b-111">需求</span><span class="sxs-lookup"><span data-stu-id="6fd6b-111">Requirements</span></span>  

 <span data-ttu-id="6fd6b-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6fd6b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fd6b-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6fd6b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6fd6b-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6fd6b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fd6b-115">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fd6b-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fd6b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6fd6b-116">See also</span></span>

- [<span data-ttu-id="6fd6b-117">ICorDebugSymbolProvider2 介面</span><span class="sxs-lookup"><span data-stu-id="6fd6b-117">ICorDebugSymbolProvider2 Interface</span></span>](icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="6fd6b-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6fd6b-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
