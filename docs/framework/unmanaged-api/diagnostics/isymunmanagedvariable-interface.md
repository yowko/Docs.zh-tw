---
title: ISymUnmanagedVariable 介面
ms.date: 03/30/2017
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
ms.openlocfilehash: d05d4451e8fb75829b22e0a1b9c9afcb0607eb8b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610167"
---
# <a name="isymunmanagedvariable-interface"></a><span data-ttu-id="8d37c-102">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="8d37c-102">ISymUnmanagedVariable Interface</span></span>
<span data-ttu-id="8d37c-103">表示變數，例如參數、本機變數或欄位。</span><span class="sxs-lookup"><span data-stu-id="8d37c-103">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8d37c-104">方法</span><span class="sxs-lookup"><span data-stu-id="8d37c-104">Methods</span></span>  
  
|<span data-ttu-id="8d37c-105">方法</span><span class="sxs-lookup"><span data-stu-id="8d37c-105">Method</span></span>|<span data-ttu-id="8d37c-106">描述</span><span class="sxs-lookup"><span data-stu-id="8d37c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8d37c-107">GetAddressField1 方法</span><span class="sxs-lookup"><span data-stu-id="8d37c-107">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)|<span data-ttu-id="8d37c-108">取得這個變數的第一個位址欄位。</span><span class="sxs-lookup"><span data-stu-id="8d37c-108">Gets the first address field for this variable.</span></span> <span data-ttu-id="8d37c-109">其意義取決於位址的種類。</span><span class="sxs-lookup"><span data-stu-id="8d37c-109">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="8d37c-110">GetAddressField2 方法</span><span class="sxs-lookup"><span data-stu-id="8d37c-110">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)|<span data-ttu-id="8d37c-111">取得這個變數的第二個位址欄位。</span><span class="sxs-lookup"><span data-stu-id="8d37c-111">Gets the second address field for this variable.</span></span> <span data-ttu-id="8d37c-112">其意義取決於位址的種類。</span><span class="sxs-lookup"><span data-stu-id="8d37c-112">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="8d37c-113">GetAddressField3 方法</span><span class="sxs-lookup"><span data-stu-id="8d37c-113">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)|<span data-ttu-id="8d37c-114">取得這個變數的第三個位址欄位。</span><span class="sxs-lookup"><span data-stu-id="8d37c-114">Gets the third address field for this variable.</span></span> <span data-ttu-id="8d37c-115">其意義取決於位址的種類。</span><span class="sxs-lookup"><span data-stu-id="8d37c-115">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="8d37c-116">GetAddressKind 方法</span><span class="sxs-lookup"><span data-stu-id="8d37c-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)|<span data-ttu-id="8d37c-117">取得此變數的網址類別型。</span><span class="sxs-lookup"><span data-stu-id="8d37c-117">Gets the kind of address of this variable.</span></span>|  
|[<span data-ttu-id="8d37c-118">GetAttributes 方法</span><span class="sxs-lookup"><span data-stu-id="8d37c-118">GetAttributes Method</span></span>](isymunmanagedvariable-getattributes-method.md)|<span data-ttu-id="8d37c-119">取得此變數的屬性旗標。</span><span class="sxs-lookup"><span data-stu-id="8d37c-119">Gets the attribute flags for this variable.</span></span>|  
|[<span data-ttu-id="8d37c-120">GetEndOffset 方法</span><span class="sxs-lookup"><span data-stu-id="8d37c-120">GetEndOffset Method</span></span>](isymunmanagedvariable-getendoffset-method.md)|<span data-ttu-id="8d37c-121">取得這個變數在其父系內的結束位移。</span><span class="sxs-lookup"><span data-stu-id="8d37c-121">Gets the end offset of this variable within its parent.</span></span>|  
|[<span data-ttu-id="8d37c-122">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="8d37c-122">GetName Method</span></span>](isymunmanagedvariable-getname-method.md)|<span data-ttu-id="8d37c-123">取得這個變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="8d37c-123">Gets the name of this variable.</span></span>|  
|[<span data-ttu-id="8d37c-124">GetSignature 方法</span><span class="sxs-lookup"><span data-stu-id="8d37c-124">GetSignature Method</span></span>](isymunmanagedvariable-getsignature-method.md)|<span data-ttu-id="8d37c-125">取得此變數的簽章。</span><span class="sxs-lookup"><span data-stu-id="8d37c-125">Gets the signature of this variable.</span></span>|  
|[<span data-ttu-id="8d37c-126">GetStartOffset 方法</span><span class="sxs-lookup"><span data-stu-id="8d37c-126">GetStartOffset Method</span></span>](isymunmanagedvariable-getstartoffset-method.md)|<span data-ttu-id="8d37c-127">取得這個變數在其父系內的起始位移。</span><span class="sxs-lookup"><span data-stu-id="8d37c-127">Gets the start offset of this variable within its parent.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8d37c-128">需求</span><span class="sxs-lookup"><span data-stu-id="8d37c-128">Requirements</span></span>  
 <span data-ttu-id="8d37c-129">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="8d37c-129">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d37c-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d37c-130">See also</span></span>

- [<span data-ttu-id="8d37c-131">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="8d37c-131">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
