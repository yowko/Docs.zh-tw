---
title: ICorDebugProcess5::GetTypeForTypeID 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeForTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeForTypeID
helpviewer_keywords:
- GetTypeForTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeForTypeID method [.NET Framework debugging]
ms.assetid: e0eed5a8-fa6d-4818-bd00-7babcea30325
topic_type:
- apiref
ms.openlocfilehash: 0ed83005bd4ab23124a458a024985d011dfce8c1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717596"
---
# <a name="icordebugprocess5gettypefortypeid-method"></a><span data-ttu-id="93bcd-102">ICorDebugProcess5::GetTypeForTypeID 方法</span><span class="sxs-lookup"><span data-stu-id="93bcd-102">ICorDebugProcess5::GetTypeForTypeID Method</span></span>

<span data-ttu-id="93bcd-103">將類型識別碼轉換成 ICorDebugType 值。</span><span class="sxs-lookup"><span data-stu-id="93bcd-103">Converts a type identifier to an ICorDebugType value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93bcd-104">語法</span><span class="sxs-lookup"><span data-stu-id="93bcd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93bcd-105">參數</span><span class="sxs-lookup"><span data-stu-id="93bcd-105">Parameters</span></span>  

 `id`  
 <span data-ttu-id="93bcd-106">在類型識別碼。</span><span class="sxs-lookup"><span data-stu-id="93bcd-106">[in] The type identifier.</span></span>  
  
 `ppType`  
 <span data-ttu-id="93bcd-107">擴展ICorDebugType 物件位址的指標。</span><span class="sxs-lookup"><span data-stu-id="93bcd-107">[out] A pointer to the address of an ICorDebugType object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93bcd-108">備註</span><span class="sxs-lookup"><span data-stu-id="93bcd-108">Remarks</span></span>  

 <span data-ttu-id="93bcd-109">在某些情況下，傳回型別識別碼的方法可能會傳回 null `COR_TYPEID` 值。</span><span class="sxs-lookup"><span data-stu-id="93bcd-109">In some cases, methods that return a type identifier may return a null `COR_TYPEID` value.</span></span> <span data-ttu-id="93bcd-110">如果將此值做為 `id` 引數傳遞， `GetTypeForTypeID` 方法將會失敗並傳回 `E_FAIL` 。</span><span class="sxs-lookup"><span data-stu-id="93bcd-110">If this value is passed as the `id` argument, the `GetTypeForTypeID` method will fail and return `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93bcd-111">需求</span><span class="sxs-lookup"><span data-stu-id="93bcd-111">Requirements</span></span>  

 <span data-ttu-id="93bcd-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="93bcd-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93bcd-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="93bcd-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93bcd-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93bcd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93bcd-115">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93bcd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93bcd-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93bcd-116">See also</span></span>

- [<span data-ttu-id="93bcd-117">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="93bcd-117">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="93bcd-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="93bcd-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
