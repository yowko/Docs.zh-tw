---
title: 服務點.m_ConnectionGroupList欄位
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ServicePoint.m_ConnectionGroupList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: df8afb59-f0f6-4ddc-b3c1-839b9fc601d8
ms.openlocfilehash: 2b1b46085ed035b67fd01447727b406fe3895980
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155891"
---
# <a name="servicepointm_connectiongrouplist-field"></a><span data-ttu-id="23232-102">服務點.m\_連接組清單欄位</span><span class="sxs-lookup"><span data-stu-id="23232-102">ServicePoint.m\_ConnectionGroupList Field</span></span>

<span data-ttu-id="23232-103">`ServicePoint.m_ConnectionGroupList`是連接<xref:System.Collections.Hashtable>組，每個組都持有<xref:System.Net.ServicePoint>URI 的連接。</span><span class="sxs-lookup"><span data-stu-id="23232-103">`ServicePoint.m_ConnectionGroupList` is a <xref:System.Collections.Hashtable> of connection groups, each holding a connection for the <xref:System.Net.ServicePoint>'s URI.</span></span>

## <a name="syntax"></a><span data-ttu-id="23232-104">語法</span><span class="sxs-lookup"><span data-stu-id="23232-104">Syntax</span></span>
  
```csharp  
private Hashtable m_ConnectionGroupList
```

> [!WARNING]
> <span data-ttu-id="23232-105">該`ServicePoint.m_ConnectionGroupList`欄位是私有的，不應直接用於代碼。</span><span class="sxs-lookup"><span data-stu-id="23232-105">The `ServicePoint.m_ConnectionGroupList` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="23232-106">在任何情況下，Microsoft 都不支援在生產應用程式中使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="23232-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="23232-107">需求</span><span class="sxs-lookup"><span data-stu-id="23232-107">Requirements</span></span>

<span data-ttu-id="23232-108">**命名空間：**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="23232-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="23232-109">**裝配：** 系統（系統中）</span><span class="sxs-lookup"><span data-stu-id="23232-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="23232-110">**.NET 框架版本：** 自 2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="23232-110">**.NET Framework versions:** Available since 2.0.</span></span>
