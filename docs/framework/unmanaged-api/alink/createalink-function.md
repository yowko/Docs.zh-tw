---
title: CreateALink 函式
ms.date: 03/30/2017
api_name:
- CreateALink
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- CreateALink
helpviewer_keywords:
- CreateALink function
- Alink API, CreateALink function
ms.assetid: fc73bcb9-6af6-44d8-bc39-2f4400325dae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11117db08d58684cc854400424d1836ec35b8c12
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498001"
---
# <a name="createalink-function"></a><span data-ttu-id="62e70-102">CreateALink 函式</span><span class="sxs-lookup"><span data-stu-id="62e70-102">CreateALink Function</span></span>
<span data-ttu-id="62e70-103">建立組件連結器的執行個體，並將指標設定為指定的介面。</span><span class="sxs-lookup"><span data-stu-id="62e70-103">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62e70-104">語法</span><span class="sxs-lookup"><span data-stu-id="62e70-104">Syntax</span></span>  
  
```  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62e70-105">參數</span><span class="sxs-lookup"><span data-stu-id="62e70-105">Parameters</span></span>  
  
|<span data-ttu-id="62e70-106">參數</span><span class="sxs-lookup"><span data-stu-id="62e70-106">Parameter</span></span>|<span data-ttu-id="62e70-107">描述</span><span class="sxs-lookup"><span data-stu-id="62e70-107">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="62e70-108">其中一個組件連結器介面的實體名稱。</span><span class="sxs-lookup"><span data-stu-id="62e70-108">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="62e70-109">成功完成時包含位置的指標`riid`介面。</span><span class="sxs-lookup"><span data-stu-id="62e70-109">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="62e70-110">需求</span><span class="sxs-lookup"><span data-stu-id="62e70-110">Requirements</span></span>  
 <span data-ttu-id="62e70-111">**程式庫**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="62e70-111">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62e70-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62e70-112">See also</span></span>
- [<span data-ttu-id="62e70-113">Al.exe (組件連結器)</span><span class="sxs-lookup"><span data-stu-id="62e70-113">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
