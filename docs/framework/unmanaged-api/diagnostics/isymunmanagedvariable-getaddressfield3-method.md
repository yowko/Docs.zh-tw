---
title: ISymUnmanagedVariable::GetAddressField3 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField3
helpviewer_keywords:
- ISymUnmanagedVariable::GetAddressField3 method [.NET Framework debugging]
- GetAddressField3 method [.NET Framework debugging]
ms.assetid: 4d834721-ad8d-439d-b356-c6b4aef022fc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 76199dd18799c9f51f37d5b92e589effd7f45a57
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778308"
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a><span data-ttu-id="0a8a9-102">ISymUnmanagedVariable::GetAddressField3 方法</span><span class="sxs-lookup"><span data-stu-id="0a8a9-102">ISymUnmanagedVariable::GetAddressField3 Method</span></span>
<span data-ttu-id="0a8a9-103">取得這個變數中的第三個的 [位址] 欄位。</span><span class="sxs-lookup"><span data-stu-id="0a8a9-103">Gets the third address field for this variable.</span></span> <span data-ttu-id="0a8a9-104">其意義取決於位址的類型。</span><span class="sxs-lookup"><span data-stu-id="0a8a9-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a8a9-105">語法</span><span class="sxs-lookup"><span data-stu-id="0a8a9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a8a9-106">參數</span><span class="sxs-lookup"><span data-stu-id="0a8a9-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="0a8a9-107">[out]指標`ULONG32`接收第三個的 [位址] 欄位。</span><span class="sxs-lookup"><span data-stu-id="0a8a9-107">[out] A pointer to a `ULONG32` that receives the third address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a8a9-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="0a8a9-108">Return Value</span></span>  
 <span data-ttu-id="0a8a9-109">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="0a8a9-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a8a9-110">需求</span><span class="sxs-lookup"><span data-stu-id="0a8a9-110">Requirements</span></span>  
 <span data-ttu-id="0a8a9-111">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0a8a9-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a8a9-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a8a9-112">See also</span></span>

- [<span data-ttu-id="0a8a9-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="0a8a9-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="0a8a9-114">GetAddressField1 方法</span><span class="sxs-lookup"><span data-stu-id="0a8a9-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="0a8a9-115">GetAddressField2 方法</span><span class="sxs-lookup"><span data-stu-id="0a8a9-115">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="0a8a9-116">GetAddressKind 方法</span><span class="sxs-lookup"><span data-stu-id="0a8a9-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
