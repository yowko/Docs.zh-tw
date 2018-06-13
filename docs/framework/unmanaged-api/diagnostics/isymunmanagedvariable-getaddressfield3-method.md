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
ms.openlocfilehash: dd474c7f149b8eff542b674c2ba6527b6a0cbcb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426994"
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a><span data-ttu-id="55a85-102">ISymUnmanagedVariable::GetAddressField3 方法</span><span class="sxs-lookup"><span data-stu-id="55a85-102">ISymUnmanagedVariable::GetAddressField3 Method</span></span>
<span data-ttu-id="55a85-103">取得這個變數的第三個地址欄位。</span><span class="sxs-lookup"><span data-stu-id="55a85-103">Gets the third address field for this variable.</span></span> <span data-ttu-id="55a85-104">其意義取決於位址類型。</span><span class="sxs-lookup"><span data-stu-id="55a85-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55a85-105">語法</span><span class="sxs-lookup"><span data-stu-id="55a85-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="55a85-106">參數</span><span class="sxs-lookup"><span data-stu-id="55a85-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="55a85-107">[out]指標`ULONG32`接收第三個地址欄位。</span><span class="sxs-lookup"><span data-stu-id="55a85-107">[out] A pointer to a `ULONG32` that receives the third address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="55a85-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="55a85-108">Return Value</span></span>  
 <span data-ttu-id="55a85-109">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="55a85-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55a85-110">需求</span><span class="sxs-lookup"><span data-stu-id="55a85-110">Requirements</span></span>  
 <span data-ttu-id="55a85-111">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="55a85-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55a85-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55a85-112">See Also</span></span>  
 [<span data-ttu-id="55a85-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="55a85-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="55a85-114">GetAddressField1 方法</span><span class="sxs-lookup"><span data-stu-id="55a85-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)  
 [<span data-ttu-id="55a85-115">GetAddressField2 方法</span><span class="sxs-lookup"><span data-stu-id="55a85-115">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)  
 [<span data-ttu-id="55a85-116">GetAddressKind 方法</span><span class="sxs-lookup"><span data-stu-id="55a85-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
