---
title: ISymUnmanagedVariable::GetAddressField1 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField1
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField1
helpviewer_keywords:
- GetAddressField1 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField1 method [.NET Framework debugging]
ms.assetid: 25788ed1-0ce3-4b97-96fc-88f8997812a3
topic_type:
- apiref
ms.openlocfilehash: e3ea3c0fd65750d52c0cfb10edbe18b1512f724b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729014"
---
# <a name="isymunmanagedvariablegetaddressfield1-method"></a><span data-ttu-id="6419d-102">ISymUnmanagedVariable::GetAddressField1 方法</span><span class="sxs-lookup"><span data-stu-id="6419d-102">ISymUnmanagedVariable::GetAddressField1 Method</span></span>

<span data-ttu-id="6419d-103">取得這個變數的第一個位址欄位。</span><span class="sxs-lookup"><span data-stu-id="6419d-103">Gets the first address field for this variable.</span></span> <span data-ttu-id="6419d-104">其意義取決於位址的種類。</span><span class="sxs-lookup"><span data-stu-id="6419d-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6419d-105">語法</span><span class="sxs-lookup"><span data-stu-id="6419d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField1(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6419d-106">參數</span><span class="sxs-lookup"><span data-stu-id="6419d-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="6419d-107">擴展 `ULONG32` 接收第一個位址欄位之的指標。</span><span class="sxs-lookup"><span data-stu-id="6419d-107">[out] A pointer to a `ULONG32` that receives the first address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6419d-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="6419d-108">Return Value</span></span>  

 <span data-ttu-id="6419d-109">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="6419d-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6419d-110">需求</span><span class="sxs-lookup"><span data-stu-id="6419d-110">Requirements</span></span>  

 <span data-ttu-id="6419d-111">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="6419d-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6419d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6419d-112">See also</span></span>

- [<span data-ttu-id="6419d-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="6419d-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="6419d-114">GetAddressField2 方法</span><span class="sxs-lookup"><span data-stu-id="6419d-114">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="6419d-115">GetAddressField3 方法</span><span class="sxs-lookup"><span data-stu-id="6419d-115">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="6419d-116">GetAddressKind 方法</span><span class="sxs-lookup"><span data-stu-id="6419d-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)
