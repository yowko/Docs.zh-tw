---
title: GetFileDef 方法
ms.date: 03/30/2017
api_name:
- IALink2.GetFileDef
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetFileDef
helpviewer_keywords:
- GetFileDef method
ms.assetid: 4e3fbe6c-b82a-4181-ab17-7faa1263f5b3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5db205993bc1a0665dc0003948ce805813251f48
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787459"
---
# <a name="getfiledef-method"></a><span data-ttu-id="b6b89-102">GetFileDef 方法</span><span class="sxs-lookup"><span data-stu-id="b6b89-102">GetFileDef Method</span></span>
<span data-ttu-id="b6b89-103">抓取中繼資料中使用的實際 FileDef token （而不是由 ALink 指派的 token）。</span><span class="sxs-lookup"><span data-stu-id="b6b89-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6b89-104">語法</span><span class="sxs-lookup"><span data-stu-id="b6b89-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6b89-105">參數</span><span class="sxs-lookup"><span data-stu-id="b6b89-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="b6b89-106">元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b6b89-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="b6b89-107">從 AddFile 方法或 AddImport 方法抓取之已加入檔案的 Token。</span><span class="sxs-lookup"><span data-stu-id="b6b89-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="b6b89-108">接收 FileDef token。</span><span class="sxs-lookup"><span data-stu-id="b6b89-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6b89-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="b6b89-109">Return Value</span></span>  
 <span data-ttu-id="b6b89-110">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="b6b89-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6b89-111">需求</span><span class="sxs-lookup"><span data-stu-id="b6b89-111">Requirements</span></span>  
 <span data-ttu-id="b6b89-112">需要 alink. h</span><span class="sxs-lookup"><span data-stu-id="b6b89-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6b89-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6b89-113">See also</span></span>

- [<span data-ttu-id="b6b89-114">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="b6b89-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="b6b89-115">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="b6b89-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="b6b89-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="b6b89-116">ALink API</span></span>](index.md)
