---
title: "ISymUnmanagedVariable 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable
helpviewer_keywords:
- ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: 704c69ba-77bc-40d7-8c0c-400061686321
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e5ae8d1d05274363dc523c1a2cebf4ed09c1f461
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedvariable-interface"></a><span data-ttu-id="1a6de-102">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="1a6de-102">ISymUnmanagedVariable Interface</span></span>
<span data-ttu-id="1a6de-103">表示變數，例如參數、 區域變數或欄位。</span><span class="sxs-lookup"><span data-stu-id="1a6de-103">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1a6de-104">方法</span><span class="sxs-lookup"><span data-stu-id="1a6de-104">Methods</span></span>  
  
|<span data-ttu-id="1a6de-105">方法</span><span class="sxs-lookup"><span data-stu-id="1a6de-105">Method</span></span>|<span data-ttu-id="1a6de-106">描述</span><span class="sxs-lookup"><span data-stu-id="1a6de-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1a6de-107">GetAddressField1 方法</span><span class="sxs-lookup"><span data-stu-id="1a6de-107">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)|<span data-ttu-id="1a6de-108">取得這個變數的第一個地址欄位。</span><span class="sxs-lookup"><span data-stu-id="1a6de-108">Gets the first address field for this variable.</span></span> <span data-ttu-id="1a6de-109">其意義取決於位址類型。</span><span class="sxs-lookup"><span data-stu-id="1a6de-109">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="1a6de-110">GetAddressField2 方法</span><span class="sxs-lookup"><span data-stu-id="1a6de-110">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)|<span data-ttu-id="1a6de-111">取得這個變數的第二個地址欄位。</span><span class="sxs-lookup"><span data-stu-id="1a6de-111">Gets the second address field for this variable.</span></span> <span data-ttu-id="1a6de-112">其意義取決於位址類型。</span><span class="sxs-lookup"><span data-stu-id="1a6de-112">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="1a6de-113">GetAddressField3 方法</span><span class="sxs-lookup"><span data-stu-id="1a6de-113">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)|<span data-ttu-id="1a6de-114">取得這個變數的第三個地址欄位。</span><span class="sxs-lookup"><span data-stu-id="1a6de-114">Gets the third address field for this variable.</span></span> <span data-ttu-id="1a6de-115">其意義取決於位址類型。</span><span class="sxs-lookup"><span data-stu-id="1a6de-115">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="1a6de-116">GetAddressKind 方法</span><span class="sxs-lookup"><span data-stu-id="1a6de-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)|<span data-ttu-id="1a6de-117">取得這個變數的位址類型。</span><span class="sxs-lookup"><span data-stu-id="1a6de-117">Gets the kind of address of this variable.</span></span>|  
|[<span data-ttu-id="1a6de-118">GetAttributes 方法</span><span class="sxs-lookup"><span data-stu-id="1a6de-118">GetAttributes Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getattributes-method.md)|<span data-ttu-id="1a6de-119">取得這個變數的屬性旗標。</span><span class="sxs-lookup"><span data-stu-id="1a6de-119">Gets the attribute flags for this variable.</span></span>|  
|[<span data-ttu-id="1a6de-120">GetEndOffset 方法</span><span class="sxs-lookup"><span data-stu-id="1a6de-120">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)|<span data-ttu-id="1a6de-121">取得其父系內這個變數的結束位移。</span><span class="sxs-lookup"><span data-stu-id="1a6de-121">Gets the end offset of this variable within its parent.</span></span>|  
|[<span data-ttu-id="1a6de-122">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="1a6de-122">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getname-method.md)|<span data-ttu-id="1a6de-123">取得這個變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="1a6de-123">Gets the name of this variable.</span></span>|  
|[<span data-ttu-id="1a6de-124">GetSignature 方法</span><span class="sxs-lookup"><span data-stu-id="1a6de-124">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getsignature-method.md)|<span data-ttu-id="1a6de-125">取得這個變數的簽章。</span><span class="sxs-lookup"><span data-stu-id="1a6de-125">Gets the signature of this variable.</span></span>|  
|[<span data-ttu-id="1a6de-126">GetStartOffset 方法</span><span class="sxs-lookup"><span data-stu-id="1a6de-126">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)|<span data-ttu-id="1a6de-127">取得其父系內這個變數的起始位移。</span><span class="sxs-lookup"><span data-stu-id="1a6de-127">Gets the start offset of this variable within its parent.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1a6de-128">需求</span><span class="sxs-lookup"><span data-stu-id="1a6de-128">Requirements</span></span>  
 <span data-ttu-id="1a6de-129">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1a6de-129">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a6de-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="1a6de-130">See Also</span></span>  
 [<span data-ttu-id="1a6de-131">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="1a6de-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
