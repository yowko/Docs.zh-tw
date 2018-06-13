---
title: EnumImportTypes 方法
ms.date: 03/30/2017
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumImportTypes
helpviewer_keywords:
- EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90319886dfe149a3d2d76451c1a8526299cf5b89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401644"
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="2ff54-102">EnumImportTypes 方法</span><span class="sxs-lookup"><span data-stu-id="2ff54-102">EnumImportTypes Method</span></span>
<span data-ttu-id="2ff54-103">列舉每個範圍中的每個型別。</span><span class="sxs-lookup"><span data-stu-id="2ff54-103">Enumerates each type in each scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ff54-104">語法</span><span class="sxs-lookup"><span data-stu-id="2ff54-104">Syntax</span></span>  
  
```  
HRESULT EnumImportTypes(  
    HALINKENUM   hEnum,  
    DWORD        dwMax,  
    mdTypeDef    aTypeDefs[],  
    DWORD*       pdwCount  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ff54-105">參數</span><span class="sxs-lookup"><span data-stu-id="2ff54-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="2ff54-106">列舉值的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="2ff54-106">Handle for enumerator.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="2ff54-107">擷取類型的最大數目。</span><span class="sxs-lookup"><span data-stu-id="2ff54-107">Maximum number of types to retrieve.</span></span>  
  
 `aTypeDefs`  
 <span data-ttu-id="2ff54-108">將收到輸入權杖，不能超過`dwMax`。</span><span class="sxs-lookup"><span data-stu-id="2ff54-108">Recieves type tokens, not to exceed `dwMax`.</span></span>  
  
 `pdwCount`  
 <span data-ttu-id="2ff54-109">接收的類型中實際數目`aTypeDefs`。</span><span class="sxs-lookup"><span data-stu-id="2ff54-109">Receives actual number of type in `aTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ff54-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="2ff54-110">Return Value</span></span>  
 <span data-ttu-id="2ff54-111">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="2ff54-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ff54-112">需求</span><span class="sxs-lookup"><span data-stu-id="2ff54-112">Requirements</span></span>  
 <span data-ttu-id="2ff54-113">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="2ff54-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ff54-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ff54-114">See Also</span></span>  
 [<span data-ttu-id="2ff54-115">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="2ff54-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="2ff54-116">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="2ff54-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="2ff54-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="2ff54-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
