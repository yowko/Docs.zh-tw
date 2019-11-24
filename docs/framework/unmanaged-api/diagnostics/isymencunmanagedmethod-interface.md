---
title: ISymENCUnmanagedMethod 介面
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod
helpviewer_keywords:
- ISymENCUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: faebf594-67d5-4abf-b9c1-547fd3a1ff87
topic_type:
- apiref
ms.openlocfilehash: 47477bb473df8b568844d07bea704df681c9b95d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448603"
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="21f74-102">ISymENCUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="21f74-102">ISymENCUnmanagedMethod Interface</span></span>
<span data-ttu-id="21f74-103">Provides information for the Edit and Continue feature.</span><span class="sxs-lookup"><span data-stu-id="21f74-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="21f74-104">方法</span><span class="sxs-lookup"><span data-stu-id="21f74-104">Methods</span></span>  
  
|<span data-ttu-id="21f74-105">方法</span><span class="sxs-lookup"><span data-stu-id="21f74-105">Method</span></span>|<span data-ttu-id="21f74-106">描述</span><span class="sxs-lookup"><span data-stu-id="21f74-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="21f74-107">GetDocumentsForMethod 方法</span><span class="sxs-lookup"><span data-stu-id="21f74-107">GetDocumentsForMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="21f74-108">Gets the documents that this method has lines in.</span><span class="sxs-lookup"><span data-stu-id="21f74-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="21f74-109">GetDocumentsForMethodCount 方法</span><span class="sxs-lookup"><span data-stu-id="21f74-109">GetDocumentsForMethodCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="21f74-110">Gets the number of documents that this method has lines in.</span><span class="sxs-lookup"><span data-stu-id="21f74-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="21f74-111">GetFileNameFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="21f74-111">GetFileNameFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="21f74-112">Gets the file name for the line associated with an offset.</span><span class="sxs-lookup"><span data-stu-id="21f74-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="21f74-113">GetLineFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="21f74-113">GetLineFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="21f74-114">Gets the line information associated with an offset.</span><span class="sxs-lookup"><span data-stu-id="21f74-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="21f74-115">GetSourceExtentInDocument 方法</span><span class="sxs-lookup"><span data-stu-id="21f74-115">GetSourceExtentInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="21f74-116">Gets the smallest start line and largest end line for the method in a specific document.</span><span class="sxs-lookup"><span data-stu-id="21f74-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="21f74-117">需求</span><span class="sxs-lookup"><span data-stu-id="21f74-117">Requirements</span></span>  
 <span data-ttu-id="21f74-118">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="21f74-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21f74-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="21f74-119">See also</span></span>

- [<span data-ttu-id="21f74-120">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="21f74-120">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
