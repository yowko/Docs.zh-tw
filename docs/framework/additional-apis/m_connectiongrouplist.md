---
title: ServicePoint。 m_ConnectionGroupList] 欄位
description: 瞭解 m_ConnectionGroupList ServicePoint 欄位，這是連接群組的雜湊表，其中每個都會在 .NET 中保存 ServicePoint URI 的連接。
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
ms.openlocfilehash: 0ebfeb782147f21abfde536b8053fa15b1e1a602
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989715"
---
# <a name="servicepointm_connectiongrouplist-field"></a><span data-ttu-id="17626-103">ServicePoint. m \_ ConnectionGroupList 欄位</span><span class="sxs-lookup"><span data-stu-id="17626-103">ServicePoint.m\_ConnectionGroupList Field</span></span>

<span data-ttu-id="17626-104">`ServicePoint.m_ConnectionGroupList`是 <xref:System.Collections.Hashtable> 連接群組的，每個都持有其 URI 的連接 <xref:System.Net.ServicePoint> 。</span><span class="sxs-lookup"><span data-stu-id="17626-104">`ServicePoint.m_ConnectionGroupList` is a <xref:System.Collections.Hashtable> of connection groups, each holding a connection for the <xref:System.Net.ServicePoint>'s URI.</span></span>

## <a name="syntax"></a><span data-ttu-id="17626-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="17626-105">Syntax</span></span>
  
```csharp  
private Hashtable m_ConnectionGroupList
```

> [!WARNING]
> <span data-ttu-id="17626-106">`ServicePoint.m_ConnectionGroupList`欄位是私用的，不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="17626-106">The `ServicePoint.m_ConnectionGroupList` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="17626-107">在任何情況下，Microsoft 不支援在生產應用程式中使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="17626-107">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="17626-108">需求</span><span class="sxs-lookup"><span data-stu-id="17626-108">Requirements</span></span>

<span data-ttu-id="17626-109">**命名空間：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="17626-109">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="17626-110">**元件：** 系統（在 System.dll 中）</span><span class="sxs-lookup"><span data-stu-id="17626-110">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="17626-111">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="17626-111">**.NET Framework versions:** Available since 2.0.</span></span>
