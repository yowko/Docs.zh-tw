---
title: PreCloseAssembly 方法
ms.date: 03/30/2017
api_name:
- IALink.PreCloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- PreCloseAssembly
helpviewer_keywords:
- PreCloseAssembly method
ms.assetid: 6d23ac54-15ea-4027-a172-9ebef43e8f56
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a820d5d742c722b495a5a4b3952450a0434110fd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741557"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="72dbc-102">PreCloseAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="72dbc-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="72dbc-103">關閉組件檔案。</span><span class="sxs-lookup"><span data-stu-id="72dbc-103">Closes the assembly file.</span></span> <span data-ttu-id="72dbc-104">關閉所有其他檔案之後, 但在關閉的組件檔案之前，請呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="72dbc-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="72dbc-105">請勿呼叫這個方法的未繫結的模組。</span><span class="sxs-lookup"><span data-stu-id="72dbc-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72dbc-106">語法</span><span class="sxs-lookup"><span data-stu-id="72dbc-106">Syntax</span></span>  
  
```cpp  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="72dbc-107">參數</span><span class="sxs-lookup"><span data-stu-id="72dbc-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="72dbc-108">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="72dbc-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72dbc-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="72dbc-109">Return Value</span></span>  
 <span data-ttu-id="72dbc-110">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="72dbc-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72dbc-111">需求</span><span class="sxs-lookup"><span data-stu-id="72dbc-111">Requirements</span></span>  
 <span data-ttu-id="72dbc-112">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="72dbc-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72dbc-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72dbc-113">See also</span></span>

- [<span data-ttu-id="72dbc-114">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="72dbc-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="72dbc-115">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="72dbc-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="72dbc-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="72dbc-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
