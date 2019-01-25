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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d418a1088f9ee23a088ab4c8246810d2c9bee4fa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574335"
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="c9730-102">ISymUnmanagedVariable::GetAttributes 方法</span><span class="sxs-lookup"><span data-stu-id="c9730-102">ISymUnmanagedVariable::GetAttributes Method</span></span>
<span data-ttu-id="c9730-103">取得此變數的屬性旗標。</span><span class="sxs-lookup"><span data-stu-id="c9730-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9730-104">語法</span><span class="sxs-lookup"><span data-stu-id="c9730-104">Syntax</span></span>  
  
```  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9730-105">參數</span><span class="sxs-lookup"><span data-stu-id="c9730-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="c9730-106">[out]指標`ULONG32`接收屬性。</span><span class="sxs-lookup"><span data-stu-id="c9730-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="c9730-107">傳回的值會是其中一個值中定義[CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="c9730-107">The returned value will be one of the values defined in the [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9730-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="c9730-108">Return Value</span></span>  
 <span data-ttu-id="c9730-109">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="c9730-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9730-110">需求</span><span class="sxs-lookup"><span data-stu-id="c9730-110">Requirements</span></span>  
 <span data-ttu-id="c9730-111">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c9730-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9730-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9730-112">See also</span></span>
- [<span data-ttu-id="c9730-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="c9730-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
