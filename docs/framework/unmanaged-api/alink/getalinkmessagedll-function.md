---
title: GetALinkMessageDll 函式
ms.date: 03/30/2017
api_name:
- GetALinkMessageDll
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- GetALinkMessageDll
helpviewer_keywords:
- Alink API, GetALinkMessageDll function
- GetALinkMessageDll function
ms.assetid: 67985a22-88a2-4c54-8d99-4bcde9d6213e
topic_type:
- apiref
ms.openlocfilehash: 63719d0c6e13768e9dc7ed80e52e2a293e32a8a1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449351"
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="0a3e8-102">GetALinkMessageDll 函式</span><span class="sxs-lookup"><span data-stu-id="0a3e8-102">GetALinkMessageDll Function</span></span>
<span data-ttu-id="0a3e8-103">尋找並載入訊息 DLL。</span><span class="sxs-lookup"><span data-stu-id="0a3e8-103">Finds and loads the message DLL.</span></span> <span data-ttu-id="0a3e8-104">如果無法找到或載入訊息 DLL，則傳回0。</span><span class="sxs-lookup"><span data-stu-id="0a3e8-104">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="0a3e8-105">訊息 DLL 應位於名稱為語言識別項的子目錄中，或在目前的目錄中。</span><span class="sxs-lookup"><span data-stu-id="0a3e8-105">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a3e8-106">語法</span><span class="sxs-lookup"><span data-stu-id="0a3e8-106">Syntax</span></span>  
  
```cpp  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="0a3e8-107">需求</span><span class="sxs-lookup"><span data-stu-id="0a3e8-107">Requirements</span></span>  
 <span data-ttu-id="0a3e8-108">**標頭：** alink。h</span><span class="sxs-lookup"><span data-stu-id="0a3e8-108">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="0a3e8-109">連結**庫**： alink .dll</span><span class="sxs-lookup"><span data-stu-id="0a3e8-109">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a3e8-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a3e8-110">See also</span></span>

- [<span data-ttu-id="0a3e8-111">Al.exe (組件連結器)</span><span class="sxs-lookup"><span data-stu-id="0a3e8-111">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
