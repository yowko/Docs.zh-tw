---
title: ConnectionGroup。 m_ConnectionList] 欄位
description: 瞭解 .NET 中的 m_ConnectionList ConnectionGroup 欄位，其中包含可為其他屬性提供相同 URI 和共用值的連線物件。
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
ms.openlocfilehash: 478b2441c062e8df6f4e718bd66d7af329f20f12
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989719"
---
# <a name="connectiongroupm_connectionlist-field"></a><span data-ttu-id="bde1e-103">ConnectionGroup. m \_ ConnectionList 欄位</span><span class="sxs-lookup"><span data-stu-id="bde1e-103">ConnectionGroup.m\_ConnectionList Field</span></span>

<span data-ttu-id="bde1e-104">`ConnectionGroup.m_ConnectionList`是 <xref:System.Collections.ArrayList> 連線物件的，它會提供相同的 URI，並針對某些其他屬性（例如到期和驗證）共用相同的值。</span><span class="sxs-lookup"><span data-stu-id="bde1e-104">`ConnectionGroup.m_ConnectionList` is an <xref:System.Collections.ArrayList> of connection objects that serves the same URI and share the same values for some other properties like expiration and authentication.</span></span>

## <a name="syntax"></a><span data-ttu-id="bde1e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="bde1e-105">Syntax</span></span>
  
```csharp  
private ArrayList m_ConnectionList
```

> [!WARNING]
> <span data-ttu-id="bde1e-106">`ConnectionGroup.m_ConnectionList`欄位是私用的，不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="bde1e-106">The `ConnectionGroup.m_ConnectionList` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="bde1e-107">在任何情況下，Microsoft 不支援在生產應用程式中使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="bde1e-107">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="bde1e-108">需求</span><span class="sxs-lookup"><span data-stu-id="bde1e-108">Requirements</span></span>

<span data-ttu-id="bde1e-109">**命名空間：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="bde1e-109">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="bde1e-110">**元件：** 系統（在 System.dll 中）</span><span class="sxs-lookup"><span data-stu-id="bde1e-110">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="bde1e-111">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="bde1e-111">**.NET Framework versions:** Available since 2.0.</span></span>
