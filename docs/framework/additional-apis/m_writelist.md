---
title: 連接。 m_WriteList 欄位
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.Connection.m_WriteList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 235503c1-1d01-4f59-895f-ae2cf15b3345
ms.openlocfilehash: 22f939d13cceac4d1c0b39e9e8fe20cdc0ab9387
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214907"
---
# <a name="connectionm_writelist-field"></a><span data-ttu-id="3895c-102">連接. m\_WriteList 欄位</span><span class="sxs-lookup"><span data-stu-id="3895c-102">Connection.m\_WriteList Field</span></span>

<span data-ttu-id="3895c-103">`Connection.m_WriteList` 是已排入佇列以透過 HTTP 傳送之 <xref:System.Net.HttpWebRequest> 物件的 <xref:System.Collections.ArrayList>。</span><span class="sxs-lookup"><span data-stu-id="3895c-103">`Connection.m_WriteList` is an <xref:System.Collections.ArrayList> of <xref:System.Net.HttpWebRequest> objects that are queued up to be sent over HTTP.</span></span>

## <a name="syntax"></a><span data-ttu-id="3895c-104">語法</span><span class="sxs-lookup"><span data-stu-id="3895c-104">Syntax</span></span>
  
```csharp  
private ArrayList m_WriteList
```

> [!WARNING]
> <span data-ttu-id="3895c-105">[`Connection.m_WriteList`] 欄位是私用的，不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="3895c-105">The `Connection.m_WriteList` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="3895c-106">在任何情況下，Microsoft 不支援在生產應用程式中使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="3895c-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="3895c-107">需求</span><span class="sxs-lookup"><span data-stu-id="3895c-107">Requirements</span></span>

<span data-ttu-id="3895c-108">**命名空間：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="3895c-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="3895c-109">**元件：** 系統（在 System .dll 中）</span><span class="sxs-lookup"><span data-stu-id="3895c-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="3895c-110">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="3895c-110">**.NET Framework versions:** Available since 2.0.</span></span>
