---
title: 連接組.m_ConnectionList欄位
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ConnectionGroup.m_ConnectionList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 186083cf-8dff-4600-a2ab-6fed4b4de6af
ms.openlocfilehash: 8eb6f215c36e214f7095eeba90bf0aed66dfcea0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155846"
---
# <a name="connectiongroupm_connectionlist-field"></a><span data-ttu-id="57377-102">連接組.m\_連接清單欄位</span><span class="sxs-lookup"><span data-stu-id="57377-102">ConnectionGroup.m\_ConnectionList Field</span></span>

<span data-ttu-id="57377-103">`ConnectionGroup.m_ConnectionList`是一<xref:System.Collections.ArrayList>個連線物件，用於相同的 URI，並為某些其他屬性（如過期和身份驗證）共用相同的值。</span><span class="sxs-lookup"><span data-stu-id="57377-103">`ConnectionGroup.m_ConnectionList` is an <xref:System.Collections.ArrayList> of connection objects that serves the same URI and share the same values for some other properties like expiration and authentication.</span></span>

## <a name="syntax"></a><span data-ttu-id="57377-104">語法</span><span class="sxs-lookup"><span data-stu-id="57377-104">Syntax</span></span>
  
```csharp  
private ArrayList m_ConnectionList
```

> [!WARNING]
> <span data-ttu-id="57377-105">該`ConnectionGroup.m_ConnectionList`欄位是私有的，不應直接用於代碼。</span><span class="sxs-lookup"><span data-stu-id="57377-105">The `ConnectionGroup.m_ConnectionList` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="57377-106">在任何情況下，Microsoft 都不支援在生產應用程式中使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="57377-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="57377-107">需求</span><span class="sxs-lookup"><span data-stu-id="57377-107">Requirements</span></span>

<span data-ttu-id="57377-108">**命名空間：**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="57377-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="57377-109">**裝配：** 系統（系統中）</span><span class="sxs-lookup"><span data-stu-id="57377-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="57377-110">**.NET 框架版本：** 自 2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="57377-110">**.NET Framework versions:** Available since 2.0.</span></span>
