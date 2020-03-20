---
title: 連接.m_WriteList欄位
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
ms.openlocfilehash: 6c60831ddf23ce8ac9afcf244383d24732c3ef8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155833"
---
# <a name="connectionm_writelist-field"></a><span data-ttu-id="f7931-102">連接.m\_寫入清單欄位</span><span class="sxs-lookup"><span data-stu-id="f7931-102">Connection.m\_WriteList Field</span></span>

<span data-ttu-id="f7931-103">`Connection.m_WriteList`<xref:System.Collections.ArrayList>是排隊通過<xref:System.Net.HttpWebRequest>HTTP 發送的物件。</span><span class="sxs-lookup"><span data-stu-id="f7931-103">`Connection.m_WriteList` is an <xref:System.Collections.ArrayList> of <xref:System.Net.HttpWebRequest> objects that are queued up to be sent over HTTP.</span></span>

## <a name="syntax"></a><span data-ttu-id="f7931-104">語法</span><span class="sxs-lookup"><span data-stu-id="f7931-104">Syntax</span></span>
  
```csharp  
private ArrayList m_WriteList
```

> [!WARNING]
> <span data-ttu-id="f7931-105">該`Connection.m_WriteList`欄位是私有的，不應直接用於代碼。</span><span class="sxs-lookup"><span data-stu-id="f7931-105">The `Connection.m_WriteList` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="f7931-106">在任何情況下，Microsoft 都不支援在生產應用程式中使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="f7931-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="f7931-107">需求</span><span class="sxs-lookup"><span data-stu-id="f7931-107">Requirements</span></span>

<span data-ttu-id="f7931-108">**命名空間：**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="f7931-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="f7931-109">**裝配：** 系統（系統中）</span><span class="sxs-lookup"><span data-stu-id="f7931-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="f7931-110">**.NET 框架版本：** 自 2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="f7931-110">**.NET Framework versions:** Available since 2.0.</span></span>
