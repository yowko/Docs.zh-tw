---
title: ISymUnmanagedVariable::GetAddressKind 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressKind
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressKind
helpviewer_keywords:
- GetAddressKind method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressKind method [.NET Framework debugging]
ms.assetid: a71563c0-62f2-4eb4-970c-825d61827613
topic_type:
- apiref
ms.openlocfilehash: 6a7824949edc905a3edcd58f60d40f8b1a40c53c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726908"
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="adb6a-102">ISymUnmanagedVariable::GetAddressKind 方法</span><span class="sxs-lookup"><span data-stu-id="adb6a-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>

<span data-ttu-id="adb6a-103">取得這個變數的位址種類。</span><span class="sxs-lookup"><span data-stu-id="adb6a-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adb6a-104">語法</span><span class="sxs-lookup"><span data-stu-id="adb6a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="adb6a-105">參數</span><span class="sxs-lookup"><span data-stu-id="adb6a-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="adb6a-106">擴展接收值之的指標 `ULONG32` 。</span><span class="sxs-lookup"><span data-stu-id="adb6a-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="adb6a-107">可能的值定義于 [CorSymAddrKind](corsymaddrkind-enumeration.md) 列舉中。</span><span class="sxs-lookup"><span data-stu-id="adb6a-107">The possible values are defined in the [CorSymAddrKind](corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="adb6a-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="adb6a-108">Return Value</span></span>  

 <span data-ttu-id="adb6a-109">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="adb6a-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adb6a-110">需求</span><span class="sxs-lookup"><span data-stu-id="adb6a-110">Requirements</span></span>  

 <span data-ttu-id="adb6a-111">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="adb6a-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adb6a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="adb6a-112">See also</span></span>

- [<span data-ttu-id="adb6a-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="adb6a-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
