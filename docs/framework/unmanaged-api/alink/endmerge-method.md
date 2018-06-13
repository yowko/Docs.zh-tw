---
title: EndMerge 方法
ms.date: 03/30/2017
api_name:
- IALink.EndMerge
- EndMerge
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EndMerge
helpviewer_keywords:
- EndMerge method
ms.assetid: 1d03bb15-a2c8-4a04-8fc6-b126c89c3778
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e8f9eecd6d6d74717eb7c1e389bfa24e40afc950
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402570"
---
# <a name="endmerge-method"></a><span data-ttu-id="ca95f-102">EndMerge 方法</span><span class="sxs-lookup"><span data-stu-id="ca95f-102">EndMerge Method</span></span>
<span data-ttu-id="ca95f-103">表示所有自訂屬性，已合併到發出範圍。</span><span class="sxs-lookup"><span data-stu-id="ca95f-103">Indicates that all custom attributes have been merged into the emit scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca95f-104">語法</span><span class="sxs-lookup"><span data-stu-id="ca95f-104">Syntax</span></span>  
  
```  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ca95f-105">參數</span><span class="sxs-lookup"><span data-stu-id="ca95f-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="ca95f-106">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="ca95f-106">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca95f-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="ca95f-107">Return Value</span></span>  
 <span data-ttu-id="ca95f-108">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="ca95f-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca95f-109">需求</span><span class="sxs-lookup"><span data-stu-id="ca95f-109">Requirements</span></span>  
 <span data-ttu-id="ca95f-110">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="ca95f-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca95f-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca95f-111">See Also</span></span>  
 [<span data-ttu-id="ca95f-112">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="ca95f-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="ca95f-113">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="ca95f-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="ca95f-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="ca95f-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
