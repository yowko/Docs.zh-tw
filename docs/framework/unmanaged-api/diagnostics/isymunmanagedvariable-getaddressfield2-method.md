---
title: "ISymUnmanagedVariable::GetAddressField2 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetAddressField2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetAddressField2
helpviewer_keywords:
- GetAddressField2 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField2 method [.NET Framework debugging]
ms.assetid: 1f25b294-72b6-4882-a49b-6c9d364b6008
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ecde3a59c3a393057f3502c8ae59d789350b913f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedvariablegetaddressfield2-method"></a><span data-ttu-id="90af9-102">ISymUnmanagedVariable::GetAddressField2 方法</span><span class="sxs-lookup"><span data-stu-id="90af9-102">ISymUnmanagedVariable::GetAddressField2 Method</span></span>
<span data-ttu-id="90af9-103">取得這個變數的第二個地址欄位。</span><span class="sxs-lookup"><span data-stu-id="90af9-103">Gets the second address field for this variable.</span></span> <span data-ttu-id="90af9-104">其意義取決於位址類型。</span><span class="sxs-lookup"><span data-stu-id="90af9-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90af9-105">語法</span><span class="sxs-lookup"><span data-stu-id="90af9-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField2(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="90af9-106">參數</span><span class="sxs-lookup"><span data-stu-id="90af9-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="90af9-107">[out]指標`ULONG32`接收第二個地址欄位。</span><span class="sxs-lookup"><span data-stu-id="90af9-107">[out] A pointer to a `ULONG32` that receives the second address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90af9-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="90af9-108">Return Value</span></span>  
 <span data-ttu-id="90af9-109">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="90af9-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90af9-110">需求</span><span class="sxs-lookup"><span data-stu-id="90af9-110">Requirements</span></span>  
 <span data-ttu-id="90af9-111">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="90af9-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90af9-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="90af9-112">See Also</span></span>  
 [<span data-ttu-id="90af9-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="90af9-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="90af9-114">GetAddressField1 方法</span><span class="sxs-lookup"><span data-stu-id="90af9-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)  
 [<span data-ttu-id="90af9-115">GetAddressField3 方法</span><span class="sxs-lookup"><span data-stu-id="90af9-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)  
 [<span data-ttu-id="90af9-116">GetAddressKind 方法</span><span class="sxs-lookup"><span data-stu-id="90af9-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
