---
title: ISymUnmanagedVariable::GetAttributes 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAttributes
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAttributes
helpviewer_keywords:
- GetAttributes method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAttributes method [.NET Framework debugging]
ms.assetid: 80f168af-a6a6-4c8f-b9e6-8a82dc834ed5
topic_type:
- apiref
ms.openlocfilehash: cfc28dfcda7bf4b3d1fc6fe3530a212ee76fadd2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446081"
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="17689-102">ISymUnmanagedVariable::GetAttributes 方法</span><span class="sxs-lookup"><span data-stu-id="17689-102">ISymUnmanagedVariable::GetAttributes Method</span></span>
<span data-ttu-id="17689-103">取得此變數的屬性旗標。</span><span class="sxs-lookup"><span data-stu-id="17689-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17689-104">語法</span><span class="sxs-lookup"><span data-stu-id="17689-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17689-105">參數</span><span class="sxs-lookup"><span data-stu-id="17689-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="17689-106">脫銷接收屬性之 `ULONG32` 的指標。</span><span class="sxs-lookup"><span data-stu-id="17689-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="17689-107">傳回的值將是[CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md)列舉中所定義的其中一個值。</span><span class="sxs-lookup"><span data-stu-id="17689-107">The returned value will be one of the values defined in the [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17689-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="17689-108">Return Value</span></span>  
 <span data-ttu-id="17689-109">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="17689-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17689-110">需求</span><span class="sxs-lookup"><span data-stu-id="17689-110">Requirements</span></span>  
 <span data-ttu-id="17689-111">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="17689-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17689-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17689-112">See also</span></span>

- [<span data-ttu-id="17689-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="17689-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
