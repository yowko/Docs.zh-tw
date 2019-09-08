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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 323e53c45a26d5703548ebe9863978f6d3929f0b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787472"
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="a2b83-102">GetALinkMessageDll 函式</span><span class="sxs-lookup"><span data-stu-id="a2b83-102">GetALinkMessageDll Function</span></span>
<span data-ttu-id="a2b83-103">尋找並載入訊息 DLL。</span><span class="sxs-lookup"><span data-stu-id="a2b83-103">Finds and loads the message DLL.</span></span> <span data-ttu-id="a2b83-104">如果無法找到或載入訊息 DLL，則傳回0。</span><span class="sxs-lookup"><span data-stu-id="a2b83-104">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="a2b83-105">訊息 DLL 應位於名稱為語言識別項的子目錄中，或在目前的目錄中。</span><span class="sxs-lookup"><span data-stu-id="a2b83-105">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2b83-106">語法</span><span class="sxs-lookup"><span data-stu-id="a2b83-106">Syntax</span></span>  
  
```cpp  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="a2b83-107">需求</span><span class="sxs-lookup"><span data-stu-id="a2b83-107">Requirements</span></span>  
 <span data-ttu-id="a2b83-108">**標頭：** alink。h</span><span class="sxs-lookup"><span data-stu-id="a2b83-108">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="a2b83-109">連結**庫**： alink .dll</span><span class="sxs-lookup"><span data-stu-id="a2b83-109">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2b83-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2b83-110">See also</span></span>

- [<span data-ttu-id="a2b83-111">Al.exe (組件連結器)</span><span class="sxs-lookup"><span data-stu-id="a2b83-111">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
