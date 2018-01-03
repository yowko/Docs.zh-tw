---
title: "ISymUnmanagedVariable::GetAddressField1 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetAddressField1
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetAddressField1
helpviewer_keywords:
- GetAddressField1 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField1 method [.NET Framework debugging]
ms.assetid: 25788ed1-0ce3-4b97-96fc-88f8997812a3
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8085deb0cdb0b16eddfa39663277ceecdde10341
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedvariablegetaddressfield1-method"></a><span data-ttu-id="eaab1-102">ISymUnmanagedVariable::GetAddressField1 方法</span><span class="sxs-lookup"><span data-stu-id="eaab1-102">ISymUnmanagedVariable::GetAddressField1 Method</span></span>
<span data-ttu-id="eaab1-103">取得這個變數的第一個地址欄位。</span><span class="sxs-lookup"><span data-stu-id="eaab1-103">Gets the first address field for this variable.</span></span> <span data-ttu-id="eaab1-104">其意義取決於位址類型。</span><span class="sxs-lookup"><span data-stu-id="eaab1-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaab1-105">語法</span><span class="sxs-lookup"><span data-stu-id="eaab1-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField1(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eaab1-106">參數</span><span class="sxs-lookup"><span data-stu-id="eaab1-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="eaab1-107">[out]指標`ULONG32`接收第一個地址欄位。</span><span class="sxs-lookup"><span data-stu-id="eaab1-107">[out] A pointer to a `ULONG32` that receives the first address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eaab1-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="eaab1-108">Return Value</span></span>  
 <span data-ttu-id="eaab1-109">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="eaab1-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eaab1-110">需求</span><span class="sxs-lookup"><span data-stu-id="eaab1-110">Requirements</span></span>  
 <span data-ttu-id="eaab1-111">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="eaab1-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaab1-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="eaab1-112">See Also</span></span>  
 [<span data-ttu-id="eaab1-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="eaab1-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="eaab1-114">GetAddressField2 方法</span><span class="sxs-lookup"><span data-stu-id="eaab1-114">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)  
 [<span data-ttu-id="eaab1-115">GetAddressField3 方法</span><span class="sxs-lookup"><span data-stu-id="eaab1-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)  
 [<span data-ttu-id="eaab1-116">GetAddressKind 方法</span><span class="sxs-lookup"><span data-stu-id="eaab1-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
