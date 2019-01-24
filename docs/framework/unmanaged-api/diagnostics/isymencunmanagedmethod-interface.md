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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f46aeed0a303278fd67265e471bfa13b43cede12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680177"
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="98379-102">ISymENCUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="98379-102">ISymENCUnmanagedMethod Interface</span></span>
<span data-ttu-id="98379-103">提供 [編輯後繼續] 功能的資訊。</span><span class="sxs-lookup"><span data-stu-id="98379-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="98379-104">方法</span><span class="sxs-lookup"><span data-stu-id="98379-104">Methods</span></span>  
  
|<span data-ttu-id="98379-105">方法</span><span class="sxs-lookup"><span data-stu-id="98379-105">Method</span></span>|<span data-ttu-id="98379-106">描述</span><span class="sxs-lookup"><span data-stu-id="98379-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="98379-107">GetDocumentsForMethod 方法</span><span class="sxs-lookup"><span data-stu-id="98379-107">GetDocumentsForMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="98379-108">取得這個方法有幾行中的文件。</span><span class="sxs-lookup"><span data-stu-id="98379-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="98379-109">GetDocumentsForMethodCount 方法</span><span class="sxs-lookup"><span data-stu-id="98379-109">GetDocumentsForMethodCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="98379-110">取得這個方法有幾行中的文件數目。</span><span class="sxs-lookup"><span data-stu-id="98379-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="98379-111">GetFileNameFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="98379-111">GetFileNameFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="98379-112">取得行位移與相關聯的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="98379-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="98379-113">GetLineFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="98379-113">GetLineFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="98379-114">取得位移與相關聯的行資訊。</span><span class="sxs-lookup"><span data-stu-id="98379-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="98379-115">GetSourceExtentInDocument 方法</span><span class="sxs-lookup"><span data-stu-id="98379-115">GetSourceExtentInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="98379-116">取得最小起始行和最大的結尾行方法特定的文件中。</span><span class="sxs-lookup"><span data-stu-id="98379-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="98379-117">需求</span><span class="sxs-lookup"><span data-stu-id="98379-117">Requirements</span></span>  
 <span data-ttu-id="98379-118">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="98379-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98379-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98379-119">See also</span></span>
- [<span data-ttu-id="98379-120">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="98379-120">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
