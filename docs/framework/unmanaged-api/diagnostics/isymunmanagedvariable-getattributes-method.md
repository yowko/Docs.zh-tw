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
ms.openlocfilehash: 1142dbb83693f6104ba6e22e174ce02fb92997a6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726895"
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="d89e8-102">ISymUnmanagedVariable::GetAttributes 方法</span><span class="sxs-lookup"><span data-stu-id="d89e8-102">ISymUnmanagedVariable::GetAttributes Method</span></span>

<span data-ttu-id="d89e8-103">取得這個變數的屬性旗標。</span><span class="sxs-lookup"><span data-stu-id="d89e8-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d89e8-104">語法</span><span class="sxs-lookup"><span data-stu-id="d89e8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d89e8-105">參數</span><span class="sxs-lookup"><span data-stu-id="d89e8-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="d89e8-106">擴展接收屬性之的指標 `ULONG32` 。</span><span class="sxs-lookup"><span data-stu-id="d89e8-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="d89e8-107">傳回的值將會是 [CorSymVarFlag](corsymvarflag-enumeration.md) 列舉中所定義的其中一個值。</span><span class="sxs-lookup"><span data-stu-id="d89e8-107">The returned value will be one of the values defined in the [CorSymVarFlag](corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d89e8-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="d89e8-108">Return Value</span></span>  

 <span data-ttu-id="d89e8-109">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="d89e8-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d89e8-110">需求</span><span class="sxs-lookup"><span data-stu-id="d89e8-110">Requirements</span></span>  

 <span data-ttu-id="d89e8-111">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="d89e8-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d89e8-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d89e8-112">See also</span></span>

- [<span data-ttu-id="d89e8-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="d89e8-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
