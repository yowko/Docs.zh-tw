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
ms.openlocfilehash: a51e8c83d0949f68a41f6a4e10396adbc4f3c9c1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741886"
---
# <a name="getfiledef-method"></a><span data-ttu-id="957e4-102">GetFileDef 方法</span><span class="sxs-lookup"><span data-stu-id="957e4-102">GetFileDef Method</span></span>
<span data-ttu-id="957e4-103">擷取中繼資料 （而不是由 ALink 指派的權杖） 中所使用的實際 FileDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="957e4-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="957e4-104">語法</span><span class="sxs-lookup"><span data-stu-id="957e4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="957e4-105">參數</span><span class="sxs-lookup"><span data-stu-id="957e4-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="957e4-106">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="957e4-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="957e4-107">語彙基元的加入的檔案從 AddFile 方法或 AddImport 方法擷取。</span><span class="sxs-lookup"><span data-stu-id="957e4-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="957e4-108">接收 FileDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="957e4-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="957e4-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="957e4-109">Return Value</span></span>  
 <span data-ttu-id="957e4-110">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="957e4-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="957e4-111">需求</span><span class="sxs-lookup"><span data-stu-id="957e4-111">Requirements</span></span>  
 <span data-ttu-id="957e4-112">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="957e4-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="957e4-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="957e4-113">See also</span></span>

- [<span data-ttu-id="957e4-114">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="957e4-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="957e4-115">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="957e4-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="957e4-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="957e4-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
