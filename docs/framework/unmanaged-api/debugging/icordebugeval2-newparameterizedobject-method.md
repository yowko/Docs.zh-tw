---
title: ICorDebugEval2::NewParameterizedObject 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObject
helpviewer_keywords:
- NewParameterizedObject method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObject method [.NET Framework debugging]
ms.assetid: 3d705463-e640-4249-8036-4e8206d03cfe
topic_type:
- apiref
ms.openlocfilehash: 5d01ab0b6b5d489b2181056129e22661a50108a3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084849"
---
# <a name="icordebugeval2newparameterizedobject-method"></a><span data-ttu-id="8a493-102">ICorDebugEval2::NewParameterizedObject 方法</span><span class="sxs-lookup"><span data-stu-id="8a493-102">ICorDebugEval2::NewParameterizedObject Method</span></span>
<span data-ttu-id="8a493-103">具現化新的參數化型別物件，並呼叫物件的函式方法。</span><span class="sxs-lookup"><span data-stu-id="8a493-103">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a493-104">語法</span><span class="sxs-lookup"><span data-stu-id="8a493-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedObject (  
    [in] ICorDebugFunction     *pConstructor,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a493-105">參數</span><span class="sxs-lookup"><span data-stu-id="8a493-105">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="8a493-106">在ICorDebugFunction 物件的指標，表示要具現化之物件的構造函式。</span><span class="sxs-lookup"><span data-stu-id="8a493-106">[in] A pointer to an ICorDebugFunction object that represents the constructor of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="8a493-107">在傳遞的型別引數數目。</span><span class="sxs-lookup"><span data-stu-id="8a493-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="8a493-108">在指標的陣列，其中每一個都會指向 ICorDebugType 物件，代表正在具現化之物件的型別引數。</span><span class="sxs-lookup"><span data-stu-id="8a493-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="8a493-109">在傳遞至此函式的引數數目。</span><span class="sxs-lookup"><span data-stu-id="8a493-109">[in] The number of arguments passed to the constructor.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="8a493-110">在指標的陣列，其中每一個都會指向 ICorDebugValue 物件，代表傳遞至此函式的引數值。</span><span class="sxs-lookup"><span data-stu-id="8a493-110">[in] An array of pointers, each of which points to an ICorDebugValue object that represents an argument value that is passed to the constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a493-111">備註</span><span class="sxs-lookup"><span data-stu-id="8a493-111">Remarks</span></span>  
 <span data-ttu-id="8a493-112">物件的函式可能會採用 <xref:System.Type> 參數。</span><span class="sxs-lookup"><span data-stu-id="8a493-112">The object's constructor may take <xref:System.Type> parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a493-113">需求</span><span class="sxs-lookup"><span data-stu-id="8a493-113">Requirements</span></span>  
 <span data-ttu-id="8a493-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8a493-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a493-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a493-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a493-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a493-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a493-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a493-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
