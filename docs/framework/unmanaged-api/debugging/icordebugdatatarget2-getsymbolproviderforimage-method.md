---
title: ICorDebugDataTarget2::GetSymbolProviderForImage 方法
ms.date: 03/30/2017
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
ms.openlocfilehash: 5a5ccaeb36dcda82c0189026e19c6a7c023f3e1c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713765"
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a><span data-ttu-id="1dcca-102">ICorDebugDataTarget2::GetSymbolProviderForImage 方法</span><span class="sxs-lookup"><span data-stu-id="1dcca-102">ICorDebugDataTarget2::GetSymbolProviderForImage Method</span></span>

<span data-ttu-id="1dcca-103">從模組的基底位址傳回模組的符號提供者。</span><span class="sxs-lookup"><span data-stu-id="1dcca-103">Returns the symbol-provider for a module from the base address of that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dcca-104">語法</span><span class="sxs-lookup"><span data-stu-id="1dcca-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1dcca-105">參數</span><span class="sxs-lookup"><span data-stu-id="1dcca-105">Parameters</span></span>  

 `imageBaseAddress`  
 <span data-ttu-id="1dcca-106">在 [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) 值，表示模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="1dcca-106">[in] A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that represents the base address of a module.</span></span>  
  
 `ppSymProvider`  
 <span data-ttu-id="1dcca-107">擴展 [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) 物件位址的指標。</span><span class="sxs-lookup"><span data-stu-id="1dcca-107">[out] A pointer to the address of an [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1dcca-108">備註</span><span class="sxs-lookup"><span data-stu-id="1dcca-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1dcca-109">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="1dcca-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dcca-110">需求</span><span class="sxs-lookup"><span data-stu-id="1dcca-110">Requirements</span></span>  

 <span data-ttu-id="1dcca-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1dcca-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dcca-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1dcca-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1dcca-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1dcca-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1dcca-114">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dcca-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dcca-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1dcca-115">See also</span></span>

- [<span data-ttu-id="1dcca-116">ICorDebugDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="1dcca-116">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="1dcca-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="1dcca-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
